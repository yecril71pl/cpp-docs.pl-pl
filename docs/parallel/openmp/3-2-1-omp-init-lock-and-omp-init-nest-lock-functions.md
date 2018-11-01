---
title: 3.2.1 Funkcje omp_init_lock i omp_init_nest_lock
ms.date: 11/04/2016
ms.assetid: 098a2721-b16a-484f-bc83-4b8e281e382c
ms.openlocfilehash: 2d15aacb5e6743d18150fb45bea85b7ca22a401f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472783"
---
# <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 Funkcje omp_init_lock i omp_init_nest_lock

Te funkcje zapewniają jedynym sposobem inicjowanie blokadę. Każda funkcja inicjuje blokady skojarzonych z parametrem *blokady* do użycia w kolejnych wywołaniach. Format jest następujący:

```
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

Początkowy stan jest odblokowana (oznacza to, że żaden wątek nie jest właścicielem blokady). Na blokadę zagnieżdżalnych początkowa liczba zagnieżdżenia wynosi zero. Jest niezgodna, aby wywołać jedną z tych procedur ze zmienną blokady, który został już zainicjowany.