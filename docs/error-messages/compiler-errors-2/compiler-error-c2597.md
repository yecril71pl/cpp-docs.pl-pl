---
title: C2597 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2597
dev_langs:
- C++
helpviewer_keywords:
- C2597
ms.assetid: 2e48127d-e3ff-4a40-8156-2863e45b1a38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 45cf9054736117526ee5e79c0bafdd8fdee7c2e2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2597"></a>C2597 błąd kompilatora
niedozwolone odwołanie do niestatycznego elementu członkowskiego 'Identyfikator'  
  
 Możliwe przyczyny:  
  
1.  W statycznej funkcji członkowskiej określono niestatycznego elementu członkowskiego. Aby uzyskać dostęp do niestatycznego elementu członkowskiego, musi przekazać w lub Utwórz lokalne wystąpienie klasy i użycie operatora dostępu do elementu członkowskiego (`.` lub `->`).  
  
2.  Określony identyfikator nie jest elementem członkowskim klasy, struktury lub związku. Sprawdzanie pisowni identyfikator.  
  
3.  Operator dostępu do elementu członkowskiego odnosi się do funkcji nieczłonkowskiej.  
  
4.  Poniższy przykład generuje C2597 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C2597.cpp  
// compile with: /c  
struct s1 {  
   static void func();  
   static void func2(s1&);  
   int i;  
};  
  
void s1::func() {  
   i = 1;    // C2597 - static function can't access non-static data member  
}  
  
// OK - fix by passing an instance of s1  
void s1::func2(s1& a) {  
   a.i = 1;  
}  
```