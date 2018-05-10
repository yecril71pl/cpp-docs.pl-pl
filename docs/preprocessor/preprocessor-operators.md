---
title: Operatory preprocesora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor operators
- operators [C++], preprocessor
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da6ff2a87007892cb5a76e7fc003e1d172056fb0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
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