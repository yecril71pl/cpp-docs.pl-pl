---
title: Błąd kompilatora C3297
ms.date: 11/04/2016
f1_keywords:
- C3297
helpviewer_keywords:
- C3297
ms.assetid: 2a718b4c-6cdb-4418-92c0-fc3a259431c4
ms.openlocfilehash: 6df8fd3df023602f65c872dedd74da36bbbc6bd8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649920"
---
# <a name="compiler-error-c3297"></a>Błąd kompilatora C3297

"constraint_2": nie można użyć "constraint_1" jako ograniczenie, ponieważ 'constraint_1' posiada wartość ograniczenia

Klasy wartości są zamknięte. Jeśli ograniczenie jest klasą wartości, kolejne ograniczenia może nigdy nie dziedziczyć po nim.

Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu ogólnego (C + +/ CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3297.

```
// C3297.cpp
// compile with: /clr /c
generic<class T, class U>
where T : value class
where U : T   // C3297
public ref struct R {};
```