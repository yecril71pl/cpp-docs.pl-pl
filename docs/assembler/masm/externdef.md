---
title: "EXTERNDEF — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- EXTERNDEF
dev_langs:
- C++
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a463f4f74f380c6d927419eb498ccd868587ac6d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
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
 [Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)