---
title: Błąd kompilatora C2675
ms.date: 11/04/2016
f1_keywords:
- C2675
helpviewer_keywords:
- C2675
ms.assetid: 4b92a12b-bff8-4dd5-a109-620065fc146c
ms.openlocfilehash: 0b7b81ce7314fbad02d6873403fc5cf1bdd54709
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760377"
---
# <a name="compiler-error-c2675"></a>Błąd kompilatora C2675

jednoargumentowy "operator": "Type" nie definiuje tego operatora lub konwersji do typu akceptowalnego dla wstępnie zdefiniowanego operatora

C2675 może również wystąpić podczas używania operatora jednoargumentowego, a typ nie definiuje operatora lub konwersji do typu akceptowalnego dla wstępnie zdefiniowanego operatora. Aby użyć operatora, należy przeciążyć go dla określonego typu lub zdefiniować konwersję do typu, dla którego zdefiniowano operator.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2675.

```cpp
// C2675.cpp
struct C {
   C(){}
} c;

struct D {
   D(){}
   void operator-(){}
} d;

int main() {
   -c;   // C2675
   -d;   // OK
}
```
