---
title: Kompilator ostrzeżenie (poziom 1) C4224
ms.date: 11/04/2016
f1_keywords:
- C4224
helpviewer_keywords:
- C4224
ms.assetid: 1531cae0-5040-49fd-b149-005bb5085391
ms.openlocfilehash: ed27e6ff63e3d5f3bab4f6d8d9639b84a5606ff2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563946"
---
# <a name="compiler-warning-level-1-c4224"></a>Kompilator ostrzeżenie (poziom 1) C4224

użyto niestandardowego rozszerzenia: parametr formalny "identyfikator" został uprzednio zdefiniowany jako typ

Identyfikator był wcześniej używany jako `typedef`. Powoduje to, że ostrzeżenie w obszarze zgodności ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).

## <a name="example"></a>Przykład

```
// C4224.cpp
// compile with: /Za /W1 /LD
typedef int I;
void func ( int I );  // C4224
```