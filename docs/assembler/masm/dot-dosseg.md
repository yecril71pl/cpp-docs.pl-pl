---
title: ". DOSSEG — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- .DOSSEG
dev_langs:
- C++
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 39f02937ed1613cbd759621b2a4e75f84db918cf
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="dosseg"></a>.DOSSEG
Porządkuje segmentów zgodnie z Konwencją segmentu systemu MS-DOS: kod najpierw, następnie segmenty nie znajduje się w DGROUP, a następnie segmenty w DGROUP.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
.DOSSEG  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Postępuj zgodnie z segmentów w DGROUP to zamówienie: segmentów nie BSS lub STOS, a następnie BSS segmentów, a na końcu segmentów STOSU. Są używane głównie za zapewnienie obsługi CodeView w programach autonomicznej MASM. Taki sam jak [dosseg —](../../assembler/masm/dosseg.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)