---
title: Błąd krytyczny C1022 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1022
dev_langs:
- C++
helpviewer_keywords:
- C1022
ms.assetid: edada720-dc73-49bc-bd93-a7945a316312
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4ddeea660515ea0a71e4807a34d2172413796046
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036738"
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