---
title: Błąd kompilatora C2612
ms.date: 11/04/2016
f1_keywords:
- C2612
helpviewer_keywords:
- C2612
ms.assetid: 6faacfd6-4455-41a2-808e-0f6799f84d6d
ms.openlocfilehash: b2d4888c1be39c4f48f0ca674426c7af612b9bb7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612163"
---
# <a name="compiler-error-c2612"></a>Błąd kompilatora C2612

końcowe "char" niedozwolony na liście inicjatora bazowych/składowych

Znak pojawia się po ostatnim podstawowy lub element członkowski na liście inicjatora.

Poniższy przykład spowoduje wygenerowanie C2612:

```
// C2612.cpp
class A {
public:
   int i;
   A( int ia ) : i( ia ) + {};   // C2612
};
```