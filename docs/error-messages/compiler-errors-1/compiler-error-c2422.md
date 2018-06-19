---
title: C2422 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2422
dev_langs:
- C++
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89a808e4b324b11c88be38ae7d8815bee4e232cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33196350"
---
# <a name="compiler-error-c2422"></a>C2422 błąd kompilatora
niedozwolone przesłonięcie segmentu w "argument operacji"  
  
 Kod zestawu wbudowanego niepoprawnie użyto operatora zastąpienie segmentu (dwukropek) dla argumentu operacji.  Możliwe przyczyny:  
  
-   Rejestr poprzedzających operator nie jest rejestr segmentu.  
  
-   Rejestr poprzedzających operator nie jest tylko rejestr segmentu w argument.  
  
-   Operator zastąpienie segmentu pojawia się w obrębie operator pośredni (nawiasy kwadratowe).  
  
-   Wyrażenie po operatorze zastąpienie segmentu nie jest natychmiastowe argument lub argument pamięci.  
  
 Poniższy przykład generuje C2422:  
  
```  
// C2422.cpp  
// processor: x86  
int main() {  
   _asm {  
      mov AX, [BX:ES]   // C2422  
      mov AX, ES   // OK  
   }  
}  
```