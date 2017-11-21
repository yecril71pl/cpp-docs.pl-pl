---
title: "JEŚLI (MASM) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: if
dev_langs: C++
helpviewer_keywords: IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b6ddb2c9d9ec6e39a0147d513fb452685d8e7213
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Odwołania do dyrektyw](../../assembler/masm/directives-reference.md)