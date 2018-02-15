---
title: . KOD | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- .CODE
dev_langs:
- C++
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: de0a9b8930c04929b05b02931a1f796d28a78099
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="code"></a>.CODE
W przypadku użycia z [. MODEL](../../assembler/masm/dot-model.md), wskazuje początek segment kodu.  
  
## <a name="syntax"></a>Składnia  
  
```  
.CODE [[name]]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`name`|Opcjonalny parametr określający nazwę segment kodu. Nazwa domyślna to _text — compact niewielki rozmiar, małe i płaski [modele](../../assembler/masm/dot-model.md). Nazwa domyślna to *modulename*_text — w przypadku innych modeli.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania do dyrektyw](../../assembler/masm/directives-reference.md)   
 [.DATA](../../assembler/masm/dot-data.md)