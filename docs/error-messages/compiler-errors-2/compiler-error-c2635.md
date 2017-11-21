---
title: "C2635 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2635
dev_langs: C++
helpviewer_keywords: C2635
ms.assetid: 9deca2a8-2d61-42eb-9783-6578132ee3fb
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8a8ff1361a312c8d2abf7e07de3add2dbd3254ca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2635"></a>C2635 błąd kompilatora
Nie można przekonwertować "identifier1 *" na "identifier2\*"; technicznego konwersję z wirtualnej klasy podstawowej  
  
 Konwersja wymaga rzutowania z `virtual` klasy podstawowej na klasę pochodną, co jest niedozwolone.  
  
 Poniższy przykład generuje C2635:  
  
```  
// C2635.cpp  
class B {};  
class D : virtual public B {};  
class E : public B {};  
  
int main() {  
   B b;  
   D d;  
   E e;  
  
   D * pD = &d;  
   E * pE = &e;  
   pD = (D*)&b;   // C2635  
   pE = (E*)&b;   // OK  
}  
```