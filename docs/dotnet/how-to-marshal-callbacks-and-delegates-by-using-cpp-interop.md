---
title: 'Porady: kierowanie wywołań zwrotnych i delegatów za pomocą międzyoperacyjności języka C++'
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
ms.openlocfilehash: 592eae0ff59baddb79b810d46669b78ecc801155
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988189"
---
# <a name="how-to-marshal-callbacks-and-delegates-by-using-c-interop"></a>Porady: kierowanie wywołań zwrotnych i delegatów za pomocą międzyoperacyjności języka C++

W tym temacie przedstawiono kierowanie wywołań zwrotnych i delegatów (zarządzanej wersji wywołania zwrotnego) między zarządzanym i niezarządzanym kodem przy użyciu wizualizacji C++.

W poniższych przykładach kodu użyto [zarządzanych, niezarządzanych](../preprocessor/managed-unmanaged.md) #pragma dyrektyw, aby zaimplementować funkcje zarządzane i niezarządzane w tym samym pliku, ale funkcje te można również zdefiniować w oddzielnych plikach. Pliki zawierające tylko funkcje niezarządzane nie muszą być kompilowane z [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak skonfigurować niezarządzany interfejs API do wyzwalania zarządzanego delegata. Zarządzany delegat jest tworzony i jedna z metod międzyoperacyjnych, <xref:System.Runtime.InteropServices.Marshal.GetFunctionPointerForDelegate%2A>, służy do pobrania bazowego punktu wejścia dla delegata. Ten adres jest następnie przesyłany do niezarządzanej funkcji, która wywołuje ją bez znajomości faktu, że jest zaimplementowana jako funkcja zarządzana.

Należy zauważyć, że jest to możliwe, ale nie jest to konieczne, aby przypiąć delegata przy użyciu [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md) , aby zapobiec jego ponownej lokalizacji lub usunięciu przez moduł wyrzucania elementów bezużytecznych. Wymagana jest ochrona przed niedojrzałym odzyskiwaniem pamięci, ale Przypinanie zapewnia większą ochronę niż jest to konieczne, ponieważ uniemożliwia zbieranie danych, ale również zapobiega relokacji.

Jeśli delegat jest ponownie zlokalizowany przez wyrzucanie elementów bezużytecznych, nie wpłynie na podwyższenie poziomu zarządzanego wywołania zwrotnego, dlatego <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> jest używany do dodawania odwołania do delegata, co pozwala na relokację delegata, ale uniemożliwianie usuwania. Użycie GCHandle zamiast pin_ptr zmniejsza możliwości fragmentacji zarządzanej sterty.

```cpp
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

Poniższy przykład jest podobny do poprzedniego przykładu, ale w tym przypadku dostarczony wskaźnik funkcji jest przechowywany przez niezarządzany interfejs API, dzięki czemu można go wywołać w dowolnym momencie, wymagając, aby wyrzucanie elementów bezużytecznych było pomijane przez długi czas. W związku z tym Poniższy przykład używa wystąpienia globalnego <xref:System.Runtime.InteropServices.GCHandle>, aby zapobiec przeniesieniu delegata, niezależnie od zakresu funkcji. Zgodnie z opisem w pierwszym przykładzie używanie pin_ptr nie jest wymagane dla tych przykładów, ale w tym przypadku nie będzie działać, ponieważ zakres pin_ptr jest ograniczony do pojedynczej funkcji.

```cpp
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
