---
title: "Kompilatora (poziom 3) ostrzeżenie C4018 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4018
dev_langs:
- C++
helpviewer_keywords:
- C4018
ms.assetid: 6e8cbb04-d914-4319-b431-cbc2fbe40eb1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 84a8efdd90a4f93e1eda779ca0e23e339099181e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4018"></a>Kompilator C4018 ostrzegawcze (poziom 3)
"wyrażenie": niezgodność podpisany niepodpisane  
  
 Porównanie liczby znakiem i bez znaku wymagany kompilator, aby przekonwertować podpisem wartości bez znaku.  
  
 Może zostać ustalona to ostrzeżenie, jeśli można rzutować jeden z dwóch typów podczas testowania typy znakiem i bez znaku.  
  
 Poniższy przykład generuje C4018:  
  
```  
// C4018.cpp  
// compile with: /W3  
int main() {  
   unsigned int uc = 0;  
   int c = 0;  
   unsigned int c2 = 0;  
  
   if (uc < c) uc = 0;   // C4018  
  
   // OK  
   if (uc == c2) uc = 0;  
}  
```