---
title: Ostrzeżenie kompilatora (poziom 4) C4690
ms.date: 07/03/2018
f1_keywords:
- C4690
helpviewer_keywords:
- C4690
ms.assetid: 080a0ea1-458b-477b-a37a-4a34c94709ff
ms.openlocfilehash: de996128c68ebf96b4a00f6206cbaf54d97ca275
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509963"
---
# <a name="compiler-warning-level-4-c4690"></a>Ostrzeżenie kompilatora (poziom 4) C4690

> \[ emitidl (pop)]: więcej punktów obecności niż wypychanie

## <a name="remarks"></a>Uwagi

Atrybut [emitidl](../../windows/attributes/emitidl.md) został zdjęte jeszcze raz na wypchnięcie.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4690. Aby rozwiązać ten problem, upewnij się, że atrybut jest zdjęte dokładnie tyle razy, ile jest wypchnięci.

```cpp
// C4690.cpp
// compile with: /c /W4
[emitidl(pop)];   // C4690
class x {};
```
