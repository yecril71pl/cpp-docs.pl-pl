---
title: . JEŚLI | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .IF
dev_langs:
- C++
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ab0e2fc510b4be8c5a9a8c0c3d0fb1c4347f0b9
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
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