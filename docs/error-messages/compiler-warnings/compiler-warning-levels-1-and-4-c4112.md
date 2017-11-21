---
title: "Kompilator C4112 ostrzeżenie (poziomy 1 i 4) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4112
dev_langs: C++
helpviewer_keywords: C4112
ms.assetid: aff64897-bb79-4a67-9b6f-902c6d44f3dc
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 868411c2cef9ef6b984e95b5f5c6abaebd8ff91a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-levels-1-and-4-c4112"></a>Kompilator C4112 ostrzeżenie (poziomy 1 i 4)
\#wiersz wymaga całkowitą z przedziału od 1 i numer  
  
 [#Line](../../preprocessor/hash-line-directive-c-cpp.md) dyrektywa określa parametr liczba całkowita jest poza dozwolonym zakresem.  
  
 Jeśli określony parametr jest mniejszy niż 1, licznik wierszy jest zmieniany na 1. Jeśli określony parametr jest większa niż *numer*, która jest limit zdefiniowany przez kompilator, licznik wierszy jest bez zmian. Jest to ostrzeżenia poziomu 1, w obszarze Zgodność ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) i ostrzeżenie poziom 4 z rozszerzeniami firmy Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).  
  
 Poniższy przykład generuje C4112:  
  
```  
// C4112.cpp  
// compile with: /W4  
#line 0   // C4112, value must be between 1 and number  
  
int main() {  
}  
```