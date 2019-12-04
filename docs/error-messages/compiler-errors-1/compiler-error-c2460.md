---
title: Błąd kompilatora C2460
ms.date: 11/04/2016
f1_keywords:
- C2460
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
ms.openlocfilehash: a7d20a7658a75a492e19b9e81acaa3b6fce5cae7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743942"
---
# <a name="compiler-error-c2460"></a>Błąd kompilatora C2460

"Identifier1": używa "identifier2", który jest definiowany

Klasa lub struktura (`identifier2`) jest zadeklarowana jako element członkowski samego siebie (`identifier1`). Definicje cykliczne klas i struktur są niedozwolone.

Poniższy przykład generuje C2460:

```cpp
// C2460.cpp
class C {
   C aC;    // C2460
};
```

Zamiast tego należy użyć odwołania do wskaźnika w klasie.

```cpp
// C2460.cpp
class C {
   C * aC;    // OK
};
```
