---
title: C2864 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2864
dev_langs:
- C++
helpviewer_keywords:
- C2864
ms.assetid: d0ca2ad9-90a6-4aef-8511-98a3b414c102
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a9f85b404fa74895cb623612331f232cf39d8407
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2864"></a>C2864 błąd kompilatora
'zmienna': statyczna składowa danych z inicjatorem w klasie musi być typu nieulotnego stałego całkowitoliczbowego  
  
 Zainicjować `static` element członkowski danych, która jest zdefiniowana jako `volatile`, nie-`const`, lub nie typem całkowitym typu, użyj instrukcji definicji elementu członkowskiego. Nie mogą one być inicjowane w deklaracji.  
  
 W tym przykładzie generuje C2864:  
  
```  
// C2864.cpp  
// compile with: /c  
class B  {  
private:  
   int a = 3;   // OK   
   static int b = 3;   // C2864  
   volatile static int c = 3;   // C2864  
   volatile static const int d = 3;   // C2864  
   const static long long e = 3;   // OK  
   static const double f = 3.33;   // C2864  
};  
```  
  
 Ten przykład pokazuje, jak naprawić C2864:  
  
```  
// C2864b.cpp  
// compile with: /c  
class C  {  
private:  
   int a = 3;  
   static int b; // = 3; C2864  
   volatile static int c; // = 3; C2864  
   volatile static const int d; // = 3; C2864  
   static const long long e = 3;  
   static const double f; // = 3.33; C2864  
};  
  
// Initialize static volatile, non-const, or non-integral  
// data members when defined, not when declared:  
int C::b = 3;  
volatile int C::c = 3;  
volatile const int C::d = 3;  
const double C::f = 3.33;  
```