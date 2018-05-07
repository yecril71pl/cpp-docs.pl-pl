---
title: C3203 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3203
dev_langs:
- C++
helpviewer_keywords:
- C3203
ms.assetid: 6356770e-22c1-434c-91fe-f60b0aa23b91
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81548f5fc8fc4a28a4ad85e4611eba9440d6f107
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3203"></a>C3203 błąd kompilatora
'type': szablon klasy niespecjalizowanej klasy lub ogólny nie może służyć jako szablon lub argumentów ogólnych dla szablonu lub parametru ogólnego "param", oczekiwano typu rzeczywistego  
  
 Nieprawidłowy argument został przekazany do szablonu klasy lub ogólny. Szablon klasy lub rodzajowa oczekuje typu jako parametru.  
  
 Ten błąd może być wygenerowanego w wyniku pracy zgodność kompilatora, która została wykonana dla Visual C++ 2005: nie można użyć szablonu klasy niespecjalizowanej klasy jako argument szablonu na liście klas podstawowych. Aby rozwiązać C3203, jawnie dodać parametrów typu szablonu Nazwa klasy szablonu w przypadku używania go jako parametr szablonu na liście klas podstawowych.  
  
```  
// C3203.cpp  
template< typename T >  
struct X {  
   void f(X) {}  
};  
  
template< typename T >  
struct Y : public X<Y> {   // C3203  
// try the following line instead  
// struct Y : public X<Y<T> > {  
   void f(Y) {}  
};  
  
int main() {  
   Y<int> y;  
}  
```  
  
 Poniższy przykład generuje C3203 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C3203_b.cpp  
// compile with: /c  
template <class T>  
struct S1 {};  
  
template <class T>  
class C1 {};  
  
typedef C1<S1> MyC1;   // C3203  
  
// OK  
template <template <class> class T>  
class C2 {};  
  
typedef C2<S1> MyC1;  
  
template <class T>  
class C3 {};  
  
typedef C3<S1<int> > MyC12;  
```  
  
 C3203 może również wystąpić, gdy użycie typów ogólnych:  
  
```  
// C3203_c.cpp  
// compile with: /clr /c  
generic <class T>  
value struct GS1 {};  
  
generic <class T>  
value struct GC1 {};  
  
typedef GC1<GS1> MyGC1;   // C3203  
typedef GC1<GS1<int> > MyGC2;   // OK  
```