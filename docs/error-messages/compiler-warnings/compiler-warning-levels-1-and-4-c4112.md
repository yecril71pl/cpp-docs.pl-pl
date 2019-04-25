---
title: Kompilator ostrzeżenie (poziomy 1 i 4) C4112
ms.date: 11/04/2016
f1_keywords:
- C4112
helpviewer_keywords:
- C4112
ms.assetid: aff64897-bb79-4a67-9b6f-902c6d44f3dc
ms.openlocfilehash: 3678d0ce5d9eb9568f0272da4173e72502b0557f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280337"
---
# <a name="compiler-warning-levels-1-and-4-c4112"></a>Kompilator ostrzeżenie (poziomy 1 i 4) C4112

\#wiersz wymaga całkowitą z zakresu od 1 i numer

[#Line](../../preprocessor/hash-line-directive-c-cpp.md) dyrektywa określa parametru liczby całkowitej, która znajduje się poza dozwolonym zakresem.

Jeśli określony parametr jest mniejsza niż 1, licznik wierszy jest resetowany do 1. Jeśli określony parametr jest większa niż *numer*, czyli limitu zdefiniowanego przez kompilator, licznik wierszy pozostaje niezmieniony. Jest to ostrzeżenia poziomu 1, w obszarze zgodności ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) i ostrzeżenia poziomu 4 z rozszerzeniami firmy Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).

Poniższy przykład spowoduje wygenerowanie C4112:

```
// C4112.cpp
// compile with: /W4
#line 0   // C4112, value must be between 1 and number

int main() {
}
```