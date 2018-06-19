---
title: Kompilatora (poziom 1) ostrzeżenie C4405 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4405
dev_langs:
- C++
helpviewer_keywords:
- C4405
ms.assetid: 155c64d6-58ae-4455-b61f-ccd711c5da96
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9971113cc34efc5aa29e4066094517530b186839
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279582"
---
# <a name="compiler-warning-level-1-c4405"></a>Kompilator C4405 ostrzegawcze (poziom 1)
'Identyfikator': identyfikator jest zarezerwowanym słowem  
  
 Słowa zastrzeżone dla zestawu wbudowanego jest używana jako nazwa zmiennej. Może to spowodować nieoczekiwane wyniki. Aby usunąć to ostrzeżenie, należy unikać nazw zmiennych z słowa zastrzeżone dla zestawu wbudowanego. Poniższy przykład generuje C4405:  
  
```  
// C4405.cpp  
// compile with: /W1  
// processor: x86  
void func1() {  
   int mov = 0, i = 0;  
   _asm {  
      mov mov, 0;   // C4405  
      // instead, try ..  
      // mov i, 0;  
   }  
}  
  
int main() {  
}  
```