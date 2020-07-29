---
title: Błąd kompilatora C2638
ms.date: 11/04/2016
f1_keywords:
- C2638
helpviewer_keywords:
- C2638
ms.assetid: 9d4275e8-406d-455e-afee-3a37799230e0
ms.openlocfilehash: 863537c60584ba836c6605f31249ada95a88a1bf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212699"
---
# <a name="compiler-error-c2638"></a>Błąd kompilatora C2638

"Identyfikator": modyfikator __based niedozwolony dla wskaźnika do składowej

**`__based`** Modyfikator nie może być używany dla wskaźników do elementów członkowskich.

Poniższy przykład generuje C2638:

```cpp
// C2638.cpp
void *a;

class C {
public:
   int i;
   int j;
   int func();
};
int __based (a) C::* cpi = &C::i;  // C2638
int (__based (a) C::* cpf)() = &C::func; // c2638
```
