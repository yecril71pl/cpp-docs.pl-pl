---
title: Błąd kompilatora C3283 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3283
dev_langs:
- C++
helpviewer_keywords:
- C3283
ms.assetid: c51d912c-cde3-4928-904e-26734c8954ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0feaad0e0eb1b9dc5ee6c5b2f47e8f2a425b6d99
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096473"
---
# <a name="compiler-error-c3283"></a>Błąd kompilatora C3283

"type": interfejs nie może posiadać konstruktora wystąpień

CLR [interfejsu](../../windows/interface-class-cpp-component-extensions.md) nie może posiadać konstruktora wystąpień.  Statyczny Konstruktor jest dozwolone.

Poniższy przykład spowoduje wygenerowanie C3283:

```
// C3283.cpp
// compile with: /clr
interface class I {
   I();   // C3283
};
```

Możliwe rozwiązanie:

```
// C3283b.cpp
// compile with: /clr /c
interface class I {
   static I(){}
};
```