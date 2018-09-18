---
title: Błąd kompilatora C2594 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2594
dev_langs:
- C++
helpviewer_keywords:
- C2594
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9be22544930bb94c36ec5906cbf60d5caac143fe
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058019"
---
# <a name="compiler-error-c2594"></a>Błąd kompilatora C2594

'operator': Niejednoznaczne konwersje z 'Typ1' na 'type2'

Brak konwersji z *type1* do *type2* był bardziej bezpośrednie niż inne. Sugerujemy dwa możliwe rozwiązania do konwertowania z *type1* do *type2*. Pierwsza opcja jest zdefiniowanie to bezpośrednia konwersji z *type1* do *type2*, i drugą opcją jest określić kombinację konwersje z *type1* do  *type2*.

Poniższy przykład spowoduje wygenerowanie C2594. Sugerowane rozwiązanie błędu jest sekwencją konwersje:

```
// C2594.cpp
// compile with: /c
struct A{};
struct I1 : A {};
struct I2 : A {};
struct D : I1, I2 {};

A *f (D *p) {
   return (A*) (p);    // C2594

// try the following line instead
// return static_cast<A *>(static_cast<I1 *>(p));
}
```