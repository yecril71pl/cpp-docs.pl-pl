---
title: Błąd krytyczny C1018
ms.date: 11/04/2016
f1_keywords:
- C1018
helpviewer_keywords:
- C1018
ms.assetid: 2ceb8a99-30b2-4b80-bf42-e9f3305b3c52
ms.openlocfilehash: 327bc0d5200fc348611da107257f2086063648fa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532672"
---
# <a name="fatal-error-c1018"></a>Błąd krytyczny C1018

Nieoczekiwany #elif

`#elif` Poza pojawia się dyrektywa `#if`, `#ifdef`, lub `#ifndef` konstruowania. Użyj `#elif` tylko w jednej z tych konstrukcji.

Poniższy przykład spowoduje wygenerowanie C1018:

```
// C1018.cpp
#elif      // C1018
#endif

int main() {}
```

Możliwe rozwiązanie:

```
// C1018b.cpp
#if 1
#elif
#endif

int main() {}
```