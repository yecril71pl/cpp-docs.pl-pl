---
title: Błąd kompilatora C2464 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2464
dev_langs:
- C++
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff74085364d6638772ab2376aace93fea741056b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103148"
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