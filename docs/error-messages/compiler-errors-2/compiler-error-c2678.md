---
title: "C2678 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2678
dev_langs: C++
helpviewer_keywords: C2678
ms.assetid: 1f0a4e26-b429-44f5-9f94-cb66441220c8
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d743ba1fbd9b65a7aa8b0f83634848e16b56c407
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2678"></a>C2678 błąd kompilatora
dane binarne "operator": zdefiniowane żadnego operatora, który przyjmuje lewostronny operand typu "type" (lub nie jest dopuszczalne konwersja)  
  
 Użycie operatora, musi ona przeciążenia dla określonego typu lub zdefiniuj konwersji do typu, dla którego zdefiniowano operator.  
  
## <a name="example"></a>Przykład  
 C2678 może wystąpić, gdy lewostronny operand jest kwalifikatora const, ale zdefiniowano operator podjęcie argument wartością stałą.  
  
 Poniższy przykład generuje C2678 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C2678a.cpp  
// Compile by using: cl /EHsc /W4 C2678a.cpp  
struct Combo {  
   int number;  
   char letter;  
};  
  
inline Combo& operator+=(Combo& lhs, int rhs) {  
   lhs.number += rhs;  
   return lhs;  
}  
  
int main() {  
   Combo const combo1{ 42, 'X' };  
   Combo combo2{ 13, 'Z' };  
  
   combo1 += 6; // C2678  
   combo2 += 9; // OK - operator+= matches non-const Combo  
}  
```  
  
## <a name="example"></a>Przykład  
 C2678 może również wystąpić, jeśli przed wywołaniem funkcji członkowskiej na nim nie należy umieszczać natywnego elementu członkowskiego.  
  
 Poniższy przykład generuje C2678 i pokazuje, jak go naprawić.  
  
```  
// C2678.cpp  
// compile with: /clr /c  
struct S { int _a; };  
  
ref class C {  
public:  
   void M( S param ) {  
      test = param;   // C2678  
  
      // OK  
      pin_ptr<S> ptest = &test;  
      *ptest = param;  
   }  
   S test;  
};  
```  
