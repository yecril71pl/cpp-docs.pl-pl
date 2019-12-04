---
title: Błąd kompilatora C2019
ms.date: 11/04/2016
f1_keywords:
- C2019
helpviewer_keywords:
- C2019
ms.assetid: 4f37b1e1-9eca-418f-a4c3-141e8512d7b6
ms.openlocfilehash: 5343d6760a7a7f2c868d92790bf9930e431e3517
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757517"
---
# <a name="compiler-error-c2019"></a>Błąd kompilatora C2019

Oczekiwano dyrektywy preprocesora, znaleziono "Character"

Znak ma `#` znak, ale nie jest to pierwsza litera dyrektywy preprocesora.

Poniższy przykład generuje C2019:

```cpp
// C2019.cpp
#!define TRUE 1   // C2019
```

Możliwe rozwiązanie:

```cpp
// C2019b.cpp
// compile with: /c
#define TRUE 1
```
