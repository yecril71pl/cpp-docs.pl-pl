---
title: "C2910 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2910
dev_langs: C++
helpviewer_keywords: C2910
ms.assetid: 09c50e6a-e099-42f6-8ed6-d80e292a7a36
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 202593b506fc957fb98cc390c1874312509ea481
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2910"></a>C2910 błąd kompilatora
"Funkcja": nie może być jawnie specjalizowany  
  
 Kompilator wykrył próbę jawnie specjalizować funkcji dwukrotnie.  
  
 Poniższy przykład generuje C2910:  
  
```  
// C2910.cpp  
// compile with: /c  
template <class T>  
struct S;  
  
template <> struct S<int> { void f() {} };  
template <> void S<int>::f() {}   // C2910 delete this specialization  
```  
  
 C2910 może być również generowany, Jeśli spróbujesz jawnie specjalizować szablonu z systemem innym niż elementu członkowskiego. Oznacza to można tylko jawnie specjalizować szablonu funkcji.  
  
 Poniższy przykład generuje C2910:  
  
```  
// C2910b.cpp  
// compile with: /c  
template <class T> struct A {  
   A(T* p);  
};  
  
template <> struct A<void> {  
   A(void* p);  
};  
  
template <class T>  
inline A<T>::A(T* p) {}  
  
template <> A<void>::A(void* p){}   // C2910  
// try the following line instead  
// A<void>::A(void* p){}  
```  
  
 Ten błąd zostanie również wygenerowany wyniku pracy zgodność kompilatora, która została wykonana w Visual Studio .NET 2003:.  
  
 Kod będzie prawidłowy w wersjach programu Visual Studio .NET 2003 i Visual Studio .NET Visual C++, Usuń `template <>`.  
  
 Poniższy przykład generuje C2910:  
  
```  
// C2910c.cpp  
// compile with: /c  
template <class T> class A {  
   void f();  
};  
  
template <> class A<int> {  
   void f();  
};  
  
template <> void A<int>::f() {}   // C2910  
// try the following line instead  
// void A<int>::f(){}   // OK  
```