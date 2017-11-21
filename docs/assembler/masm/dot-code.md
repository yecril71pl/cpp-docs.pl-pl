---
title: . KOD | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .CODE
dev_langs: C++
helpviewer_keywords: .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4a884f4d3d1f754f12a23d6e24a6c1b533104e89
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [. DANE](../../assembler/masm/dot-data.md)