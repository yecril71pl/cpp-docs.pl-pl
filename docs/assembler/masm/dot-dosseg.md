---
title: . DOSSEG — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .DOSSEG
dev_langs:
- C++
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3817cfe98758faf86ea87d74e02657598c3e806b
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32054889"
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