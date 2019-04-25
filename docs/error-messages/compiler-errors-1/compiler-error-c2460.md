---
title: Błąd kompilatora C2460
ms.date: 11/04/2016
f1_keywords:
- C2460
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
ms.openlocfilehash: 414b6e53cf1610a55db984a1127bfc884102494f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230324"
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