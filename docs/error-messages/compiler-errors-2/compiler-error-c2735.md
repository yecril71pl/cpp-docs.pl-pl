---
title: Błąd kompilatora C2735
ms.date: 11/04/2016
f1_keywords:
- C2735
helpviewer_keywords:
- C2735
ms.assetid: 6ce45600-7148-4bc0-8699-af0ef137571e
ms.openlocfilehash: 73d5f61b5f86153db74a970d97b4656fb662bdad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152452"
---
# <a name="compiler-error-c2735"></a>Błąd kompilatora C2735

słowo kluczowe "— słowo kluczowe" nie jest dozwolone w specyfikatorze typu formalnego parametru

Słowo kluczowe jest nieprawidłowy w tym kontekście.

Poniższy przykład spowoduje wygenerowanie C2735:

```
// C2735.cpp
void f(inline int){}   // C2735
```