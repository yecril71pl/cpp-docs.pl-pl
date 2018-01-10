---
title: Operatory preprocesora | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- preprocessor operators
- operators [C++], preprocessor
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f28d2eba75636d6000f909ffe4527ca2b037dd85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="preprocessor-operators"></a>Operatory preprocesora
Cztery operatory preprocesora specyficzne są używane w kontekście `#define` — dyrektywa (zobacz poniżej podsumowanie każdego). W trzech kolejnych sekcjach omówiono operatory tworzenia ciągów, konwersji na znaki i wklejania tokenu. Aby uzyskać informacje dotyczące **zdefiniowane** operatora, zobacz [#if, #elif, #else i #endif — dyrektywy](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md).  
  
|Operator|Akcja|  
|--------------|------------|  
|[Operator tworzenia ciągów (#)](../preprocessor/stringizing-operator-hash.md)|Powoduje, że odpowiednie rzeczywisty argument być ujęta w znaki podwójnego cudzysłowu|  
|[Operator konwersji na znaki (#@)](../preprocessor/charizing-operator-hash-at.md)|Powoduje, że odpowiednie argumentu, aby być ujęta w znaki apostrofu i należy go traktować jako znak (Microsoft Specific)|  
|[Operator wklejania tokenu (##)](../preprocessor/token-pasting-operator-hash-hash.md)|Umożliwia tokeny używane jako argumenty rzeczywiste ma zostać połączony do utworzenia innych tokenów|  
|[defined-operator](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|Upraszcza zapisywanie wyrażenia złożone w niektórych dyrektywy makr|  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)   
 [Wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md)   
 [Dokumentacja preprocesora języka C/C++](../preprocessor/c-cpp-preprocessor-reference.md)