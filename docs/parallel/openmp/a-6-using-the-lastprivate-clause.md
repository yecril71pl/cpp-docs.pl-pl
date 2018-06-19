---
title: Przy użyciu lastprivate klauzuli A.6 | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: eec6ddc46aab36671e767963e5aaf6e25c4d25cd
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690546"
---
# <a name="a6---using-the-lastprivate-clause"></a>A.6   Użycie klauzuli ostatniej prywatnej
Czasami prawidłowe wykonanie zależy od wartości przypisującej ostatnich iteracji pętli do zmiennej. Programów, które musi zawierać takie zmienne jako argumenty do `lastprivate` klauzuli ([sekcji 2.7.2.3 ostatnia](../../parallel/openmp/2-7-2-3-lastprivate.md) na stronie 27) tak, aby wartości zmiennych są takie same jak podczas pętli jest wykonywane sekwencyjnie.  
  
```  
#pragma omp parallel  
{  
   #pragma omp for lastprivate(i)  
      for (i=0; i<n-1; i++)  
         a[i] = b[i] + b[i+1];  
}  
a[i]=b[i];  
```  
  
 W powyższym przykładzie wartość `i` na końcu równoległego regionu będzie równa `n-1`, jak w przypadku sekwencyjnych.