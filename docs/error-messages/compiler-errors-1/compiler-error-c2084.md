---
title: "C2084 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2084
dev_langs: C++
helpviewer_keywords: C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cf9e0888e0f959d77198efe036c0234c985ea365
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2084"></a>C2084 błąd kompilatora
Funkcja "*funkcja*" ma już treść  
  
 Funkcja została już zdefiniowana.  
  
 W wersjach programu Visual C++ przed Visual Studio 2002  
  
-   Kompilator będzie akceptować wiele specjalizacji szablonu, których nazwy zostały rozstrzygnięte na ten sam typ rzeczywistego, mimo że dodatkowe definicje nigdy nie będzie dostępna. Kompilator teraz wykrywa te wiele definicji.  
  
-   `__int32`i `int` są traktowane jako osobne typy. Kompilator teraz traktuje `__int32` jako synonimem `int`. Oznacza to, że kompilator wykrywa wiele definicji, jeśli funkcja jest przeciążony zarówno `__int32` i `int` i zwraca błąd.  
  
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