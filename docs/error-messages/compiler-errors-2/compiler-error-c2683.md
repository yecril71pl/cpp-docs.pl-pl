---
title: Błąd kompilatora C2683
ms.date: 11/04/2016
f1_keywords:
- C2683
helpviewer_keywords:
- C2683
ms.assetid: db605e4f-601b-4d05-92a1-c43ca24de08d
ms.openlocfilehash: 49e4897ad5db866aa1ca42589859bedff12718df
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266871"
---
# <a name="compiler-error-c2683"></a>Błąd kompilatora C2683

Instrukcja "cast": "type" nie jest typem polimorficznym

Nie można użyć [dynamic_cast](../../cpp/dynamic-cast-operator.md) do konwersji z klasą polimorficzny (klasa żadnych funkcji wirtualnych).

Możesz użyć [static_cast](../../cpp/static-cast-operator.md) do wykonywania konwersji-polimorficzne typy. Jednak `static_cast` nie wykonuje sprawdzanie w czasie wykonania.

Poniższy przykład spowoduje wygenerowanie C2683:

```
// C2683.cpp
// compile with: /c
class B { };
class D : public B { };

void f(B* pb) {
   D* pd1 = dynamic_cast<D*>(pb);  // C2683
   D* pd1 = static_cast<D*>(pb);   // OK
}
```