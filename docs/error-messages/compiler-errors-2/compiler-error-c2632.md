---
title: Błąd kompilatora C2632
ms.date: 11/04/2016
f1_keywords:
- C2632
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
ms.openlocfilehash: b92d44bcfd04d4de7b39c5bdab5ee146d9b6693b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257637"
---
# <a name="compiler-error-c2632"></a>Błąd kompilatora C2632

'Typ1', po której następuje 'Typ2' jest niedozwolony

Ten błąd może być spowodowany, jeśli brak kodu między dwoma specyfikatory typu.

Poniższy przykład spowoduje wygenerowanie C2632:

```
// C2632.cpp
int float i;   // C2632
```

Ten błąd można wygenerować w taki sposób, w wyniku pracy zgodności kompilatora, która została wykonana dla Visual Studio .NET 2003. `bool` jest teraz odpowiedniego typu. W poprzednich wersjach `bool` został element typedef i identyfikatory można utworzyć przy użyciu tej nazwy.

Poniższy przykład spowoduje wygenerowanie C2632:

```
// C2632_2.cpp
// compile with: /LD
void f(int bool);   // C2632
```

Aby rozwiązać ten problem, tak aby dany kod jest prawidłowy w wersjach Visual Studio .NET 2003 i Visual Studio .NET, Visual c++, zmień identyfikator.