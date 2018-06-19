---
title: C2071 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2071
dev_langs:
- C++
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: faee56023d14e9b010d1c691af654ffcbc31dc78
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169208"
---
# <a name="compiler-error-c2071"></a>C2071 błąd kompilatora
"identyfikator": niedozwolona Klasa magazynu  
  
 `identifier` została zadeklarowana z nieprawidłową [Klasa magazynu](../../c-language/c-storage-classes.md). Ten błąd może być spowodowany, gdy określono więcej niż jedną klasę magazynu dla identyfikatora lub definicji jest niezgodny z deklaracją klasy magazynu.  
  
 Aby rozwiązać ten problem, należy zrozumieć klasy magazynu zamierzone identyfikatora — na przykład `static` lub `extern`— i popraw deklarację do dopasowania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2071.  
  
```  
// C2071.cpp  
// compile with: /c  
struct C {  
   extern int i;   // C2071  
};  
struct D {  
   int i;   // OK, no extern on an automatic  
};  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2071.  
  
```  
// C2071_b.cpp  
// compile with: /c  
typedef int x(int i) { return i; }   // C2071  
typedef int (x)(int);   // OK, no local definition in typedef  
```