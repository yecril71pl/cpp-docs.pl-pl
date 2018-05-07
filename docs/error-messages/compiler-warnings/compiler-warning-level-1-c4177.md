---
title: Kompilatora (poziom 1) ostrzeżenie C4177 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4177
dev_langs:
- C++
helpviewer_keywords:
- C4177
ms.assetid: 2b05a5b3-696e-4f21-818e-227b9335e748
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae001b593d965ead0c834793dbbeee3972a5b0bd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4177"></a>Kompilator C4177 ostrzegawcze (poziom 1)
\#pragma pragma powinien być w zakresie globalnym  
  
 [Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) pragma nie powinny być używane w ramach zakresu lokalnego. **Pragma** nie będzie obowiązywać do momentu globalne napotkano po bieżącym zakresie.  
  
 Poniższy przykład generuje C4177:  
  
```  
// C4177.cpp  
// compile with: /W1  
// #pragma bss_seg("global")   // OK  
  
int main() {  
   #pragma bss_seg("local")    // C4177  
}  
```