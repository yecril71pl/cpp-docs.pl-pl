---
title: Błąd krytyczny C1018
ms.date: 11/04/2016
f1_keywords:
- C1018
helpviewer_keywords:
- C1018
ms.assetid: 2ceb8a99-30b2-4b80-bf42-e9f3305b3c52
ms.openlocfilehash: 327bc0d5200fc348611da107257f2086063648fa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383220"
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