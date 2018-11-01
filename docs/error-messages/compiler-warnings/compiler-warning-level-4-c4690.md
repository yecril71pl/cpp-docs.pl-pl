---
title: Kompilator ostrzeżenie (poziom 4) C4690
ms.date: 07/03/2018
f1_keywords:
- C4690
helpviewer_keywords:
- C4690
ms.assetid: 080a0ea1-458b-477b-a37a-4a34c94709ff
ms.openlocfilehash: c7facdde54b44ba2ce07db0447b251d7014f76c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518485"
---
# <a name="compiler-warning-level-4-c4690"></a>Kompilator ostrzeżenie (poziom 4) C4690

> \[ emitidl (pop)]: więcej zdejmowań niż włożeń

## <a name="remarks"></a>Uwagi

[Emitidl](../../windows/emitidl.md) atrybut został zdjęte ze stosu jeszcze raz, że został on wypchnięty.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4690. Aby rozwiązać ten problem, upewnij się, że ten atrybut jest zdejmowany dokładnie dowolną liczbę razy, ile jest on wypchnięty.

```cpp
// C4690.cpp
// compile with: /c /W4
[emitidl(pop)];   // C4690
class x {};
```
