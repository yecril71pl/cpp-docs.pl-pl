---
title: Błąd kompilatora C2883 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2883
dev_langs:
- C++
helpviewer_keywords:
- C2883
ms.assetid: 5c6d689d-ed42-41ad-b5c0-e9c2e0b8c356
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50cc5b2abb34fae21bea78aa146e74b9aa9491c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019266"
---
# <a name="compiler-error-c2883"></a>Błąd kompilatora C2883

"name": deklaracja funkcji powoduje konflikt z 'Identyfikator' wynikające z deklaracji using

Próbowano zdefiniować funkcję więcej niż jeden raz. Pierwsza definicja została wprowadzona w obszarze nazw o `using` deklaracji. Drugim była lokalnej definicji.

Poniższy przykład spowoduje wygenerowanie C2883:

```
// C2883.cpp
namespace A {
   void z(int);
}

int main() {
   using A::z;
   void z(int);   // C2883  z is already defined
}
```