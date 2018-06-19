---
title: Kompilatora (poziom 1) ostrzeżenie C4553 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4553
dev_langs:
- C++
helpviewer_keywords:
- C4553
ms.assetid: d8aacbe0-3cb5-4367-a6e5-fd7e28f0ff9d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8633a9cf3eb8f825f1bfd131db6c1dfd2f8d6159
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277884"
---
# <a name="compiler-warning-level-1-c4553"></a>Kompilator C4553 ostrzegawcze (poziom 1)
"operator": operator nie ma żadnego wpływu; Czy planowane "operator"?  
  
 Jeśli Instrukcja wyrażenia operator o nie działa po stronie jak wartość górnej części wyrażenia, prawdopodobnie jest błąd.  
  
 Poniższy przykład generuje C4553:  
  
```  
// C4553.cpp  
// compile with: /W1  
int func()  
{  
   return 0;  
}  
  
int main()  
{  
   int i;  
   i == func();   // C4553  
   // try the following line instead  
   // i = func();  
}  
```