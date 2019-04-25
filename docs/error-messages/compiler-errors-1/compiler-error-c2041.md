---
title: Błąd kompilatora C2041
ms.date: 11/04/2016
f1_keywords:
- C2041
helpviewer_keywords:
- C2041
ms.assetid: c9a33bb1-f9cf-47d6-bd21-7d867a8c37d5
ms.openlocfilehash: 37d32285f9c01efb981c5f02acba21f2d6fe3dc2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165673"
---
# <a name="compiler-error-c2041"></a>Błąd kompilatora C2041

niedozwolony znak "character" dla podstawowego numeru

Określony znak nie jest prawidłową cyfrą dla podstawowego (na przykład ósemkowa i szesnastkowa).

Poniższy przykład spowoduje wygenerowanie C2041:

```
// C2041.cpp
int i = 081;   // C2041  8 is not a base 8 digit
```

Możliwe rozwiązanie:

```
// C2041b.cpp
// compile with: /c
int j = 071;
```