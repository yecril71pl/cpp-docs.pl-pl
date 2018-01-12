---
title: "Kompilatora (poziom 4) ostrzeżenie C4100 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4100
dev_langs: C++
helpviewer_keywords: C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 72236ee0c100388906689121a0936daf23c58e89
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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