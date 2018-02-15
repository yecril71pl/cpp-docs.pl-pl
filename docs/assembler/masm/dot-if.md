---
title: ". JEŚLI | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- .IF
dev_langs:
- C++
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1ad05314b9ee0612622f0b57508d30016eeeff5d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="if"></a>.IF
Generuje kod, który umożliwia sprawdzenie `condition1` (na przykład AX > 7) i wykonuje *instrukcje* Jeśli ten warunek jest spełniony.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
   .IF condition1   
statements  
[[.ELSEIF condition2   
   statements]]  
[[.ELSE  
   statements]]  
.ENDIF  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli [. ELSE](../../assembler/masm/dot-else.md) następujące, jego instrukcje są wykonywane, jeśli fabrycznego była wartość false. Należy pamiętać, że warunki są oceniane w czasie wykonywania.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)