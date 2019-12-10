---
title: 'Porady: przeprowadzanie marshalingu ciągów za pomocą funkcji PInvoke'
ms.custom: get-started-article
ms.date: 09/09/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- data marshaling [C++], strings
- platform invoke [C++], strings
ms.assetid: bcc75733-7337-4d9b-b1e9-b95a98256088
ms.openlocfilehash: e89177261aa32d34ea392030078d4088ea61e2a5
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988444"
---
# <a name="how-to-marshal-strings-using-pinvoke"></a>Porady: przeprowadzanie marshalingu ciągów za pomocą funkcji PInvoke

W tym temacie wyjaśniono, jak natywne funkcje, które akceptują ciągi w stylu C, można wywołać za pomocą typu ciągu CLR System:: String przy użyciu funkcji wywołania .NET Framework platformy. Programiści C++ wizualni są zachęcani do C++ używania funkcji międzyoperacyjnych (jeśli to możliwe), ponieważ funkcja P/Invoke zapewnia niewielkie raportowanie błędów w czasie kompilacji, nie jest bezpieczna pod względem typu i może być żmudnym do wdrożenia. Jeśli niezarządzany interfejs API jest spakowany jako biblioteka DLL, a kod źródłowy jest niedostępny, to polecenie P/Invoke jest jedyną opcją, ale w przeciwnym razie zobacz [using C++ Interop (niejawny element PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

Parametry zarządzane i niezarządzane są inaczej ułożone w pamięci, więc przekazywanie ciągów z zarządzanych do funkcji niezarządzanych wymaga atrybutu <xref:System.Runtime.InteropServices.MarshalAsAttribute>, aby kompilator mógł wstawić wymagane mechanizmy konwersji do prawidłowego i bezpiecznego organizowania danych ciągu.

Podobnie jak w przypadku funkcji używających tylko typów danych wewnętrznych, <xref:System.Runtime.InteropServices.DllImportAttribute> jest używany do deklarowania zarządzanych punktów wejścia do funkcji natywnych, ale — do przekazywania ciągów — zamiast definiowania tych punktów wejścia jako ciągów w stylu C, zamiast tego można użyć dojścia do typu <xref:System.String>. Zostanie wyświetlony komunikat z instrukcjami kompilatora, aby wstawić kod, który wykonuje wymaganą konwersję. Dla każdego argumentu funkcji w niezarządzanej funkcji, która przyjmuje ciąg, atrybut <xref:System.Runtime.InteropServices.MarshalAsAttribute> powinien być używany do wskazania, że obiekt String powinien być zorganizowany do funkcji natywnej jako ciąg w stylu C.

Organizator zawija wywołanie funkcji niezarządzanej w ukrytej procedurze otoki, która przypina i kopiuje ciąg zarządzany do lokalnie przydzielonego ciągu w niezarządzanym kontekście, który następnie jest przekazywany do niezarządzanej funkcji. Gdy funkcja niezarządzana zwróci, otoka usuwa zasób lub, jeśli znajduje się on na stosie, jest odzyskiwana, gdy otoka wykracza poza zakres. Niezarządzana funkcja nie odpowiada za tę pamięć. Kod niezarządzany tworzy i usuwa pamięć w stosie skonfigurowanym przez własną CRT, więc nigdy nie występuje problem dotyczący organizatora przy użyciu innej wersji CRT.

Jeśli niezarządzana funkcja zwraca ciąg, jako wartość zwracaną lub parametr out, organizator kopiuje go do nowego łańcucha zarządzanego, a następnie zwalnia pamięć. Aby uzyskać więcej informacji, zobacz [domyślne zachowanie organizowania](/dotnet/framework/interop/default-marshaling-behavior) i [kierowanie danych za pomocą wywołania platformy](/dotnet/framework/interop/marshaling-data-with-platform-invoke).

## <a name="example"></a>Przykład

Poniższy kod składa się z niezarządzanego i zarządzanego modułu. Moduł niezarządzany jest biblioteką DLL, która definiuje funkcję o nazwie TakesAString, która akceptuje ciąg ANSI w stylu C w postaci znaku *. Moduł zarządzany jest aplikacją wiersza polecenia, która importuje funkcję TakesAString, ale definiuje ją jako przyjmującą zarządzany system. String zamiast znaku\*. Atrybut <xref:System.Runtime.InteropServices.MarshalAsAttribute> jest używany do wskazania, w jaki sposób zarządzany ciąg powinien być zorganizowany po wywołaniu TakesAString.

```cpp
// TraditionalDll2.cpp
// compile with: /LD /EHsc
#include <windows.h>
#include <stdio.h>
#include <iostream>

using namespace std;

#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

extern "C" {
   TRADITIONALDLL_API void TakesAString(char*);
}

void TakesAString(char* p) {
   printf_s("[unmanaged] %s\n", p);
}
```

```cpp
// MarshalString.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value struct TraditionalDLL
{
   [DllImport("TraditionalDLL2.dll")]
      static public void
      TakesAString([MarshalAs(UnmanagedType::LPStr)]String^);
};

int main() {
   String^ s = gcnew String("sample string");
    Console::WriteLine("[managed] passing managed string to unmanaged function...");
   TraditionalDLL::TakesAString(s);
   Console::WriteLine("[managed] {0}", s);
}
```

Ta technika powoduje, że kopia ciągu ma być skonstruowana na stercie niezarządzanym, więc zmiany wprowadzone do ciągu przez funkcję natywną nie zostaną odzwierciedlone w zarządzanej kopii ciągu.

Należy zauważyć, że żadna część biblioteki DLL nie jest ujawniona w kodzie zarządzanym za pośrednictwem tradycyjnego #include dyrektywy. W rzeczywistości plik DLL jest dostępny tylko w czasie wykonywania, dlatego problemy z funkcjami zaimportowanymi z `DllImport` nie będą wykrywane w czasie kompilacji.

## <a name="see-also"></a>Zobacz także

[Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
