---
title: Kompilator ostrzeżenie (poziom 1) C4369
ms.date: 11/04/2016
f1_keywords:
- C4369
helpviewer_keywords:
- C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
ms.openlocfilehash: b374b67fa3319be35490358d7664bcb45bc640db
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623958"
---
# <a name="compiler-warning-level-1-c4369"></a>Kompilator ostrzeżenie (poziom 1) C4369

'moduł wyliczający': moduł wyliczający wartość "value" nie może być reprezentowana "type", wartość to "nowa_wartość"

Moduł wyliczający został obliczony powinien być większy niż największa wartość dla określonego typu bazowego.  To spowodowało przepełnienie i kompilator opakowane wartość modułu wyliczającego do najmniejszej możliwej wartości dla typu.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4369.

```
// C4369.cpp
// compile with: /W1
int main() {
   enum Color: char { red = 0x7e, green, blue };   // C4369
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK
}
```