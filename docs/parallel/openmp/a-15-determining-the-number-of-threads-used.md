---
title: A.15 Określanie liczby wykorzystywanych wątków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 026bb59a-f668-40db-a7cb-69a1bae83d2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1042b4871f53bddb5cff894330f3afe7d8a088ef
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428744"
---
# <a name="a15---determining-the-number-of-threads-used"></a>A.15   Określanie liczby wykorzystywanych wątków

Rozważmy następujący przykład niepoprawny (dla [sekcji 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stronie 37):

```
np = omp_get_num_threads(); // misplaced
#pragma omp parallel for schedule(static)
    for (i=0; i<np; i++)
        work(i);
```

`omp_get_num_threads()` Wywołania zwraca 1 serial sekcji kodu, więc *potoki* zawsze będzie równy 1 w powyższym przykładzie. Aby określić liczbę wątków, które zostaną wdrożone do równoległego regionu, wywołanie powinno być w ramach równoległego regionu.

Poniższy przykład pokazuje, jak ponownie zapisać ten program bez uwzględniania zapytanie dotyczące liczby wątków:

```
#pragma omp parallel private(i)
{
    i = omp_get_thread_num();
    work(i);
}
```