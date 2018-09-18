---
title: Błąd krytyczny C1018 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1018
dev_langs:
- C++
helpviewer_keywords:
- C1018
ms.assetid: 2ceb8a99-30b2-4b80-bf42-e9f3305b3c52
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5549cdd40b8287f75f80b0e633ff053a23cdecde
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034450"
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