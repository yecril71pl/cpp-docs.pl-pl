---
title: C2467 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2467
dev_langs:
- C++
helpviewer_keywords:
- C2467
ms.assetid: f9ead270-5d0b-41cc-bdcd-586a647c67a7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ed9b1b50c63852ed830c2072d7cd8fce668a671
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2467"></a>C2467 błąd kompilatora
Niedozwolona deklaracja "użytkownik zdefiniowany typu anonimowego"  
  
 Zdefiniowane przez użytkownika typu zagnieżdżonego została zadeklarowana. Jest to błąd podczas kompilowania kodu źródłowego C z opcją zgodność ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) włączone.  
  
 Poniższy przykład generuje C2467:  
  
```  
//C2467.c  
// compile with: /Za   
int main() {  
   struct X {  
      union { int i; };   // C2467, nested declaration  
   };  
}  
```