---
title: Błąd krytyczny C1022
ms.date: 11/04/2016
f1_keywords:
- C1022
helpviewer_keywords:
- C1022
ms.assetid: edada720-dc73-49bc-bd93-a7945a316312
ms.openlocfilehash: 044ebbbe895677acf74977e56879c292486e18cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383142"
---
# <a name="fatal-error-c1022"></a>Błąd krytyczny C1022

Oczekiwano #endif

`#if`, `#ifdef`, Lub `#ifndef` dyrektywy nie ma odpowiadającego `#endif` dyrektywy. Można się, że każdy `#if`, `#ifdef`, lub `#ifndef` miała zgodną `#endif`.

Poniższy przykład spowoduje wygenerowanie C1022:

```
// C1022.cpp
#define true 1

#if (true)
#else
#else    // C1022
```

Możliwe rozwiązanie:

```
// C1022b.cpp
// compile with: /c
#define true 1

#if (true)
#else
#endif
```