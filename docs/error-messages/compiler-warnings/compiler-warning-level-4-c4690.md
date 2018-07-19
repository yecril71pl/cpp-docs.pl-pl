---
title: Kompilator ostrzeżenie (poziom 4) C4690 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/03/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4690
dev_langs:
- C++
helpviewer_keywords:
- C4690
ms.assetid: 080a0ea1-458b-477b-a37a-4a34c94709ff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04fb68bdab762f0f541849fad1568caff836b623
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853325"
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
