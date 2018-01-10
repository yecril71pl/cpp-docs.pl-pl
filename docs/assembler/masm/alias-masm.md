---
title: ALIAS (MASM) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Alias
dev_langs: C++
helpviewer_keywords: ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 59dc4fd5481b22e69153c68e94a81b2887118ebc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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