---
title: Kompilatora (poziom 3) ostrzeżenie C4636 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4636
dev_langs:
- C++
helpviewer_keywords:
- C4636
ms.assetid: 59112a0f-850f-41c6-bd84-8ae8dc84706a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c48c7d93846d4c313fa3a09c22e009f31bdd2224
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4636"></a>Kompilator C4636 ostrzegawcze (poziom 3)
Zastosowane do "konstruowania" komentarz dokumentu XML: tag wymaga niepustym "atrybutu.  
  
 A tagów, takich jak `cref`, nie ma wartości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4636.  
  
```  
// C4636.cpp  
// compile with: /clr /doc /W3 /c  
/// <see cref=''/>  
// /// <see cref='System::Exception'/>  
ref struct A {   // C4636  
   void f(int);  
};  
  
// OK  
/// <see cref='System::Exception'/>  
ref struct B {  
   void f(int);  
};  
```