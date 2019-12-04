---
title: Błąd kompilatora C2628
ms.date: 11/04/2016
f1_keywords:
- C2628
helpviewer_keywords:
- C2628
ms.assetid: 19a25e77-d5be-4107-88d5-0745b6281f98
ms.openlocfilehash: 4198d6ff0552f5280904ed1fea5e185df1a9c804
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754722"
---
# <a name="compiler-error-c2628"></a>Błąd kompilatora C2628

"type1", po którym następuje wyrażenie "type2", jest niedozwolone (Czy pamiętasz ";"?)

Może brakować średnika.

Poniższy przykład generuje C2628:

```cpp
// C2628.cpp
class CMyClass {}
int main(){}   // C2628 error
```

Możliwe rozwiązanie:

```cpp
// C2628b.cpp
class CMyClass {};
int main(){}
```
