---
title: "Kompilatora (poziom 1) ostrzeżenie C4669 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4669
dev_langs: C++
helpviewer_keywords: C4669
ms.assetid: 97730679-e3dc-44d4-b2a8-aa65badc17f2
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 203650a0d1e53fe9e13ca6dae58dfa3d0a42e4ec
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4669"></a>Kompilator C4669 ostrzegawcze (poziom 1)
Instrukcja "cast": niebezpieczna konwersja: "class" jest zarządzanego lub obiekt typu WinRT  
  
 Rzutowanie zawiera środowiska wykonawczego systemu Windows lub typ zarządzany. Kompilator zakończeniu rzutowanie, wykonując kopię operacja jeden wskaźnik do drugiego, ale zapewnia nie sprawdzenia. Aby usunąć to ostrzeżenie, nie Rzutuj klasy zawierające zarządzanych elementów członkowskich lub typów środowiska wykonawczego systemu Windows.  
  
 Poniższy przykład generuje C4669 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C4669.cpp  
// compile with: /clr /W1  
ref struct A {  
   int i;  
   Object ^ pObj;   // remove the managed member to fix the warning  
};  
  
ref struct B {  
   int j;  
};  
  
int main() {  
   A ^ a = gcnew A;  
   B ^ b = reinterpret_cast<B ^>(a);   // C4669  
}  
```