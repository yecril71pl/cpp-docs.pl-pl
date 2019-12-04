---
title: Błąd krytyczny C1022
ms.date: 11/04/2016
f1_keywords:
- C1022
helpviewer_keywords:
- C1022
ms.assetid: edada720-dc73-49bc-bd93-a7945a316312
ms.openlocfilehash: b709d4bd855e38cb3721dec6d09b95ed02454def
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756880"
---
# <a name="fatal-error-c1022"></a>Błąd krytyczny C1022

oczekiwane #endif

Dyrektywa `#if`, `#ifdef`lub `#ifndef` nie ma zgodnej dyrektywy `#endif`. Upewnij się, że każda `#if`, `#ifdef`lub `#ifndef` ma pasujące `#endif`.

Poniższy przykład generuje C1022:

```cpp
// C1022.cpp
#define true 1

#if (true)
#else
#else    // C1022
```

Możliwe rozwiązanie:

```cpp
// C1022b.cpp
// compile with: /c
#define true 1

#if (true)
#else
#endif
```
