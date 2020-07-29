---
title: Błąd kompilatora C2632
ms.date: 11/04/2016
f1_keywords:
- C2632
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
ms.openlocfilehash: 8ea3a106e8819bf067203f220ca51e17b87bfe46
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225465"
---
# <a name="compiler-error-c2632"></a>Błąd kompilatora C2632

element "type1", po którym następuje wyrażenie "type2", jest niedozwolony

Ten błąd może być spowodowany brakiem kodu między dwoma specyfikatorami typu.

Poniższy przykład generuje C2632:

```cpp
// C2632.cpp
int float i;   // C2632
```

Ten błąd może być również wygenerowany w wyniku działania kompilatora, który został wykonany dla programu Visual Studio .NET 2003. **`bool`** jest teraz prawidłowym typem. W poprzednich wersjach **`bool`** była elementem TypeDef i można utworzyć identyfikatory o tej nazwie.

Poniższy przykład generuje C2632:

```cpp
// C2632_2.cpp
// compile with: /LD
void f(int bool);   // C2632
```

Aby rozwiązać ten problem, aby kod był prawidłowy w wersjach programu Visual Studio .NET 2003 i Visual Studio .NET Visual C++, Zmień nazwę identyfikatora.
