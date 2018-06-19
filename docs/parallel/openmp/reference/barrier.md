---
title: bariera | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- barrier
dev_langs:
- C++
helpviewer_keywords:
- barrier OpenMP directive
ms.assetid: 5c73ad4f-c768-443a-8f9e-4fd8bc2253c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf5b2cd9edf54e58c06e7d2a48529393cd3ced64
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690897"
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