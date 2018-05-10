---
title: 4.3 OMP_DYNAMIC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a15edefb-1f85-4f06-a427-beb3cfc4434f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f376fe639d9bca58b6e2bd55fd081b88921a7342
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="43-ompdynamic"></a>4.3 OMP_DYNAMIC
**OMP_DYNAMIC** zmiennej środowiskowej Włącza lub wyłącza dynamiczne Dostosowywanie liczba wątków dostępnych do wykonywania równoległego regionów, chyba że jawnie włączyć lub wyłączyć przez wywołanie metody dynamiczneDostosowywanie**omp_set_dynamic** procedury biblioteki. Wartość musi być **TRUE** lub **FALSE**.  
  
 Jeśli ustawiono **TRUE**, liczba wątków, które są używane do wykonywania równoległego regiony mogą być dostosowywane przez środowisko uruchomieniowe najlepiej wykorzystać zasoby systemowe.  Jeśli ustawiono **FALSE**, dynamiczne Dostosowywanie jest wyłączona. Stan domyślny jest zdefiniowane w implementacji.  
  
 Przykład:  
  
```  
setenv OMP_DYNAMIC TRUE  
```  
  
## <a name="cross-references"></a>Odsyłacze:  
  
-   Aby uzyskać więcej informacji na równoległych regionów, zobacz [2.3 sekcji](../../parallel/openmp/2-3-parallel-construct.md) na stronie 8.  
  
-   **omp_set_dynamic** funkcji, zobacz [sekcji 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stronie 39.