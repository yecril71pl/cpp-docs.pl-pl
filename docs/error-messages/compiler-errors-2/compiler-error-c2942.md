---
title: "C2942 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2942
dev_langs: C++
helpviewer_keywords: C2942
ms.assetid: 13abf744-8fa1-450d-886d-e5717c04956e
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2685762bc57b4ff0c2d056dff4c246d2286503eb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2942"></a>C2942 błąd kompilatora
"class": typ klasy identyfikator ponownie zdefiniować jako formalny argument funkcji  
  
 Klasy ogólne lub szablonu nie można użyć jako formalny argument. Argument nie można przekazać bezpośrednio do konstruktora ogólnego lub klasy szablonu.  
  
 Poniższy przykład generuje C2942:  
  
```  
  
// C2942.cpp  
// compile with: /c  
template<class T>  
struct TC {};   
void f(int TC<int>) {}   // C2942  
  
// OK  
struct TC2 {};  
void f(TC2 i) {}  
```  
  
 C2942 może również wystąpić, gdy użycie typów ogólnych:  
  
```  
// C2942b.cpp  
// compile with: /clr /c  
generic<class T>  
ref struct GC {};  
void f(int GC<int>) {}   // C2942  
ref struct GC2 { };  
void f(int GC2) {}  
```