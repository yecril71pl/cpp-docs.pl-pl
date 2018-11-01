---
title: Błąd kompilatora C2790
ms.date: 11/04/2016
f1_keywords:
- C2790
helpviewer_keywords:
- C2790
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
ms.openlocfilehash: e377c18b5c0774a466dc535f2a1fba3411bd15b8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530250"
---
# <a name="compiler-error-c2790"></a>Błąd kompilatora C2790

"super": to słowo kluczowe może być użyte tylko w treści funkcji składowej klasy

Ten komunikat o błędzie jest wyświetlany, jeśli użytkownik nigdy nie próbuje używa słowa kluczowego [super](../../cpp/super.md) poza kontekstem dla funkcji członkowskiej.

Poniższy przykład spowoduje wygenerowanie C2790:

```
// C2790.cpp
void f() {
   __super::g();   // C2790
}
```