---
title: . SAFESEH | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ea34448b4dae0525e7feb2fd7cca310a95a6e3c
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32052466"
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