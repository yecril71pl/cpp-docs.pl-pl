---
title: Operatory preprocesora | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor operators
- operators [C++], preprocessor
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 551b2c3ba8a5055fc6b6dfd1b94c461c37e72209
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
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