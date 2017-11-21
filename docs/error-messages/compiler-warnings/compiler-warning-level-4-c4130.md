---
title: "Kompilatora (poziom 4) ostrzeżenie C4130 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4130
dev_langs: C++
helpviewer_keywords: C4130
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 577d241be51209dfbe65ad8c46556a1abcdb431e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4130"></a>Kompilator C4130 ostrzegawcze (poziom 4)
"operator": operacja logiczna na adresie ciągu stałych  
  
 Przy użyciu operatora z adresem literału ciągu znaków powoduje nieoczekiwany kod.  
  
 Poniższy przykład generuje C4130:  
  
```  
// C4130.cpp  
// compile with: /W4  
int main()  
{  
   char *pc;  
   pc = "Hello";  
   if (pc == "Hello") // C4130  
   {  
   }  
}  
```  
  
 **Jeśli** instrukcji porównuje wartość przechowywana we wskaźniku `pc` na adres ciąg "Hello", który jest przydzielony oddzielnie zawsze występuje ciąg w kodzie. **Jeśli** instrukcji porównuje ciąg wskazywana przez `pc` z ciągiem "Hello".  
  
 Aby porównać ciągów, należy użyć `strcmp` funkcji.