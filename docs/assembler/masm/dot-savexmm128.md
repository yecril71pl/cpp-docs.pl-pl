---
title: . SAVEXMM128 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .SAVEXMM128
dev_langs: C++
helpviewer_keywords: .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4f79fc84e12f536383753d1d5982751cd30099d6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="savexmm128"></a>.SAVEXMM128
Generuje albo `UWOP_SAVE_XMM128` lub `UWOP_SAVE_XMM128_FAR` unwind wpis kod dla określonego rejestru XMM i przesunięcie, przy użyciu bieżącego przesunięcie prologu. MASM wybierze najbardziej efektywne kodowanie.  
  
## <a name="syntax"></a>Składnia  
  
```  
.savexmm128 xmmreg , offset  
```  
  
## <a name="remarks"></a>Uwagi  
 . SAVEXMM128 umożliwia użytkownikom ml64.exe określające, jak funkcja ramki cofa i jest dozwolone tylko w prologu, który rozciąga się od [PROC](../../assembler/masm/proc.md) deklaracji ramki [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) dyrektywy. Dyrektywy te nie generują kod; tylko generowanie `.xdata` i `.pdata`. . SAVEXMM128 powinien być poprzedzony instrukcje faktycznie implementujących działania, które można oddzielić. Jest dobrą praktyką jest zawijany zarówno dyrektywy unwind i kodu, które są przeznaczone do unwind w makrze do zapewnienia umowy.  
  
 `offset`musi być wielokrotnością 16.  
  
 Aby uzyskać więcej informacji, zobacz [MASM dla x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania do dyrektyw](../../assembler/masm/directives-reference.md)