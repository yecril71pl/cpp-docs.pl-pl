---
title: Błąd kompilatora C2675
ms.date: 11/04/2016
f1_keywords:
- C2675
helpviewer_keywords:
- C2675
ms.assetid: 4b92a12b-bff8-4dd5-a109-620065fc146c
ms.openlocfilehash: aea79509d0e1ae5c31fcf0cf369c28af39a21154
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367931"
---
# <a name="compiler-error-c2675"></a>Błąd kompilatora C2675

Jednoargumentowy "operator": "type" nie definiuje tego operatora lub konwersji do typu akceptowalnego dla wstępnie zdefiniowanego operatora

C2675 może również wystąpić, gdy za pomocą operatora jednoargumentowego, a typ nie posiada zdefiniowanego operatora lub konwersji do typu akceptowalnego dla wstępnie zdefiniowanego operatora. Użycie operatora, możesz go przeciążenia dla określonego typu lub zdefiniuj konwersji na typ, dla którego zdefiniowano operator.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2675.

```
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