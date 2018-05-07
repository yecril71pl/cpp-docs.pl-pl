---
title: C2432 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2432
dev_langs:
- C++
helpviewer_keywords:
- C2432
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8dfbadf2c7d53cce799efbd5f10286b31bb3cd3b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2432"></a>C2432 błąd kompilatora
niedozwolone odwołanie do 16-bitowych danych w polu "identyfikator"  
  
 Rejestr 16-bitowy jest używany jako indeksu lub klucza rejestru podstawowej. Kompilator nie obsługuje odwołujące się do 16-bitowych danych. rejestruje 16-bitowych nie można użyć jako indeks lub base rejestrów podczas kompilowania kodu dla kodu 32-bitowego.  
  
 Poniższy przykład generuje C2432:  
  
```  
// C2432.cpp  
// processor: x86  
int main() {  
   _asm mov eax, DWORD PTR [bx]   // C2432  
}  
```