---
title: C2316 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2316
dev_langs:
- C++
helpviewer_keywords:
- C2316
ms.assetid: 9ad08eb5-060b-4eb0-8d66-0dc134f7bf67
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 895db6535299a077bc32b6485a360ae450e6c87e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2316"></a>C2316 błąd kompilatora

> "*wyjątek*": nie można przechwycić elementu, ponieważ destruktor i/lub Konstruktor kopiujący są niedostępne.  
  
Wystąpił wyjątek według wartości lub według odwołania, ale konstruktora kopiującego i/lub operator przypisania były niedostępne.  
  
Ten kod został zaakceptowany przez wersje programu Visual C++ przed Visual Studio 2003, ale teraz zwraca błąd.  
  
Zgodność programu Visual Studio 2015 zmian tego błędu, Zastosuj do instrukcji catch zły wyjątków MFC pochodzące z `CException`. Ponieważ `CException` ma konstruktora dziedziczone prywatnej kopii, klasy i jej pochodne są z systemem innym niż copyable i nie mogą być przekazywane przez wartość, która oznacza również, że nie można przechwycić przez wartość. CATCH instrukcji, które są objęte wyjątków MFC wartość wcześniej doprowadziło do nieprzechwyconych wyjątków w czasie wykonywania, ale teraz kompilator prawidłowo identyfikuje tej sytuacji i raporty błąd C2316. Aby rozwiązać ten problem, zaleca się, że używasz makr MFC TRY/CATCH, zamiast pisać własne programy obsługi wyjątków, ale jeśli nie jest ona odpowiednia dla kodu, catch wyjątków MFC przez odwołanie zamiast tego.   
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2316:  
  
```  
// C2316.cpp  
// compile with: /EHsc  
#include <stdio.h>  
  
extern "C" int printf_s(const char*, ...);  
  
struct B   
{  
public:  
    B() {}  
    // Delete the following line to resolve.  
private:  
    // copy constructor  
    B(const B&)   
    {  
    }  
};  
  
void f(const B&)   
{  
}  
  
int main()   
{  
    try   
    {  
        B aB;  
        f(aB);  
    }  
    catch (B b) {   // C2316  
        printf_s("Caught an exception!\n");     
    }  
}  
```