---
title: Błąd kompilatora C2014
ms.date: 11/04/2016
f1_keywords:
- C2014
helpviewer_keywords:
- C2014
ms.assetid: 231d8e9c-48c0-4027-99a3-245d186275ec
ms.openlocfilehash: 58cf9867a9e36b304ab9da79084bc01dff453892
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462663"
---
# <a name="compiler-error-c2014"></a>Błąd kompilatora C2014

polecenie preprocesora musi zaczynać się niebiałym

`#` Logowania dyrektywy preprocesora musi być pierwszym znakiem w wierszu, który nie jest biały znak.

Poniższy przykład spowoduje wygenerowanie C2014:

```
// C2014.cpp
int k; #include <stdio.h>   // C2014
```

Możliwe rozwiązanie:

```
// C2014b.cpp
// compile with: /c
int k;
#include <stdio.h>
```