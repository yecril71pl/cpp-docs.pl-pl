---
title: C2513 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2513
dev_langs:
- C++
helpviewer_keywords:
- C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 704e5d71301886d46c8a2ce08d7ea34ef1f8275a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2513"></a>C2513 błąd kompilatora
'type': Brak deklaracji zmiennej przed "="  
  
 Specyfikator typu pojawia się w deklaracji z nie zmiennej identyfikatora.  
  
 Poniższy przykład generuje C2513:  
  
```  
// C2513.cpp  
int main() {  
   int = 9;   // C2513  
   int i = 9;   // OK  
}  
```  
  
 Ten błąd może być również generowany w wyniku pracy zgodność kompilatora Visual Studio .NET 2003: inicjowanie jako element typedef nie jest dozwolone. Inicjowanie jako element typedef nie jest dozwolona przez standardowe i generuje błąd kompilatora.  
  
```  
// C2513b.cpp  
// compile with: /c  
typedef struct S {  
   int m_i;  
} S = { 1 };   // C2513  
// try the following line instead  
// } S;  
```  
  
 Alternatywą jest usunąć `typedef` do zdefiniowania zmiennej z listy inicjator agregacji, ale nie jest zalecane, ponieważ utworzy zmienna o takiej samej nazwie jako typ i Ukryj nazwy typu.