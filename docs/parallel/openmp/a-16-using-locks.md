---
title: A.16   Użycie blokad
ms.date: 11/04/2016
ms.assetid: 873bf32b-6cfe-4ce1-b994-bef80b50f399
ms.openlocfilehash: 6afb94660acdc79ea5a7eb61d3bf7e21fd70d751
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458987"
---
# <a name="a16---using-locks"></a>A.16   Użycie blokad

W poniższym przykładzie (dla [sekcji 3.2](../../parallel/openmp/3-2-lock-functions.md) na stronie 41) należy pamiętać, że argument do funkcji blokady musi mieć właściwość type `omp_lock_t`, i że nie ma potrzeby opróżnić go.  Funkcje blokady spowodować, że wątki ze stanu bezczynności podczas oczekiwania na wpis do pierwszej sekcję krytyczną, ale także wykonywanie innych zadań podczas oczekiwania na zapis do drugiego.  `omp_set_lock` Bloków funkcji, ale `omp_test_lock` funkcja nie jest, co umożliwia pracę w skip() do zrobienia.

## <a name="example"></a>Przykład

### <a name="code"></a>Kod

```
// omp_using_locks.c
// compile with: /openmp /c
#include <stdio.h>
#include <omp.h>

void work(int);
void skip(int);

int main() {
   omp_lock_t lck;
   int id;

   omp_init_lock(&lck);
   #pragma omp parallel shared(lck) private(id)
   {
      id = omp_get_thread_num();

      omp_set_lock(&lck);
      printf_s("My thread id is %d.\n", id);

      // only one thread at a time can execute this printf
      omp_unset_lock(&lck);

      while (! omp_test_lock(&lck)) {
         skip(id);   // we do not yet have the lock,
                     // so we must do something else
      }
      work(id);     // we now have the lock
                    // and can do the work
      omp_unset_lock(&lck);
   }
   omp_destroy_lock(&lck);
}
```