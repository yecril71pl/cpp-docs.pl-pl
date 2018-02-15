---
title: . PUSHREG | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- .PUSHREG
dev_langs:
- C++
helpviewer_keywords:
- .PUSHREG directive
ms.assetid: e0c83758-dfed-40ea-afe6-cb833c8d2d30
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 84cc00d51f72993e1e7673d8d4f3d01478d32041
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="pushreg"></a>.PUSHREG
Generuje `UWOP_PUSH_NONVOL` unwind kod dla określonego zarejestrować numer przy użyciu bieżącego przesunięcie w prologu.  
  
## <a name="syntax"></a>Składnia  
  
```  
.PUSHREG register  
```  
  
## <a name="remarks"></a>Uwagi  
 . PUSHREG umożliwia użytkownikom ml64.exe określające, jak funkcja ramki cofa i jest dozwolone tylko w prologu, który rozciąga się od [PROC](../../assembler/masm/proc.md) deklaracji ramki [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) dyrektywy. Dyrektywy te nie generują kod; tylko generowanie `.xdata` i `.pdata`. . PUSHREG powinien być poprzedzony instrukcje faktycznie implementujących działania, które można oddzielić. Jest dobrą praktyką jest zawijany zarówno dyrektywy unwind i kodu, które są przeznaczone do unwind w makrze do zapewnienia umowy.  
  
 Aby uzyskać więcej informacji, zobacz [MASM dla x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
## <a name="sample"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład przedstawia sposób tegisters trwałej push.  
  
### <a name="code"></a>Kod  
  
```  
; ml64 ex1.asm /link /entry:Example1 /SUBSYSTEM:CONSOLE  
_text SEGMENT  
Example1 PROC FRAME  
   push r10  
.pushreg r10  
   push r15  
.pushreg r15  
   push rbx  
.pushreg rbx  
   push rsi  
.pushreg rsi  
.endprolog  
   ; rest of function ...  
   ret  
Example1 ENDP  
_text ENDS  
END  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)