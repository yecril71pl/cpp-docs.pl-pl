---
title: Błąd kompilatora C2014
ms.date: 11/04/2016
f1_keywords:
- C2014
helpviewer_keywords:
- C2014
ms.assetid: 231d8e9c-48c0-4027-99a3-245d186275ec
ms.openlocfilehash: 6c7e941970415c933b38f35b6c09247a3c0fd411
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757400"
---
# <a name="compiler-error-c2014"></a>Błąd kompilatora C2014

polecenie preprocesora musi zaczynać się od pierwszego niebiałego znaku

Znak `#` dyrektywy preprocesora musi być pierwszym znakiem w wierszu, który nie jest znakiem odstępu.

Poniższy przykład generuje C2014:

```cpp
// C2014.cpp
int k; #include <stdio.h>   // C2014
```

Możliwe rozwiązanie:

```cpp
// C2014b.cpp
// compile with: /c
int k;
#include <stdio.h>
```
