---
title: Błąd kompilatora C2289
ms.date: 11/04/2016
f1_keywords:
- C2289
helpviewer_keywords:
- C2289
ms.assetid: cb41a29e-1b06-47dc-bfce-8d73bd63a0df
ms.openlocfilehash: 9fe9b765af72a8864e3e899cafcf648a9facb67e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528131"
---
# <a name="compiler-error-c2289"></a>Błąd kompilatora C2289

tym samym kwalifikator typu użyty więcej niż raz

Typ deklaracji lub definicji używa kwalifikator typu (`const`, `volatile`, `signed`, lub `unsigned`) więcej niż raz, co powoduje wystąpienie błędu w obszarze zgodności ANSI (**/Za**).

Poniższy przykład spowoduje wygenerowanie C2286:

```
// C2289.cpp
// compile with: /Za /c
volatile volatile int i;   // C2289
volatile int j;   // OK
```