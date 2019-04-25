---
title: Błąd kompilatora C2790
ms.date: 11/04/2016
f1_keywords:
- C2790
helpviewer_keywords:
- C2790
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
ms.openlocfilehash: e377c18b5c0774a466dc535f2a1fba3411bd15b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257130"
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