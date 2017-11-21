---
title: "C2431 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2431
dev_langs: C++
helpviewer_keywords: C2431
ms.assetid: 88a5b648-c89f-47d1-a20e-63231ab4f0f7
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3db0777c8ac330db747e3376328fe87119407568
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2431"></a>C2431 błąd kompilatora
Niedozwolony indeks rejestru w "identyfikator"  
  
 Rejestr ESP jest skalowana lub używana jako indeks i rejestr podstawowego. RODZEŃSTWA, kodowanie x86 nie zezwala na jeden procesor.  
  
 Poniższy przykład generuje C2431:  
  
```  
// C2431.cpp  
// processor: x86  
int main() {  
   _asm mov ax, [ESI + 2*ESP]   // C2431  
   _asm mov ax, [esp + esp]   // C2431  
}  
```