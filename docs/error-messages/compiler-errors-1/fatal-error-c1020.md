---
title: Błąd krytyczny C1020
ms.date: 11/04/2016
f1_keywords:
- C1020
helpviewer_keywords:
- C1020
ms.assetid: 42f429e2-5e3b-4086-a10d-b99e032e51c5
ms.openlocfilehash: 67cf5067c85d07215f6391d9e5d3d1bcb4978e42
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756906"
---
# <a name="fatal-error-c1020"></a>Błąd krytyczny C1020

nieoczekiwany #endif

Dyrektywa `#endif` nie ma zgodnej dyrektywy `#if`, `#ifdef`lub `#ifndef`. Upewnij się, że każda `#endif` ma pasującą dyrektywę.

Poniższy przykład generuje C1020:

```cpp
// C1020.cpp
#endif     // C1020
```

Możliwe rozwiązanie:

```cpp
// C1020b.cpp
// compile with: /c
#if 1
#endif
```
