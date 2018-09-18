---
title: Kompilator ostrzeżenie (poziomy 1 i 4) C4112 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4112
dev_langs:
- C++
helpviewer_keywords:
- C4112
ms.assetid: aff64897-bb79-4a67-9b6f-902c6d44f3dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9015a7ee7a0b71d3c6aafd3e3b32d4ea1b07f108
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110552"
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