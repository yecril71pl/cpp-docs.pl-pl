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
ms.workload: cplusplus
ms.openlocfilehash: 150b5a0c26be3c3c4d0412157179ebfcbec128e7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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