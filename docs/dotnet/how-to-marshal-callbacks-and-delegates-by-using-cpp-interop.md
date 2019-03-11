---
title: 'Instrukcje: Kierowanie wywołań zwrotnych i delegatów za pomocą międzyoperacyjności języka C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- C++ Interop, callbacks and delegates
- interop [C++], callbacks and delegates
- delegates [C++], marshaling
- marshaling [C++], callbacks and delegates
- callbacks [C++], marshaling
ms.assetid: 2313e9eb-5df9-4367-be0f-14b4712d8d2d
ms.openlocfilehash: d3814ffbcd23168a9727b1b1d73e2c825639a9c5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739219"
---
# <a name="how-to-marshal-callbacks-and-delegates-by-using-c-interop"></a>Instrukcje: Kierowanie wywołań zwrotnych i delegatów za pomocą międzyoperacyjności języka C++

W tym temacie przedstawiono kierowania wywołań zwrotnych i delegatów (zarządzanej wersji wywołanie zwrotne) między kodem zarządzanym i niezarządzanym przy użyciu języka Visual C++.

Poniższy kod przykłady użycia [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md) #pragma — dyrektywy do zaimplementowania zarządzanych i niezarządzanych funkcji w tym samym pliku, ale można również zdefiniować funkcje w oddzielnych plikach. Pliki zawierające tylko funkcji niezarządzanych nie muszą być skompilowana przy użyciu [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak skonfigurować niezarządzanego interfejsu API do wyzwolenia zarządzanych delegata. Zarządzane delegata jest tworzony i jednej z metod międzyoperacyjny <xref:System.Runtime.InteropServices.Marshal.GetFunctionPointerForDelegate%2A>, służy do pobierania podstawowego punktu wejścia dla delegata. Ten adres jest następnie przekazywany do niezarządzanej funkcji, który ją wywołuje nie znajomości fakt, że jest implementowana jako funkcji zarządzanej.

Zwróć uwagę, że jest to możliwe, ale nie jest to konieczne, aby przypiąć delegata za pomocą [pin_ptr (C + +/ CLI)](../windows/pin-ptr-cpp-cli.md) aby zapobiec jej się ponownie lub usuwane przez moduł odśmiecania pamięci. Konieczna jest ochrona z przedwczesne wyrzucania elementów bezużytecznych, ale przypinanie chroni więcej niż jest to konieczne, ponieważ zapobiega kolekcji, ale także zapobiega relokacji.

Jeśli delegat znajduje się ponownie, wyrzucanie elementów bezużytecznych, nie wpłynie to wywołanie zwrotne underlaying zarządzane, dlatego <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> służy do dodawania odwołania do delegata, umożliwiając przenoszenia obiektu delegowanego, ale uniemożliwia usuwania. Za pomocą GCHandle — zamiast pin_ptr zmniejsza ryzyko fragmentację sterty zarządzanej.

```
// MarshalDelegate1.cpp
// compile with: /clr
#include <iostream>

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

// Declare an unmanaged function type that takes two int arguments
// Note the use of __stdcall for compatibility with managed code
typedef int (__stdcall *ANSWERCB)(int, int);

int TakesCallback(ANSWERCB fp, int n, int m) {
   printf_s("[unmanaged] got callback address, calling it...\n");
   return fp(n, m);
}

#pragma managed

public delegate int GetTheAnswerDelegate(int, int);

int GetNumber(int n, int m) {
   Console::WriteLine("[managed] callback!");
   return n + m;
}

int main() {
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);
   GCHandle gch = GCHandle::Alloc(fp);
   IntPtr ip = Marshal::GetFunctionPointerForDelegate(fp);
   ANSWERCB cb = static_cast<ANSWERCB>(ip.ToPointer());
   Console::WriteLine("[managed] sending delegate as callback...");

// force garbage collection cycle to prove
// that the delegate doesn't get disposed
   GC::Collect();

   int answer = TakesCallback(cb, 243, 257);

// release reference to delegate
   gch.Free();
}
```

## <a name="example"></a>Przykład

Poniższy przykład jest podobny do poprzedniego przykładu, ale w tym przypadku wskaźnika określona funkcja jest przechowywany przez niezarządzanego interfejsu API, dzięki czemu może być wywoływany w dowolnym momencie wymagające pomijane wyrzucania elementów bezużytecznych dla dowolnego określonego czasu. W rezultacie, w poniższym przykładzie użyto globalnego wystąpienia <xref:System.Runtime.InteropServices.GCHandle> uniemożliwi delegata przenoszone, niezależne od zakresu funkcji. Zgodnie z opisem w pierwszym przykładzie, za pomocą pin_ptr nie jest konieczne w poniższych przykładach, ale w takim przypadku nie działa mimo to, jak zakres pin_ptr jest ograniczona do jednej funkcji.

```
// MarshalDelegate2.cpp
// compile with: /clr
#include <iostream>

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

// Declare an unmanaged function type that takes two int arguments
// Note the use of __stdcall for compatibility with managed code
typedef int (__stdcall *ANSWERCB)(int, int);
static ANSWERCB cb;

int TakesCallback(ANSWERCB fp, int n, int m) {
   cb = fp;
   if (cb) {
      printf_s("[unmanaged] got callback address (%d), calling it...\n", cb);
      return cb(n, m);
   }
   printf_s("[unmanaged] unregistering callback");
   return 0;
}

#pragma managed

public delegate int GetTheAnswerDelegate(int, int);

int GetNumber(int n, int m) {
   Console::WriteLine("[managed] callback!");
   static int x = 0;
   ++x;

   return n + m + x;
}

static GCHandle gch;

int main() {
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);

   gch = GCHandle::Alloc(fp);

   IntPtr ip = Marshal::GetFunctionPointerForDelegate(fp);
   ANSWERCB cb = static_cast<ANSWERCB>(ip.ToPointer());
   Console::WriteLine("[managed] sending delegate as callback...");

   int answer = TakesCallback(cb, 243, 257);

   // possibly much later (in another function)...

   Console::WriteLine("[managed] releasing callback mechanisms...");
   TakesCallback(0, 243, 257);
   gch.Free();
}
```

## <a name="see-also"></a>Zobacz także

[Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
