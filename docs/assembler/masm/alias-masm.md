---
title: ALIAS (MASM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Alias
dev_langs:
- C++
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b14e1c41a448d0cb7014dabc50a42305249938f
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32049170"
---
# <a name="alias-masm"></a>ALIAS (MASM)
**ALIAS** dyrektywy tworzy alternatywną nazwę funkcji.  Dzięki temu można utworzyć wiele nazw dla funkcji lub bibliotek, które umożliwia konsolidator (LINK.exe) do mapowania funkcji starego nową funkcję.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
ALIAS  <  
alias  
> = <  
actual-name  
>  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `actual-name`  
 Rzeczywistą nazwą funkcji lub procedury.  Nawiasy są wymagane.  
  
 `alias`  
 Alternatywną nazwę.  Nawiasy są wymagane.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)