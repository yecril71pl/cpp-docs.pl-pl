---
title: "Kompilatora (poziom 1) ostrzeżenie C4090 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4090
dev_langs: C++
helpviewer_keywords: C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3b508e27d72454568e26d2f1d173b05c8a65c250
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4090"></a>Kompilator C4090 ostrzegawcze (poziom 1)
"operacji": kwalifikatory innego modyfikatora  
  
 Zmienna używany w operacji jest zdefiniowana na określonym modyfikatorem, który zapobiega modyfikowaniu bez wykrywania przez kompilator. Wyrażenie jest kompilowana bez żadnych modyfikacji.  
  
 To ostrzeżenie może wystąpić, gdy wskaźnik do **const** lub `volatile` elementu jest przypisany do wskaźnika nie jest zadeklarowany jako wskazujący **const** lub `volatile`.  
  
 To ostrzeżenie zostanie wyświetlone dla programów C. W programie C++, kompilator generuje błąd: [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md).  
  
 Poniższy przykład generuje C4090:  
  
```  
// C4090.c  
// compile with: /W1  
int *volatile *p;  
int *const *q;  
int **r;  
  
int main() {  
   p = q;   // C4090  
   p = r;  
   q = p;   // C4090  
   q = r;  
   r = p;   // C4090  
   r = q;   // C4090  
}  
```