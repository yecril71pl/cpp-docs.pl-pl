---
title: Błąd kompilatora C2460 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2460
dev_langs:
- C++
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb2d85ffbc7aa799f0688fbb10021a04ef9455ad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022624"
---
# <a name="compiler-error-c2460"></a>Błąd kompilatora C2460

"identifier1": używa "identifier2", który jest definiowany

Klasa lub Struktura (`identifier2`) jest zadeklarowany jako członka niej samej (`identifier1`). Cykliczne definicje klas i struktur są niedozwolone.

Poniższy przykład spowoduje wygenerowanie C2460:

```
// C2460.cpp
class C {
   C aC;    // C2460
};
```

Zamiast tego należy użyć odwołanie wskaźnika w klasie.

```
// C2460.cpp
class C {
   C * aC;    // OK
};
```