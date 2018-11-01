---
title: Błąd kompilatora C2372
ms.date: 11/04/2016
f1_keywords:
- C2372
helpviewer_keywords:
- C2372
ms.assetid: 406bea63-c8d3-4231-9d26-c70af6980840
ms.openlocfilehash: db13a6bc108588fbbd9c15e2bcc647bea073a333
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603466"
---
# <a name="compiler-error-c2372"></a>Błąd kompilatora C2372

'Identyfikator': zmiana definicji; różne typy pośredniego wywołania

Identyfikator jest już zdefiniowany przy użyciu innego typu pochodnego.

Poniższy przykład spowoduje wygenerowanie C2326:

```
// C2372.cpp
// compile with: /c
extern int *fp;
extern int fp[];   // C2372
extern int fp2[];   // OK
```