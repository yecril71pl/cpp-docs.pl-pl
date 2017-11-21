---
title: bariera | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: barrier
dev_langs: C++
helpviewer_keywords: barrier OpenMP directive
ms.assetid: 5c73ad4f-c768-443a-8f9e-4fd8bc2253c7
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4ce85fce6e4f1611381026bd365760b02d3d174f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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