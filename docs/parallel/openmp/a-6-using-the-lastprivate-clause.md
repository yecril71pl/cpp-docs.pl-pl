---
title: A.6 użycie klauzuli lastprivate | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cf3bf0cc-aa46-4e44-9433-e2969e3be2c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 03d18d3aaf5c5d1cbe03282710ae4f4e2bb613f3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390582"
---
# <a name="a6---using-the-lastprivate-clause"></a>A.6   Użycie klauzuli ostatniej prywatnej

Czasami prawidłowe wykonanie zależy od wartości ostatniej iteracji pętli jest przypisywany do zmiennej. Programów, które musi zawierać takich zmiennych jako argumenty `lastprivate` — klauzula ([2.7.2.3 ostatnia sekcja](../../parallel/openmp/2-7-2-3-lastprivate.md) na stronie 27) tak, aby wartości zmiennych są takie same jak kiedy pętla jest wykonywana sekwencyjnie.

```
#pragma omp parallel
{
   #pragma omp for lastprivate(i)
      for (i=0; i<n-1; i++)
         a[i] = b[i] + b[i+1];
}
a[i]=b[i];
```

W poprzednim przykładzie wartość `i` na końcu równoległego regionu będzie równa `n-1`, jak w przypadku sekwencyjnych.