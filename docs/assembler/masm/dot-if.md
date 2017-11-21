---
title: ". JEŚLI | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .IF
dev_langs: C++
helpviewer_keywords: .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2416b73fa42f9cac629644ea624a9545f3988dc3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Odwołania do dyrektyw](../../assembler/masm/directives-reference.md)