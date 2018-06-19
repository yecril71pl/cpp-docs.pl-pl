---
title: EXTERNDEF — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- EXTERNDEF
dev_langs:
- C++
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b010f52f91a04388f34052fcc5c374690cff13df
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32052703"
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