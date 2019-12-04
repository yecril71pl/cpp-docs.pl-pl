---
title: Błąd kompilatora C2632
ms.date: 11/04/2016
f1_keywords:
- C2632
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
ms.openlocfilehash: f69d43bf50f5f13957e49d1e9ffa798a3db5a7b3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754696"
---
# <a name="compiler-error-c2632"></a>Błąd kompilatora C2632

element "type1", po którym następuje wyrażenie "type2", jest niedozwolony

Ten błąd może być spowodowany brakiem kodu między dwoma specyfikatorami typu.

Poniższy przykład generuje C2632:

```cpp
// C2632.cpp
int float i;   // C2632
```

Ten błąd może być również wygenerowany w wyniku działania kompilatora, który został wykonany dla programu Visual Studio .NET 2003. `bool` jest teraz odpowiednim typem. W poprzednich wersjach `bool` była elementem TypeDef i można utworzyć identyfikatory o tej nazwie.

Poniższy przykład generuje C2632:

```cpp
// C2632_2.cpp
// compile with: /LD
void f(int bool);   // C2632
```

Aby rozwiązać ten problem, aby kod był prawidłowy w wersji Visual Studio .NET 2003 i Visual Studio .NET C++, Zmień nazwę identyfikatora.
