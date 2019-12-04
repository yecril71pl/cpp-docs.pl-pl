---
title: Błąd kompilatora C2390
ms.date: 11/04/2016
f1_keywords:
- C2390
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
ms.openlocfilehash: 515e2e151d27dd2eb84fc1dc71b9197b36b14cbb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745047"
---
# <a name="compiler-error-c2390"></a>Błąd kompilatora C2390

"Identyfikator": nieprawidłowa specyfikator klasy magazynu "

Klasa magazynu nie jest prawidłowa dla identyfikatora zakresu globalnego. Domyślna Klasa magazynu jest używana zamiast nieprawidłowej klasy.

Możliwe rozwiązania:

- Jeśli identyfikator jest funkcją, zadeklaruj ją z magazynem `extern`.

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
