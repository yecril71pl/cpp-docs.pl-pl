---
title: Błąd kompilatora C2199
ms.date: 11/04/2016
f1_keywords:
- C2199
helpviewer_keywords:
- C2199
ms.assetid: 6a92a1b7-7906-49e6-a31f-e8bffbc7706a
ms.openlocfilehash: e5892a537cbf337b23ff2356583cec4bf5925677
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530979"
---
# <a name="compiler-error-c2199"></a>Błąd kompilatora C2199

Błąd składniowy: znaleziono "identyfikator (" w zakresie globalnym (była deklaracja jest zamierzona?)

Określony kontekst spowodował błąd składni. Może to być Składnia deklaracji niepoprawne.

Poniższy przykład spowoduje wygenerowanie C2199:

```
// C2199.cpp
// compile with: /c
int j = int(1) int(1);   // C2199
int j = 1;   // OK
```