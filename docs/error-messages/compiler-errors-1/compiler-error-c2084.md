---
title: C2084 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2084
dev_langs:
- C++
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ce1510dd6e78b8774d3cc433f583c16cdbb8d06
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2084"></a>C2084 błąd kompilatora
Funkcja "*funkcja*" ma już treść  
  
 Funkcja została już zdefiniowana.  
  
 W wersjach programu Visual C++ przed Visual Studio 2002  
  
-   Kompilator będzie akceptować wiele specjalizacji szablonu, których nazwy zostały rozstrzygnięte na ten sam typ rzeczywistego, mimo że dodatkowe definicje nigdy nie będzie dostępna. Kompilator teraz wykrywa te wiele definicji.  
  
-   `__int32` i `int` są traktowane jako osobne typy. Kompilator teraz traktuje `__int32` jako synonimem `int`. Oznacza to, że kompilator wykrywa wiele definicji, jeśli funkcja jest przeciążony zarówno `__int32` i `int` i zwraca błąd.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2084:  
  
```cpp  
// C2084.cpp  
void Func(int);  
void Func(int) {}   // define function  
void Func(int) {}   // C2084 second definition  
```  
  
Aby rozwiązać ten problem, Usuń zduplikowane definicję:  
  
```  
// C2084b.cpp  
// compile with: /c  
void Func(int);  
void Func(int) {}  
```