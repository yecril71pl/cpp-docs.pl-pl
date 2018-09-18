---
title: Błąd kompilatora C3116 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3116
dev_langs:
- C++
helpviewer_keywords:
- C3116
ms.assetid: 597463e1-a5cc-4ed3-a917-eae9a61d3312
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1104b731fa565991615eb88cc34fa946e2bfb505
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077852"
---
# <a name="compiler-error-c3116"></a>Błąd kompilatora C3116

"specyfikatora magazynu": nieprawidłowa klasa magazynu dla metody interfejsu

Użyte `typedef`, `register`, lub `static` jako klasa magazynu dla metody interfejsu. Te klasy magazynu nie są dozwolone w składowych interfejsu.

Poniższy przykład spowoduje wygenerowanie C3116:

```
// C3116.cpp
__interface ImyInterface
{
   static void myFunc();   // C3116
};
```