---
title: 'Instrukcje: Przeprowadzanie marshalingu tablic za pomocą — międzyoperacyjności języka C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- arrays [C++], marshaling
- marshaling [C++], arrays
- interop [C++], arrays
- C++ Interop, arrays
- data marshaling [C++], arrays
ms.assetid: c2b37ab1-8acf-4855-ad3c-7d2864826b14
ms.openlocfilehash: 91fd86a547a0241f0cfcca7cfc36c204429d80ac
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58776898"
---
# <a name="how-to-marshal-arrays-using-c-interop"></a>Instrukcje: Przeprowadzanie marshalingu tablic za pomocą — międzyoperacyjności języka C++

W tym temacie przedstawiono jeden zestaw reguł współdziałania Visual C++. Aby uzyskać więcej informacji, zobacz [za pomocą międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

Poniższy kod przykłady użycia [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md) #pragma — dyrektywy do zaimplementowania zarządzanych i niezarządzanych funkcji w tym samym pliku, ale te funkcje współpracować w taki sam sposób, jeśli zdefiniowany w oddzielnych plikach. Pliki zawierające tylko funkcji niezarządzanych nie muszą być skompilowana przy użyciu [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak przekazać tablicy zarządzanej do niezarządzanej funkcji. Używa funkcji zarządzanej [pin_ptr (C + +/ CLI)](../extensions/pin-ptr-cpp-cli.md) do pomijania wyrzucania elementów bezużytecznych dla tablicy przed wywołaniem funkcji niezarządzanej. Dostarczając niezarządzanej funkcji za pomocą przypiętego wskaźnika do sterty GC, należy unikać obciążenie skopiowanie elementu tablicy. Wykazanie, że niezarządzanej funkcji uzyskuje dostęp do pamięci sterty GC, modyfikuje zawartości tablicy, a zmiany zostaną uwzględnione podczas funkcji zarządzanej wznawia kontroli.

```
// PassArray1.cpp
// compile with: /clr
#ifndef _CRT_RAND_S
#define _CRT_RAND_S
#endif

#include <iostream>
#include <stdlib.h>
using namespace std;

using namespace System;

#pragma unmanaged

void TakesAnArray(int* a, int c) {
   cout << "(unmanaged) array received:\n";
   for (int i=0; i<c; i++)
      cout << "a[" << i << "] = " << a[i] << "\n";

   unsigned int number;
   errno_t err;

   cout << "(unmanaged) modifying array contents...\n";
   for (int i=0; i<c; i++) {
      err = rand_s( &number );
      if ( err == 0 )
         a[i] = number % 100;
   }
}

#pragma managed

int main() {
   array<int>^ nums = gcnew array<int>(5);

   nums[0] = 0;
   nums[1] = 1;
   nums[2] = 2;
   nums[3] = 3;
   nums[4] = 4;

   Console::WriteLine("(managed) array created:");
   for (int i=0; i<5; i++)
      Console::WriteLine("a[{0}] = {1}", i, nums[i]);

   pin_ptr<int> pp = &nums[0];
   TakesAnArray(pp, 5);

   Console::WriteLine("(managed) contents:");
   for (int i=0; i<5; i++)
      Console::WriteLine("a[{0}] = {1}", i, nums[i]);
}
```

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, przekazując tablicę niezarządzanych do funkcji zarządzanej. Funkcji zarządzanej uzyskuje dostęp do pamięci tablica bezpośrednio (w przeciwieństwie do tworzenia tablicy zarządzanej i kopiowanie zawartości tablicy), co umożliwia zmiany wprowadzone przez funkcję zarządzanych zostaną odzwierciedlone w funkcji niezarządzanej, gdy go przez formant.

```
// PassArray2.cpp
// compile with: /clr
#include <iostream>
using namespace std;

using namespace System;

#pragma managed

void ManagedTakesAnArray(int* a, int c) {
   Console::WriteLine("(managed) array received:");
   for (int i=0; i<c; i++)
      Console::WriteLine("a[{0}] = {1}", i, a[i]);

   cout << "(managed) modifying array contents...\n";
   Random^ r = gcnew Random(DateTime::Now.Second);
   for (int i=0; i<c; i++)
      a[i] = r->Next(100);
}

#pragma unmanaged

void NativeFunc() {
   int nums[5] = { 0, 1, 2, 3, 4 };

   printf_s("(unmanaged) array created:\n");
   for (int i=0; i<5; i++)
      printf_s("a[%d] = %d\n", i, nums[i]);

   ManagedTakesAnArray(nums, 5);

   printf_s("(ummanaged) contents:\n");
   for (int i=0; i<5; i++)
      printf_s("a[%d] = %d\n", i, nums[i]);
}

#pragma managed

int main() {
   NativeFunc();
}
```

## <a name="see-also"></a>Zobacz także

[Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
