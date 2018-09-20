---
title: 'Porady: przeprowadzanie Marshalingu wskaźników osadzonych za pomocą międzyoperacyjności języka C++ | Dokumentacja firmy Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- structures [C++], marshaling embedded pointers
- interop [C++], embedded pointers
- C++ Interop, embedded pointers
- marshaling [C++], embedded pointers
- pointers [C++], marshaling
- data marshaling [C++], embedded pointers
ms.assetid: 05fb8858-97f2-47aa-86b2-2c0ad713bdb2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e64697edad62b440ce739b4bca7856f84f608135
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417218"
---
# <a name="how-to-marshal-embedded-pointers-using-c-interop"></a>Porady: przeprowadzanie marshalingu wskaźników osadzonych za pomocą międzyoperacyjności języka C++

Poniższy kod przykłady użycia [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md) #pragma — dyrektywy do zaimplementowania zarządzanych i niezarządzanych funkcji w tym samym pliku, ale te funkcje współpracować w taki sam sposób, jeśli zdefiniowany w oddzielnych plikach. Pliki zawierające tylko funkcji niezarządzanych nie muszą być skompilowana przy użyciu [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak niezarządzanej funkcji, która przyjmuje struktury zawierającej wskaźniki, można wywołać z funkcji zarządzanej. Funkcji zarządzanej tworzenia wystąpienia struktury i inicjuje osadzone wskaźnika za pomocą słowa kluczowego new (zamiast [ref new, gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md) — słowo kluczowe). Ponieważ to przydziela pamięć na natywnej stercie, nie ma potrzeby przypinanie tablicy, aby pominąć wyrzucania elementów bezużytecznych. Jednak pamięć muszą zostać jawnie usunięte w celu uniknięcia wycieku pamięci.

```
// marshal_embedded_pointer.cpp
// compile with: /clr
#include <iostream>

using namespace System;
using namespace System::Runtime::InteropServices;

// unmanaged struct
struct ListStruct {
   int count;
   double* item;
};

#pragma unmanaged

void UnmanagedTakesListStruct(ListStruct list) {
   printf_s("[unmanaged] count = %d\n", list.count);
   for (int i=0; i<list.count; i++)
      printf_s("array[%d] = %f\n", i, list.item[i]);
}

#pragma managed

int main() {
   ListStruct list;
   list.count = 10;
   list.item = new double[list.count];

   Console::WriteLine("[managed] count = {0}", list.count);
   Random^ r = gcnew Random(0);
   for (int i=0; i<list.count; i++) {
      list.item[i] = r->NextDouble() * 100.0;
      Console::WriteLine("array[{0}] = {1}", i, list.item[i]);
   }

   UnmanagedTakesListStruct( list );
   delete list.item;
}
```

```Output
[managed] count = 10
array[0] = 72.624326996796
array[1] = 81.7325359590969
array[2] = 76.8022689394663
array[3] = 55.8161191436537
array[4] = 20.6033154021033
array[5] = 55.8884794618415
array[6] = 90.6027066011926
array[7] = 44.2177873310716
array[8] = 97.754975314138
array[9] = 27.370445768987
[unmanaged] count = 10
array[0] = 72.624327
array[1] = 81.732536
array[2] = 76.802269
array[3] = 55.816119
array[4] = 20.603315
array[5] = 55.888479
array[6] = 90.602707
array[7] = 44.217787
array[8] = 97.754975
array[9] = 27.370446
```

## <a name="see-also"></a>Zobacz też

[Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)