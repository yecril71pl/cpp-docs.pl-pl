---
title: JEŚLI (MASM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- if
dev_langs:
- C++
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 76bf63b917a65a5a41fd261cfc861a77b0f0d16f
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32054006"
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