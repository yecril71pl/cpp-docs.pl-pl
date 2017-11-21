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
ms.openlocfilehash: c0eaa2a5c689dbe63957e5a0d5dcb8bbd1959949
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Odwołania preprocesora C/C++](../preprocessor/c-cpp-preprocessor-reference.md)