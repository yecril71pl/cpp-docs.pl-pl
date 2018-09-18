---
title: Błąd kompilatora C2632 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2632
dev_langs:
- C++
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7bf03c35c60bebb52c94ed04cca2349f35c06fbc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093653"
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