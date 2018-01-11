---
title: "C2245 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2245
dev_langs: C++
helpviewer_keywords: C2245
ms.assetid: 08aaeadf-10ec-485a-b2a6-6e775289082b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aa96c1afce7d53fc8e4fe815349553ce02dfb87a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2245"></a>C2245 błąd kompilatora
nieistniejący element członkowski funkcji "function" określony jako przyjaciel (sygnatura funkcji członkowskiej nie dopasowania do żadnego przeciążenia)  
  
 Nie znaleziono funkcji określony jako przyjaciel przez kompilator.  
  
 Poniższy przykład generuje C2245:  
  
```  
// C2245.cpp  
// compile with: /c  
class B {  
   void f(int i);  
};  
  
class A {  
   int m_i;  
   friend void B::f(char);   // C2245  
   // try the following line instead  
   // friend void B::f(int);  
};  
  
void B::f(int i) {  
   A a;  
   a.m_i = 0;  
}  
```