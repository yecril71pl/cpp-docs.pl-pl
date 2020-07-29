---
title: Błąd kompilatora C2390
ms.date: 11/04/2016
f1_keywords:
- C2390
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
ms.openlocfilehash: 48012c0fe31b2017cad29cc98992c9b1121efa7c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221188"
---
# <a name="compiler-error-c2390"></a>Błąd kompilatora C2390

"Identyfikator": nieprawidłowa specyfikator klasy magazynu "

Klasa magazynu nie jest prawidłowa dla identyfikatora zakresu globalnego. Domyślna Klasa magazynu jest używana zamiast nieprawidłowej klasy.

Możliwe rozwiązania:

- Jeśli identyfikator jest funkcją, zadeklaruj ją z **`extern`** magazynem.

- Jeśli identyfikator jest parametrem formalnym lub zmienną lokalną, zadeklaruj go za pomocą automagazynu.

- Jeśli identyfikator jest zmienną globalną, zadeklaruj ją bez klasy magazynu (autostorage).

## <a name="example"></a>Przykład

- Poniższy przykład generuje C2390:

```cpp
// C2390.cpp
register int i;   // C2390

int main() {
   register int j;   // OK
}
```
