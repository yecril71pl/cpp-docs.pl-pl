---
title: C3849 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3849
dev_langs:
- C++
helpviewer_keywords:
- C3849
ms.assetid: 5347140e-1a81-4841-98c0-b63d98264b64
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e771e67e3432273c8b3880b44d04e4a17217960b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270967"
---
# <a name="compiler-error-c3849"></a>C3849 błąd kompilatora
Wywołanie w stylu funkcji na wyrażeniu typu "type" spowoduje utratę kwalifikatorów const i/lub volatile dla wszystkich liczba dostępnych przeciążeń operatora  
  
 Zmienna z określonym typem const-volatile można wywołać tylko członek funkcje zdefiniowane z kwalifikacji const-volatile sam lub większy.  
  
 Aby naprawić ten błąd, podaj funkcję właściwego członka. Nie można wykonać konwersji na typu const lub volatile kwalifikowaną obiektu, gdy konwersji powoduje utratę kwalifikacji. Kwalifikatory można uzyskać, ale nie utratę kwalifikatorów w konwersji.  
  
 Poniższe przykłady Generowanie C3849:  
  
```  
// C3849.cpp  
void glbFunc3(int i, char c)  
{  
   i;  
}  
typedef void (* pFunc3)(int, char);  
  
void glbFunc2(int i)  
{  
   i;  
}  
  
typedef void (* pFunc2)(int);  
  
void glbFunc1()  
{  
}  
typedef void (* pFunc1)();  
  
struct S4  
{  
   operator ()(int i)  
   {  
      i;  
   }  
  
   operator pFunc1() const  
   {  
      return &glbFunc1;  
   }  
  
   operator pFunc2() volatile  
   {  
      return &glbFunc2;  
   }  
  
   operator pFunc3()  
   {  
      return &glbFunc3;  
   }  
  
   // operator pFunc1() const volatile  
   // {  
   //    return &glbFunc1;  
   // }  
};  
  
int main()  
{  
   // Cannot call any of the 4 overloads of "operator ()(.....)" and   
   // "operator pFunc()" because none is declared as "const volatile"  
   const volatile S4 s4;  // can only call cv member functions of S4  
   s4();   // C3849 to resolve, uncomment member function  
}  
```