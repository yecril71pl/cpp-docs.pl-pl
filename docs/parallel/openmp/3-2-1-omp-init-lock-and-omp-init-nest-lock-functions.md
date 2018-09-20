---
title: 3.2.1 funkcje omp_init_lock i omp_init_nest_lock funkcje | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 098a2721-b16a-484f-bc83-4b8e281e382c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4303eb3ccfcb1c449022a4be32f94b9f91e6e80c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387006"
---
# <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 Funkcje omp_init_lock i omp_init_nest_lock

Te funkcje zapewniają jedynym sposobem inicjowanie blokadę. Każda funkcja inicjuje blokady skojarzonych z parametrem *blokady* do użycia w kolejnych wywołaniach. Format jest następujący:

```
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

Początkowy stan jest odblokowana (oznacza to, że żaden wątek nie jest właścicielem blokady). Na blokadę zagnieżdżalnych początkowa liczba zagnieżdżenia wynosi zero. Jest niezgodna, aby wywołać jedną z tych procedur ze zmienną blokady, który został już zainicjowany.