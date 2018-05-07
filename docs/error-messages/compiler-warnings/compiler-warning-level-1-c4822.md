---
title: Kompilatora (poziom 1) ostrzeżenie C4822 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4822
dev_langs:
- C++
helpviewer_keywords:
- C4822
ms.assetid: 0f231a30-2eb0-4722-aaa0-e2d19d3e7eea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9491d522c65eba3599c3618d510c57b55682876
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4822"></a>Kompilator C4822 ostrzegawcze (poziom 1)
"członek": funkcja członkowska klasy lokalnej nie ma treści  
  
 Funkcja członkowska klasy lokalnej został zadeklarowany, ale nie jest zdefiniowana w klasie. Aby używać funkcji członkowskiej klasy lokalnej, należy zdefiniować ją w klasie. Nie można zadeklarować go w klasie i zdefiniować go poza klasy.  
  
 Wszelkie-klasy definicji funkcji członkowskiej klasy lokalnej będzie wystąpił błąd.  
  
 Poniższy przykład generuje C4822:  
  
```  
// C4822.cpp  
// compile with: /W1  
int main() {  
   struct C {  
      void func1(int);   // C4822  
      // try the following line instead  
      // void func1(int){}  
  };  
}  
```