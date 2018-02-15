---
title: "JEŚLI (MASM) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- if
dev_langs:
- C++
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 74d9d223d12164de6a908159eb0d44ea271b0be5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="if-masm"></a>IF (MASM)
Przyznaje zestawu *ifstatements* Jeśli *wyrażenie1* ma wartość true (niezerowej) lub *elseifstatements* Jeśli *wyrażenie1* ma wartość false (0) i *wyrażenie2* ma wartość true.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
   IF expression1  
ifstatements  
[[ELSEIF expression2  
   elseifstatements]]  
[[ELSE  
   elsestatements]]  
ENDIF  
```  
  
## <a name="remarks"></a>Uwagi  
 Może być zastąpiona następujące dyrektywy [ELSEIF](../../assembler/masm/elseif-masm.md): **ELSEIFB**, **elseifdef —**, **ELSEIFDIF**, **ELSEIFDIFI** , **ELSEIFE**, **ELSEIFIDN**, **ELSEIFIDNI**, **ELSEIFNB**, i **elseifndef —** . Opcjonalnie składana *elsestatements* Jeśli poprzednie wyrażenie ma wartość false. Należy pamiętać, że wyrażenia są oceniane w czasie zestawu.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)