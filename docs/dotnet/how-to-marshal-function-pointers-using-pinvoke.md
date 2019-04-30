---
title: 'Instrukcje: Przeprowadzanie marshalingu wskaźników funkcji przy użyciu PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- interop [C++], callbacks and delegates
- platform invoke [C++], callbacks and delegates
- marshaling [C++], callbacks and delegates
ms.assetid: dcf396fd-a91d-49c0-ab0b-1ea160668a89
ms.openlocfilehash: 031bda0f93d6a95aa3c774553aefca0647d0518c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400568"
---
# <a name="how-to-marshal-function-pointers-using-pinvoke"></a>Instrukcje: Przeprowadzanie marshalingu wskaźników funkcji przy użyciu PInvoke

W tym temacie wyjaśniono, jak zarządzane delegatów mogą być używane zamiast wskaźników funkcji, podczas współpracy z niezarządzanych funkcji przy użyciu funkcji .NET Framework P/Invoke. Jednak w programowaniu w języku Visual C++ zachęcamy do zamiast tego użyj funkcji międzyoperacyjności języka C++ (jeśli jest to możliwe) ponieważ P/Invoke zapewnia nieco błąd kompilacji, raportowanie, nie jest bezpieczny i może być uciążliwe do zaimplementowania. Jeśli niezarządzanego interfejsu API jest spakowany jako biblioteki DLL i kod źródłowy jest niedostępny, P/Invoke jest jedyną opcją. W przeciwnym razie zobacz następujące tematy:

- [Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

- [Instrukcje: przeprowadzanie marshalingu wywołań zwrotnych i delegatów za pomocą międzyoperacyjności języka C++](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)

Niezarządzane interfejsy API, które umożliwiają wykorzystywanie wskaźników funkcji, ponieważ argumenty mogą być wywoływane z kodu zarządzanego z zarządzanego delegatem zamiast wskaźnik natywnej funkcji. Kompilator automatycznie kieruje delegata z funkcjami niezarządzanymi jako wskaźnik funkcji i wstawia kod konieczne przejście zarządzanych/niezarządzanych.

## <a name="example"></a>Przykład

Poniższy kod składa się z modułu zarządzanego i niezarządzanego. Moduł niezarządzane to biblioteki DLL, która definiuje funkcję o nazwie TakesCallback, który akceptuje wskaźnik funkcji. Ten adres jest używany do wykonywania funkcji.

Moduł zarządzany definiowany delegat jest przekazywane do kodu macierzystego jako wskaźnik funkcji, która używa <xref:System.Runtime.InteropServices.DllImportAttribute> atrybutu do udostępnienia funkcji TakesCallback natywnej związane z kodem zarządzanym. Wystąpienie delegata funkcji main jest utworzony i przekazany do funkcji TakesCallback. Dane wyjściowe programu pokazuje, że ta funkcja pobiera wykonywane przez funkcji macierzystej TakesCallback.

Funkcji zarządzanej pomija wyrzucania elementów bezużytecznych dla zarządzanych delegata zapobiec .NET Framework wyrzucania elementów bezużytecznych z przemieszczanie delegata, gdy wykonuje funkcji macierzystej.

```cpp
// TraditionalDll5.cpp
// compile with: /LD /EHsc
#include <iostream>
#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

extern "C" {
   /* Declare an unmanaged function type that takes two int arguments
      Note the use of __stdcall for compatibility with managed code */
   typedef int (__stdcall *CALLBACK)(int);
   TRADITIONALDLL_API int TakesCallback(CALLBACK fp, int);
}

int TakesCallback(CALLBACK fp, int n) {
   printf_s("[unmanaged] got callback address, calling it...\n");
   return fp(n);
}
```

```cpp
// MarshalDelegate.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

public delegate int GetTheAnswerDelegate(int);
public value struct TraditionalDLL {
   [DllImport("TraditionalDLL5.dll")]
   static public int TakesCallback(GetTheAnswerDelegate^ pfn, int n);
};

int GetNumber(int n) {
   Console::WriteLine("[managed] callback!");
   static int x = 0;
   ++x;
   return x + n;
}

int main() {
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);
   pin_ptr<GetTheAnswerDelegate^> pp = &fp;
   Console::WriteLine("[managed] sending delegate as callback...");

   int answer = TraditionalDLL::TakesCallback(fp, 42);
}
```

Należy pamiętać, że części biblioteki DLL jest uwidaczniany związane z kodem zarządzanym przy użyciu tradycyjnych # dyrektywy include. W rzeczywistości biblioteki DLL jest dostępny tylko w czasie wykonywania, więc problemy z funkcjami zaimportowane wraz z <xref:System.Runtime.InteropServices.DllImportAttribute> nie zostanie wykryty w czasie kompilacji.

## <a name="see-also"></a>Zobacz także

[Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
