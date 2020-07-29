---
title: Błąd kompilatora C2714
ms.date: 07/22/2020
f1_keywords:
- C2714
helpviewer_keywords:
- C2714
ms.assetid: 401a5a42-660c-4bad-9d63-1a2d092bc489
ms.openlocfilehash: d3f733f065af5b3217dc19d46b46e504d39151f4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225413"
---
# <a name="compiler-error-c2714"></a>Błąd kompilatora C2714

> `alignof(void)`nie jest dozwolone

Nieprawidłowa wartość została przeniesiona do operatora.

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [ `alignof` operator](../../cpp/alignof-operator.md) .

## <a name="example"></a>Przykład

Poniższy przykład generuje C2714.

```cpp
// C2714.cpp
int main() {
   return alignof(void);   // C2714
   return alignof(char);   // OK
}
```
