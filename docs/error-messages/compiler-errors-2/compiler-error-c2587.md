---
title: Błąd kompilatora C2587 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2587
dev_langs:
- C++
helpviewer_keywords:
- C2587
ms.assetid: 7637a2c7-35d4-4b5a-a8f2-515a7bda98fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4141c101c5b7b2801ccd656964a501f9fa11e3a8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054067"
---
# <a name="compiler-error-c2587"></a>Błąd kompilatora C2587

'Identyfikator': niedozwolone użycie lokalnej zmiennej jako parametru domyślnego

Zmienne lokalne nie są dozwolone jako parametry domyślne.

Poniższy przykład spowoduje wygenerowanie C2587:

```
// C2587.cpp
// compile with: /c
int i;
void func() {
   int j;
   extern void func2( int k = j );  // C2587 -- local variable
   extern void func3( int k = i );   // OK
}
```