---
title: "C2512 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2512
dev_langs: C++
helpviewer_keywords: C2512
ms.assetid: 15206da9-1164-451a-b869-280e00711aad
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 63090bc7dac08aa87bcd68e77c076185176a7285
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2512"></a>C2512 błąd kompilatora
'Identyfikator': nie niedostępny odpowiedni konstruktor domyślny  
  
 Brak domyślnego konstruktora jest dostępna dla określonej klasy, struktury lub związku. Kompilator udostępnia domyślny konstruktor tylko wtedy, gdy nie podano konstruktorów zdefiniowanych przez użytkownika.  
  
 Jeśli podasz konstruktora, który przyjmuje parametr inny niż void, a chcesz zezwolić na klasie ma zostać utworzony bez parametrów — na przykład jako elementy tablicy — należy również podać konstruktora domyślnego. Domyślny konstruktor może być konstruktora z wartościami domyślnymi dla wszystkich parametrów.  
  
 Poniższy przykład generuje C2512 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C2512.cpp  
// C2512 expected  
struct B {  
   B (char *);  
   // Uncomment the following line to fix.  
   // B() {};  
};  
  
int main() {  
   B b;   
}  
```  
  
 Poniższy przykład przedstawia C2512 aspekty. Aby naprawić ten błąd, rozmieszczanie kod, aby zdefiniować klasy przed jego konstruktora odwołuje się do:  
  
```  
// C2512b.cpp  
// compile with: /c  
struct S {  
   struct X;  
  
   void f() {  
      X *x = new X();   // C2512 X not defined yet  
   }  
  
};  
  
struct S::X {};  
  
struct T {  
   struct X;  
   void f();  
};  
  
struct T::X {};  
  
void T::f() {  
   X *x = new X();  
}  
```  
  
 C2512 mogą także być spowodowane przez wywołanie do domyślnego — konstrukcja klasę, która zawiera stałą lub element członkowski danych odwołania. Elementy te muszą zostać zainicjowane na liście inicjatora konstruktora, który uniemożliwia kompilatorowi wygenerowanie konstruktora domyślnego.  
  
 Poniższy przykład generuje C2512 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C2512c.cpp  
// Compile by using: cl /c /W3 C2512c.cpp  
struct S {  
   const int i_;  
   int &r_;   
};   
  
int SumS() {  
   const int ci = 7;  
   int ir = 42;  
  
   S s1; // C2512 - no default constructor available  
   S s2{ci, ir};  // Fix - initialize const and reference members   
   return s2.i_ + s2.r_;  
}  
```