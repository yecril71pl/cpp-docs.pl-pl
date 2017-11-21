---
title: 4.3 OMP_DYNAMIC | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a15edefb-1f85-4f06-a427-beb3cfc4434f
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2b23719d1559a00b807f724a3e31eb7b673a5a17
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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