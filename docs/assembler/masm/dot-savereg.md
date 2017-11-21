---
title: . SAVEREG | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .SAVEREG
dev_langs: C++
helpviewer_keywords: .SAVEREG directive
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e55abe8a5661184b022fad3f6a50dc9813cae9d8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="savereg"></a>.SAVEREG
Generuje albo `UWOP_SAVE_NONVOL` lub `UWOP_SAVE_NONVOL_FAR` unwind wpis kod dla określonego rejestru (`reg`) i przesunięcia (`offset`) przy użyciu bieżącego przesunięcie prologu. MASM wybierze najbardziej efektywne kodowanie.  
  
## <a name="syntax"></a>Składnia  
  
```  
.SAVEREG reg, offset  
```  
  
## <a name="remarks"></a>Uwagi  
 . SAVEREG umożliwia użytkownikom ml64.exe określić, jak funkcja ramki cofa i jest dozwolone tylko w prologu, który rozciąga się od [PROC](../../assembler/masm/proc.md) deklaracji ramki [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) dyrektywy. Dyrektywy te nie generują kod; tylko generowanie `.xdata` i `.pdata`. . SAVEREG powinien być poprzedzony instrukcje faktycznie implementujących działania, które można oddzielić. Jest dobrą praktyką jest zawijany zarówno dyrektywy unwind i kodu, które są przeznaczone do unwind w makrze do zapewnienia umowy.  
  
 Aby uzyskać więcej informacji, zobacz [MASM dla x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania do dyrektyw](../../assembler/masm/directives-reference.md)