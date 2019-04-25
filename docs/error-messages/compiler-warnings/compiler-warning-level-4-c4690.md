---
title: Kompilator ostrzeżenie (poziom 4) C4690
ms.date: 07/03/2018
f1_keywords:
- C4690
helpviewer_keywords:
- C4690
ms.assetid: 080a0ea1-458b-477b-a37a-4a34c94709ff
ms.openlocfilehash: c7facdde54b44ba2ce07db0447b251d7014f76c8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324587"
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
