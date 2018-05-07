---
title: Kompilatora (poziom 1) ostrzeżenie C4237 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4237
dev_langs:
- C++
helpviewer_keywords:
- C4237
ms.assetid: f2e86c4b-80d8-460e-9429-83c5f3f5d7ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3dfefb2dc7dd04f2334b2b7d222153d5ee351ae2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4237"></a>Kompilator C4237 ostrzegawcze (poziom 1)
słowo kluczowe "— słowo kluczowe" jest nie jest jeszcze obsługiwane, ale zarezerwowane do użytku w przyszłości  
  
 Słowo kluczowe w specyfikacji języka C++ nie jest zaimplementowana w kompilatorze języka Visual C++, ale słowo kluczowe nie jest dostępna symbolu zdefiniowane przez użytkownika.  
  
 Poniższy przykład generuje C4237:  
  
```  
// C4237.cpp  
// compile with: /W1 /c  
int export;   // C4237  
```