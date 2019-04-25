---
title: 'Instrukcje: Przeprowadzanie marshalingu tablic przy użyciu PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling [C++], arrays
- platform invoke [C++], arrays
- interop [C++], arrays
- data marshaling [C++], arrays
ms.assetid: a1237797-a2da-4df4-984a-6333ed3af406
ms.openlocfilehash: 60b49135928e3dadffc2a3c7a422646d2f3a768d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325445"
---
# <a name="how-to-marshal-arrays-using-pinvoke"></a>Instrukcje: Przeprowadzanie marshalingu tablic przy użyciu PInvoke

W tym temacie wyjaśniono, jak natywne funkcje, których można wywołać ciągi stylu C przy użyciu typu ciąg CLR <xref:System.String> dzięki obsłudze wywołania do platformy .NET Framework. W programowaniu w języku Visual C++ są zachęcani do zamiast tego użyj funkcji międzyoperacyjności języka C++ (jeśli jest to możliwe), ponieważ metody P/Invoke zapewnia nieco błąd kompilacji, raportowanie, nie jest bezpieczny i może być uciążliwe do zaimplementowania. Jeśli niezarządzanego interfejsu API jest spakowany jako biblioteki DLL i kod źródłowy jest niedostępny, P/Invoke jest jedyną opcją (w przeciwnym razie zobacz [za pomocą międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)).

## <a name="example"></a>Przykład

Natywnych i zarządzanych tablic są wyświetlane inaczej w pamięci, przekazując je pomyślnie granicę zarządzanych/niezarządzanych wymaga konwersji ani kierowania. W tym temacie pokazano, jak tablica elementów proste (blitable) mogą być przekazywane do funkcji natywnych z kodu zarządzanego.

Podobnie jak zarządzanych/niezarządzanych danych marshalingu ogólnie rzecz biorąc, <xref:System.Runtime.InteropServices.DllImportAttribute> atrybut jest używany do tworzenia zarządzany punkt wejścia dla każdej funkcji natywnej, który będzie używany. W przypadku funkcji, które przyjmują tablic jako argumenty <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybut musi także służyć do określania kompilatora, jak można zorganizować dane. W poniższym przykładzie <xref:System.Runtime.InteropServices.UnmanagedType> wyliczenia jest używany do wskazania, że tablicy zarządzanej będzie organizowane w postaci tablicy stylu C.

Poniższy kod składa się z modułu zarządzanego i niezarządzanego. Moduł niezarządzane to biblioteki DLL, która definiuje funkcję, która akceptuje tablicy liczb całkowitych. Drugi moduł jest aplikacją wiersza polecenia zarządzanych, importuje tej funkcji, ale definiuje ją pod kątem tablica zarządzana, która używa <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu, aby określić, czy tablica powinny być konwertowane na tablicy natywnej, gdy zostanie wywołana.

Moduł zarządzany jest kompilowany za pomocą/CLR.

```cpp
// TraditionalDll4.cpp
// compile with: /LD /EHsc
#include <iostream>

#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

extern "C" {
   TRADITIONALDLL_API void TakesAnArray(int len, int[]);
}

void TakesAnArray(int len, int a[]) {
   printf_s("[unmanaged]\n");
   for (int i=0; i<len; i++)
      printf("%d = %d\n", i, a[i]);
}
```

```cpp
// MarshalBlitArray.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value struct TraditionalDLL {
   [DllImport("TraditionalDLL4.dll")]
   static public void TakesAnArray(
   int len,[MarshalAs(UnmanagedType::LPArray)]array<int>^);
};

int main() {
   array<int>^ b = gcnew array<int>(3);
   b[0] = 11;
   b[1] = 33;
   b[2] = 55;
   TraditionalDLL::TakesAnArray(3, b);

   Console::WriteLine("[managed]");
   for (int i=0; i<3; i++)
      Console::WriteLine("{0} = {1}", i, b[i]);
}
```

Należy pamiętać, że części biblioteki DLL jest narażony na kodu zarządzanego za pośrednictwem tradycyjnych # dyrektywy include. W rzeczywistości, ponieważ biblioteka DLL jest dostępny tylko w czasie wykonywania, problemy z funkcjami są importowane z <xref:System.Runtime.InteropServices.DllImportAttribute> nie zostanie wykryty w czasie kompilacji.

## <a name="see-also"></a>Zobacz także

[Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
