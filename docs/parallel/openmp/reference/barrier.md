---
title: bariera | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- barrier
dev_langs:
- C++
helpviewer_keywords:
- barrier OpenMP directive
ms.assetid: 5c73ad4f-c768-443a-8f9e-4fd8bc2253c7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0008c343130bf47170957204793cf3c85b22f1e3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="barrier"></a>ograniczenie
Synchronizuje wszystkie wątki w zespole; wszystkie wątki wstrzymane w bariery, dopóki wszystkie wątki wykonania bariera.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma omp barrier  
```  
  
## <a name="remarks"></a>Uwagi  
 `barrier` Dyrektywy obsługuje nie klauzule OpenMP.  
  
 Aby uzyskać więcej informacji, zobacz [2.6.3 dyrektywa określająca bariery](../../../parallel/openmp/2-6-3-barrier-directive.md).  
  
## <a name="example"></a>Przykład  
 Przykładowe zastosowania `barrier`, zobacz [wzorca](../../../parallel/openmp/reference/master.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy](../../../parallel/openmp/reference/openmp-directives.md)