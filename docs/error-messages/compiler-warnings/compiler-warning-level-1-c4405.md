---
title: "Kompilatora (poziom 1) ostrzeżenie C4405 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4405
dev_langs: C++
helpviewer_keywords: C4405
ms.assetid: 155c64d6-58ae-4455-b61f-ccd711c5da96
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2301c85eeb91ece43cec75e4cbb2a451c27a0c8d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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