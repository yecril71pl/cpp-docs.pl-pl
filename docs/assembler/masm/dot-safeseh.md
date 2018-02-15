---
title: .SAFESEH | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- .SAFESEH
dev_langs:
- C++
helpviewer_keywords:
- registering functions as exception handlers
- SAFESEH directive
- .SAFESEH directive
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 69212e7a3542a6b6ac88ccbe2ecbbf8894862e65
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="safeseh"></a>.SAFESEH
Rejestruje funkcję obsługi wyjątków strukturalnych.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
.SAFESEH identifier  
```  
  
## <a name="remarks"></a>Uwagi  
 *Identyfikator* musi być Identyfikatorem dla zdefiniowanego lokalnie [PROC](../../assembler/masm/proc.md) lub [extrn —](../../assembler/masm/extrn.md) obrady A [etykiety](../../assembler/masm/label-masm.md) jest niedozwolone. . SAFESEH — dyrektywa wymaga [opcja/SAFESEH](../../assembler/masm/ml-and-ml64-command-line-reference.md) ml.exe opcji wiersza polecenia.  
  
 Aby uzyskać więcej informacji na temat obsługi wyjątków strukturalnych, zobacz [opcja/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md).  
  
 Na przykład można zarejestrować obsługi wyjątków bezpieczne, Utwórz nowy plik MASM (następujący), złóż z opcja/SAFESEH i dodać go do powiązane obiekty.  
  
```  
.386  
.model  flat  
MyHandler   proto  
.safeseh    MyHandler  
end  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)