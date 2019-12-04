---
title: Błąd kompilatora C3899
ms.date: 11/04/2016
f1_keywords:
- C3899
helpviewer_keywords:
- C3899
ms.assetid: 14e07e4a-f7a7-4309-baaa-649d69e12e23
ms.openlocfilehash: 022bc1a37f7d9cfdb2c206592dd303a9c3c95080
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749116"
---
# <a name="compiler-error-c3899"></a>Błąd kompilatora C3899

"var": wykorzystanie wartości l składowej danych initonly nie jest dozwolone bezpośrednio w ramach równoległego regionu w klasie "Class"

Nie można zainicjować składowej danych [initonly (C++/CLI)](../../dotnet/initonly-cpp-cli.md) w obrębie tej części konstruktora, która znajduje się w regionie [równoległym](../../parallel/openmp/reference/parallel.md) .  Dzieje się tak, ponieważ kompilator wykonuje wewnętrzną relokację tego kodu, tak że nie jest już częścią konstruktora.

Aby rozwiązać ten problem, zainicjuj element członkowski danych initonly w konstruktorze, ale poza regionem równoległym.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3899.

```cpp
// C3899.cpp
// compile with: /clr /openmp
#include <omp.h>

public ref struct R {
   initonly int x;
   R() {
      x = omp_get_thread_num() + 1000;   // OK
      #pragma omp parallel num_threads(5)
      {
         // cannot assign to 'x' here
         x = omp_get_thread_num() + 1000;   // C3899
         System::Console::WriteLine("thread {0}", omp_get_thread_num());
      }
      x = omp_get_thread_num() + 1000;   // OK
   }
};

int main() {
   R^ r = gcnew R;
   System::Console::WriteLine(r->x);
}
```
