---
title: Błąd kompilatora C2464
ms.date: 11/04/2016
f1_keywords:
- C2464
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
ms.openlocfilehash: a00ac997f73175eeab08a0132128e48e8fc58feb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498192"
---
# <a name="compiler-error-c2464"></a>Błąd kompilatora C2464

'Identyfikator': nie można użyć "new", aby przydzielić odwołanie

Identyfikator odwołania został przydzielony przy użyciu `new` operatora. Odwołania nie są obiekty w pamięci, dlatego `new` nie może zwracać wskaźnik do nich. Należy użyć składni standardowych deklaracja zmiennej do zadeklarowania odwołania.

Poniższy przykład spowoduje wygenerowanie C2464:

```
// C2464.cpp
int main() {
   new ( int& ir );   // C2464
}
```