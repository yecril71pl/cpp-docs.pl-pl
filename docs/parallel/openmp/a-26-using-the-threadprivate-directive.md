---
title: A.26 użycie dyrektywy threadprivate | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6eda76c2-c4f1-4208-a900-e0ea98a53eca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93a596a4015f92e2a4d42151560171157232047b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447654"
---
# <a name="a26---using-the-threadprivate-directive"></a>A.26   Użycie dyrektywy prywatnego wątku

W poniższych przykładach pokazano sposób użycia `threadprivate` — dyrektywa ([sekcji 2.7.1](../../parallel/openmp/2-7-1-threadprivate-directive.md) na stronie 23) pozwala każdy wątek oddzielne licznika.

**Przykład 1:**

```
int counter = 0;
#pragma omp threadprivate(counter)

int sub()
{
    counter++;
    return(counter);
}
```

**Przykład 2:**

```
int sub()
{
    static int counter = 0;
    #pragma omp threadprivate(counter)
    counter++;
    return(counter);
}
```