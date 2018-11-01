---
title: Błąd kompilatora C3899
ms.date: 11/04/2016
f1_keywords:
- C3899
helpviewer_keywords:
- C3899
ms.assetid: 14e07e4a-f7a7-4309-baaa-649d69e12e23
ms.openlocfilehash: 26860ba0e8fd92f491ee389147605ba82cecf25c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598396"
---
# <a name="compiler-error-c3899"></a>Błąd kompilatora C3899

"var": wykorzystanie wartości l składowej danych initonly nie jest dozwolona bezpośrednio w ramach równoległego regionu w klasie "class"

[Initonly (C + +/ interfejsu wiersza polecenia)](../../dotnet/initonly-cpp-cli.md) nie można zainicjować składowej danych wewnątrz konstruktora, który znajduje się w tej części [równoległe](../../parallel/openmp/reference/parallel.md) regionu.  Jest to spowodowane kompilator wykonuje wewnętrznego relokacji ten kod taki sposób, że nie jest już skutecznie część konstruktora.

Aby rozwiązać problem, należy zainicjować składowej danych initonly w konstruktorze, ale poza programem równoległego regionu.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3899.

```
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