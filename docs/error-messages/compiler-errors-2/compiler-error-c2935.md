---
title: Błąd kompilatora C2935
ms.date: 11/04/2016
f1_keywords:
- C2935
helpviewer_keywords:
- C2935
ms.assetid: e11ef90d-0756-4e43-8a09-4974c6aa72a3
ms.openlocfilehash: 676c238dfb0ae78dbe5b144b5242bfb4ccbda76c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756152"
---
# <a name="compiler-error-c2935"></a>Błąd kompilatora C2935

"Class": Identyfikator klasy typu został ponownie zdefiniowany jako funkcja globalna

Nie można użyć klasy generycznej ani szablonu jako funkcji globalnej.

Ten błąd może być spowodowany nieprawidłowym dopasowaniem nawiasów klamrowych.

Poniższy przykład generuje C2935:

```cpp
// C2935.cpp
// compile with: /c
template<class T>
struct TC {};
void TC<int>() {}   // C2935

// OK
struct TC2 {};
void TC2() {}
```

C2935 może również wystąpić przy użyciu typów ogólnych:

```cpp
// C2935b.cpp
// compile with: /clr /c
generic<class T>
ref struct GC { };
void GC<int>() {}   // C2935
void GC() {}   // OK
```
