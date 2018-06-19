---
title: Kompilatora (poziom 3) ostrzeżenie C4281 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4281
dev_langs:
- C++
helpviewer_keywords:
- C4281
ms.assetid: a9771261-5725-4fc6-87b6-16cf92113a25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5511d82b250ec1e568752bf7bf7993dee003f335
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302451"
---
# <a name="compiler-warning-level-3-c4281"></a>Kompilator C4281 ostrzegawcze (poziom 3)
"operator ->" rekursja wystąpiła za pośrednictwem typu "type"  
  
 Umożliwia kodu **operator ->** aby wywoływać samego siebie.  
  
 Poniższy przykład generuje C4281:  
  
```  
// C4281.cpp  
// compile with: /W3 /WX  
struct A;  
struct B;  
struct C;  
  
struct A  
{  
   int z;  
   B& operator->();  
};  
  
struct B  
{  
   C& operator->();  
};  
  
struct C  
{  
   A& operator->();  
};  
  
void f(A p)  
{  
   int i = p->z; // C4281  
}  
```