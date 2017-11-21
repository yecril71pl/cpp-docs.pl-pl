---
title: "EXTERNDEF — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EXTERNDEF
dev_langs: C++
helpviewer_keywords: EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 64aa9cc69825ef1f932024bc45c051e16c99e2eb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="externdef"></a>EXTERNDEF
Określa jeden lub więcej zmiennych zewnętrznych, etykiety lub symbole o nazwie *nazwa* o typie `type`.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
EXTERNDEF [[langtype]] name:type [[, [[langtype]] name:type]]...  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli *nazwa* jest zdefiniowany w module jest traktowany jako [publicznego](../../assembler/masm/public-masm.md). Jeśli *nazwa* odwołuje się do modułu, jest traktowany jako [EXTERN](../../assembler/masm/extern-masm.md). Jeśli *nazwa* jest nie odwołuje się do, jest ignorowana. `type` Może być [ABS](../../assembler/masm/operator-abs.md), który importuje *nazwa* jako stała. Zwykle używane w pliki dołączane.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania do dyrektyw](../../assembler/masm/directives-reference.md)