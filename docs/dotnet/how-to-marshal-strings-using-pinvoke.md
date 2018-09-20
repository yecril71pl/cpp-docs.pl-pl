---
title: 'Porady: przeprowadzanie Marshalingu ciągów za pomocą funkcji PInvoke | Dokumentacja firmy Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- data marshaling [C++], strings
- platform invoke [C++], strings
ms.assetid: bcc75733-7337-4d9b-b1e9-b95a98256088
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d917228b1972715c291d84625cc684fc9de5b998
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396379"
---
# <a name="how-to-marshal-strings-using-pinvoke"></a>Porady: przeprowadzanie marshalingu ciągów za pomocą funkcji PInvoke

W tym temacie wyjaśniono, jak natywne funkcje, których można wywołać ciągi stylu C przy użyciu ciągu CLR typu System::String dzięki obsłudze wywołania do platformy .NET Framework. W programowaniu w języku Visual C++ są zachęcani do zamiast tego użyj funkcji międzyoperacyjności języka C++ (jeśli jest to możliwe), ponieważ metody P/Invoke zapewnia nieco błąd kompilacji, raportowanie, nie jest bezpieczny i może być uciążliwe do zaimplementowania. Niezarządzany interfejs API jest spakowany jako biblioteki DLL i kod źródłowy jest niedostępny, następnie P/Invoke jest jedyną opcją, ale w przeciwnym razie zobacz [za pomocą międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

Ciągi zarządzane i niezarządzane są wyświetlane inaczej w pamięci, dlatego przekazywanie ciągi z kodu zarządzanego do funkcji niezarządzanych wymaga <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu, aby poinstruować kompilator, aby wstawić mechanizmy konwersji wymagane do kierowania danych ciągu poprawnie i bezpiecznie.

Podobnie jak w przypadku funkcji używających tylko typów danych wewnętrznych <xref:System.Runtime.InteropServices.DllImportAttribute> służy do deklarowania punkty wejścia zarządzanych w funkcjach natywnych, ale — w przypadku przekazywania ciągów — zamiast Definiowanie te punkty wejścia jako ciągi stylu C, dojścia do przełączania <xref:System.String> typu można zamiast tego. Kompilator, aby wstawić kod, który wykonuje wymagane konwersja powoduje wyświetlenie monitu. Dla każdego argumentu funkcji w funkcji niezarządzanej, która przyjmuje parametry <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybut powinien być używany do wskazania, że obiekt ciągu powinny być wprowadzane do natywnej funkcji jako ciąg stylu C.

## <a name="example"></a>Przykład

Poniższy kod składa się z modułu zarządzanego i niezarządzanego. Moduł niezarządzane to biblioteki DLL, która definiuje funkcję o nazwie TakesAString, który akceptuje ciąg stylu C ANSI w formie char *. Moduł zarządzany jest aplikacją wiersza polecenia, który importuje funkcja TakesAString, ale definiuje ją jako biorąc zarządzanych System.String zamiast znaku\*. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybut jest używany do wskazania, jak powinny być wprowadzane zarządzanych ciągu wywołanego TakesAString.

```
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

```
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

Ta technika sprawia, że kopia ciągu skonstruowany na stosie niezarządzanym, dzięki czemu zmiany wprowadzone do ciągu za pomocą natywnej funkcji nie zostaną odzwierciedlone w zarządzanych kopia ciągu.

Należy pamiętać, że części biblioteki DLL jest narażony na kodu zarządzanego za pośrednictwem tradycyjnych # dyrektywy include. W rzeczywistości biblioteki DLL odbywa się w czasie wykonywania, dzięki czemu problemy z funkcjami zaimportowane wraz z `DllImport` nie zostanie wykryty w czasie kompilacji.

## <a name="see-also"></a>Zobacz też

[Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)