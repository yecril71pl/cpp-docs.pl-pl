---
title: C2885 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2885
dev_langs:
- C++
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f37ea0f9fadb74b44eea5ad110f7f12b884f0e41
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33244175"
---
# <a name="compiler-error-c2885"></a>C2885 błąd kompilatora
"class::identifier": nie Nieprawidłowa deklaracja using w zakresie nieklasowym  
  
 Możesz użyć [przy użyciu](../../cpp/using-declaration.md) deklaracji niepoprawnie.  
  
## <a name="example"></a>Przykład  
 Ten błąd może być wygenerowanego w wyniku pracy zgodność kompilatora, która została wykonana dla Visual C++ 2005: nie jest już prawidłowy mają `using` deklaracji typu zagnieżdżonego; musi jawnie kwalifikować się każde odwołanie dokonać typu zagnieżdżonego, umieść typ w nazwie miejsce, lub utworzyć jako element typedef.  
  
 Poniższy przykład generuje C2885.  
  
```  
// C2885.cpp  
namespace MyNamespace {  
   class X1 {};  
}  
  
struct MyStruct {  
   struct X1 {  
      int i;  
   };  
};  
  
int main () {  
   using MyStruct::X1;   // C2885  
  
   // OK  
   using MyNamespace::X1;  
   X1 myX1;  
  
   MyStruct::X1 X12;  
  
   typedef MyStruct::X1 abc;  
   abc X13;  
   X13.i = 9;  
}  
```  
  
## <a name="example"></a>Przykład  
 Jeśli używasz `using` — słowo kluczowe z elementem członkowskim klasy C++ wymaga zdefiniowania ten element członkowski wewnątrz innej klasy (Klasa pochodna).  
  
 Poniższy przykład generuje C2885.  
  
```  
// C2885_b.cpp  
// compile with: /c  
class A {  
public:  
   int i;  
};  
  
void z() {  
   using A::i;   // C2885 not in a class  
}  
  
class B : public A {  
public:  
   using A::i;  
};  
```