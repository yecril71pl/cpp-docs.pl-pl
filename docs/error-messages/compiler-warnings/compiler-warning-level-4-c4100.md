---
title: Kompilatora (poziom 4) ostrzeżenie C4100 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4100
dev_langs:
- C++
helpviewer_keywords:
- C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d3cf831590af2e1f2f7cd13d93c9d13ba217e11
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292808"
---
# <a name="compiler-warning-level-4-c4100"></a>Kompilator C4100 ostrzegawcze (poziom 4)
'Identyfikator': nieużywane parametrów formalnych  
  
 Parametr formalny nie są przywoływane w treści funkcji. Parametr nieużywane jest ignorowany.  
  
 C4100 również mogą być wystawiane, gdy kod wywołuje destruktora w inny sposób których nie ma odwołań parametru typu pierwotnego.  Jest to ograniczenie kompilatora Visual C++.  
  
 Poniższy przykład generuje C4100:  
  
```  
// C4100.cpp  
// compile with: /W4  
void func(int i) {   // C4100, delete the unreferenced parameter to  
                     //resolve the warning  
   // i;   // or, add a reference like this  
}  
  
int main()  
{  
   func(1);  
}  
```