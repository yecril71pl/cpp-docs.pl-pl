---
title: Błąd krytyczny C1103
ms.date: 11/04/2016
f1_keywords:
- C1103
helpviewer_keywords:
- C1103
ms.assetid: 9d276939-9c47-4235-9d20-76b8434f9731
ms.openlocfilehash: b6253af9fcf400321fb58d4d8a6d7aacf461b926
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577648"
---
# <a name="fatal-error-c1103"></a>Błąd krytyczny C1103

krytyczny błąd importu progid: "message"

Kompilator wykrył problem podczas importowania biblioteki typów.  Na przykład nie można określić bibliotekę typów z progid i również określić `no_registry`.

Aby uzyskać więcej informacji, zobacz [#import Directive](../../preprocessor/hash-import-directive-cpp.md).

Poniższy przykład spowoduje wygenerowanie C1103:

```
// C1103.cpp
#import "progid:a.b.id.1.5" no_registry auto_search   // C1103
```