---
title: Błąd kompilatora C2372
ms.date: 11/04/2016
f1_keywords:
- C2372
helpviewer_keywords:
- C2372
ms.assetid: 406bea63-c8d3-4231-9d26-c70af6980840
ms.openlocfilehash: db13a6bc108588fbbd9c15e2bcc647bea073a333
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339029"
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