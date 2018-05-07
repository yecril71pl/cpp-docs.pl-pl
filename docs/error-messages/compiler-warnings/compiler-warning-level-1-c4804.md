---
title: Kompilatora (poziom 1) ostrzeżenie C4804 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4804
dev_langs:
- C++
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 677899230b2475c80f9bdd461a0c79740c4d3bec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4804"></a>Kompilator C4804 ostrzegawcze (poziom 1)
"operacji": niebezpieczne użycie typu "bool" w operacji  
  
 To ostrzeżenie jest dla przypadku użycia `bool` zmiennej lub wartość w nieoczekiwany sposób. Na przykład C4804 jest generowany, gdy używasz operatorów, takich jak operator jednoargumentowy ujemna (**-**) lub operator dopełnienia jednostkowego (`~`). Kompilator oblicza wyrażenie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4804:  
  
```  
// C4804.cpp  
// compile with: /W1  
  
int main()  
{  
   bool i = true;  
   if (-i)   // C4804, remove the '-' to resolve  
   {  
      i = false;  
   }  
}  
```