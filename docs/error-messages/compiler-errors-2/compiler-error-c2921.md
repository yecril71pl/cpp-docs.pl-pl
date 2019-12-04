---
title: Błąd kompilatora C2921
ms.date: 11/04/2016
f1_keywords:
- C2921
helpviewer_keywords:
- C2921
ms.assetid: 323642a0-bfc4-4942-9f41-c3adf5c54296
ms.openlocfilehash: 82042b851282e686719ed54ccad0a2802afda22b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761022"
---
# <a name="compiler-error-c2921"></a>Błąd kompilatora C2921

Ponowna definicja: "Class": szablon klasy lub ogólny jest ponownie deklarowany jako "typ"

Klasa generyczna lub szablonu ma wiele deklaracji, które nie są równoważne. Aby naprawić ten błąd, Użyj różnych nazw dla różnych typów lub Usuń ponowną definicję nazwy typu.

Poniższy przykład generuje C2921:

```cpp
// C2921.cpp
// compile with: /c
template <class T> struct TC2 {};
typedef int TC2;   // C2921
// try the following line instead
// typedef struct TC2<int> x;   // OK - declare a template instance
```

C2921 może również wystąpić podczas korzystania z typów ogólnych.

```cpp
// C2921b.cpp
// compile with: /clr /c
generic <class T> ref struct GC2 {};
typedef int GC2;   // C2921
// try the following line instead
// typedef ref struct GC2<int> x;
```
