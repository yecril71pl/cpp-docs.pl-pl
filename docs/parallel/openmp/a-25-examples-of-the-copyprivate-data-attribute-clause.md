---
title: A.25   Przykłady klauzuli atrybutu danych prywatnej kopii
ms.date: 11/04/2016
ms.assetid: 7b1cb6a5-5691-4b95-b3ac-d7543ede6405
ms.openlocfilehash: 6c3c174780023f17cc2aa47a54bff14fccf99306
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493892"
---
# <a name="a25---examples-of-the-copyprivate-data-attribute-clause"></a>A.25   Przykłady klauzuli atrybutu danych prywatnej kopii

**Przykład 1:** `copyprivate` — klauzula ([sekcji 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) na stronie 32) może służyć do emisji wartości uzyskanych przez pojedynczy wątek bezpośrednio do wszystkich wystąpień w zmiennych prywatnych w innych wątków.

```
float x, y;
#pragma omp threadprivate(x, y)

void init( )
{
    float a;
    float b;

    #pragma omp single copyprivate(a,b,x,y)
    {
        get_values(a,b,x,y);
    }

    use_values(a, b, x, y);
}
```

W przypadku rutynowych *init* nazywa się z obszarem serial jego zachowanie nie występuje w obecności dyrektywy. Po wywołaniu *get_values* procedury zostało wykonane przez jeden wątek, żadnego wątku pozostawia konstrukcja do prywatnego obiekty wskazywany przez *a*, *b*, *x*, i *y* w wszystkie wątki zdefiniowano stają się przy użyciu wartości do odczytu.

**Przykład 2:** w przeciwieństwie do poprzedniego przykładu załóżmy, że odczytu muszą być wykonywane przez określonego wątku, załóżmy, że głównego wątku. W tym przypadku `copyprivate` nie można używać klauzuli w celu emisji bezpośrednio, ale może służyć do zapewnienia dostępu do udostępnionych obiektów tymczasowych.

```
float read_next( )
{
    float * tmp;
    float return_val;

    #pragma omp single copyprivate(tmp)
    {
        tmp = (float *) malloc(sizeof(float));
    }

    #pragma omp master
    {
        get_float( tmp );
    }

    #pragma omp barrier
    return_val = *tmp;
    #pragma omp barrier

    #pragma omp single
    {
       free(tmp);
    }

    return return_val;
}
```

**Przykład 3:** Załóżmy, że liczba obiektów blokady wymaganymi w ramach równoległego regionu łatwo nie można ustalić przed jej wprowadzeniem. `copyprivate` Klauzuli może służyć do zapewnienia dostępu do blokady współużytkowanej obiektów, które są przydzielane w ramach równoległego regionu.

```
#include <omp.h>

omp_lock_t *new_lock()
{
    omp_lock_t *lock_ptr;

    #pragma omp single copyprivate(lock_ptr)
    {
        lock_ptr = (omp_lock_t *) malloc(sizeof(omp_lock_t));
        omp_init_lock( lock_ptr );
    }

    return lock_ptr;
}
```