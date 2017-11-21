---
title: ". DOSSEG — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .DOSSEG
dev_langs: C++
helpviewer_keywords: .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4d2156161686583ba00d357c1dbca2e2e2867e9b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Odwołania do dyrektyw](../../assembler/masm/directives-reference.md)