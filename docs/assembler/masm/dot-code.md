---
title: . KOD | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .CODE
dev_langs:
- C++
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 59e376fc9c10ab8891b02e4da334341ae0534b73
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
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