---
title: "C2812 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2812
dev_langs: C++
helpviewer_keywords: C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 859d371d5886ece416ea6d60c405b114a527864f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2812"></a>C2812 błąd kompilatora
\#Import nie jest obsługiwany z/CLR: pure i/CLR: Safe  
  
 **/CLR: pure** i **/CLR: Safe** — opcje kompilatora zostały uznane za przestarzałe w programie Visual Studio 2015.  
  
 [#import — dyrektywa](../../preprocessor/hash-import-directive-cpp.md) nie jest obsługiwany z **/CLR: pure** i **/CLR: Safe** ponieważ `#import` wymaga użycia bibliotek obsługi macierzystego kompilatora.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2812.  
  
```  
// C2812.cpp  
// compile with: /clr:pure /c  
#import "importlib.tlb"   // C2812  
```