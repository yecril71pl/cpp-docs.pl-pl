---
title: Błąd kompilatora C2921
ms.date: 11/04/2016
f1_keywords:
- C2921
helpviewer_keywords:
- C2921
ms.assetid: 323642a0-bfc4-4942-9f41-c3adf5c54296
ms.openlocfilehash: 47f348f6c30d96e8c4ae40e0c26a8ebade14c8ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611253"
---
# <a name="compiler-error-c2921"></a>Błąd kompilatora C2921

Ponowna definicja: "class": szablon klasy lub typ ogólny jest ponownie deklarowany jako "type"

Klasa generyczny lub szablonu ma wiele deklaracje, które nie są równoważne. Aby naprawić ten błąd, użyj innej nazwy dla różnych typów, lub usuń ponowna definicja nazwę typu.

Poniższy przykład spowoduje wygenerowanie C2921:

```
// C2921.cpp
// compile with: /c
template <class T> struct TC2 {};
typedef int TC2;   // C2921
// try the following line instead
// typedef struct TC2<int> x;   // OK - declare a template instance
```

C2921 może również wystąpić, gdy za pomocą typów ogólnych.

```
// C2921b.cpp
// compile with: /clr /c
generic <class T> ref struct GC2 {};
typedef int GC2;   // C2921
// try the following line instead
// typedef ref struct GC2<int> x;
```