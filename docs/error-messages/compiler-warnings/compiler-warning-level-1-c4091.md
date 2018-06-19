---
title: Kompilatora (poziom 1) ostrzeżenie C4091 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4091
dev_langs:
- C++
helpviewer_keywords:
- C4091
ms.assetid: 3a404967-ab42-49b0-b324-fd7ba1859d78
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 79a0a74ad2cf6471679fd776f296d465ee8dd29c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276519"
---
# <a name="compiler-warning-level-1-c4091"></a>Kompilator C4091 ostrzegawcze (poziom 1)
"— słowo kluczowe": zignorowano na lewo od "type", gdy brak deklaracji zmiennej  
  
 Kompilator wykryto sytuacji, gdy użytkownik prawdopodobnie przeznaczone można zadeklarować zmiennej, ale kompilator nie może zadeklarować zmienną.  
  
## <a name="example"></a>Przykład  
 A `__declspec` atrybutu na początku deklaracji typu zdefiniowanego przez użytkownika, który ma zastosowanie do zmiennej typu. C4091 wskazuje, że brak deklaracji zmiennej. Poniższy przykład generuje C4091.  
  
```  
// C4091.cpp  
// compile with: /W1 /c  
__declspec(dllimport) class X {}; // C4091  
  
// __declspec attribute applies to varX  
__declspec(dllimport) class X2 {} varX;  
  
// __declspec attribute after the class or struct keyword   
// applies to user defined type  
class __declspec(dllimport) X3 {};  
```  
  
## <a name="example"></a>Przykład  
 Jeśli identyfikator jest typem typedef, nie może być również nazwę zmiennej. Poniższy przykład generuje C4091.  
  
```  
// C4091_b.cpp  
// compile with: /c /W1 /WX  
#define LIST 4  
typedef struct _LIST {} LIST;   // C4091  
```