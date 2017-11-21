---
title: "C2071 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2071
dev_langs: C++
helpviewer_keywords: C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c62bb735a84b04bfb0c1addd5e3dd20a48a3eb33
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2071"></a>C2071 błąd kompilatora
"identyfikator": niedozwolona Klasa magazynu  
  
 `identifier`została zadeklarowana z nieprawidłową [Klasa magazynu](../../c-language/c-storage-classes.md). Ten błąd może być spowodowany, gdy określono więcej niż jedną klasę magazynu dla identyfikatora lub definicji jest niezgodny z deklaracją klasy magazynu.  
  
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