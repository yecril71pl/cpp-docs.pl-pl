---
title: Kompilatora (poziom 4) ostrzeżenie C4239 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4239
dev_langs:
- C++
helpviewer_keywords:
- C4239
ms.assetid: a23dc16a-649e-4870-9a24-275de1584fcd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d756bba65100d3e5c2987527d7a0dd4cc3fdc050
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4239"></a>Kompilator C4239 ostrzegawcze (poziom 4)
użyto niestandardowego rozszerzenia: "token": konwersja z "type" na "type"  
  
 Ta konwersja typu nie jest dozwolona przez C++ standard, ale jest dozwolone jako rozszerzenie. To ostrzeżenie jest zawsze następuje co najmniej jeden wiersz wyjaśnienie opisujące trwa naruszenie reguły języka.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4239.  
  
```  
// C4239.cpp  
// compile with: /W4 /c  
struct C {  
   C() {}  
};  
  
void func(void) {  
   C & rC = C();   // C4239  
   const C & rC2 = C();   // OK  
   rC2;  
}  
```  
  
## <a name="example"></a>Przykład  
 Konwersja z typu całkowitego na typ wyliczeniowy nie jest ściśle dozwolona.  
  
 Poniższy przykład generuje C4239.  
  
```  
// C4239b.cpp  
// compile with: /W4 /c  
enum E { value };   
struct S {   
   E e : 2;   
} s = { 5 };   // C4239   
// try the following line instead  
// } s = { (E)5 };  
```