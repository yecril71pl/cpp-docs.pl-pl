---
title: Błąd kompilatora C2464
ms.date: 11/04/2016
f1_keywords:
- C2464
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
ms.openlocfilehash: a00ac997f73175eeab08a0132128e48e8fc58feb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338899"
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