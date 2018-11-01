---
title: Błąd kompilatora C2646
ms.date: 11/04/2016
f1_keywords:
- C2646
helpviewer_keywords:
- C2646
ms.assetid: 92ff1f02-5eaf-40a5-8b7a-a682f149e967
ms.openlocfilehash: c02d7216df42681ae2ec733ae932d22861c1f0ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572011"
---
# <a name="compiler-error-c2646"></a>Błąd kompilatora C2646

anonimowej struktury lub Unii, globalnie lub zakresie przestrzeni nazw musi być zadeklarowane jako statyczne

Anonimowej struktury lub Unii ma globalne lub zakresie przestrzeni nazw ale nie jest zadeklarowana `static`.

Poniższy przykład generuje C2646 i pokazuje, jak go naprawić:

```
// C2646.cpp
// compile with: /c
union { int i; };   // C2646 not static

// OK
static union { int j; };
union U { int i; };
```