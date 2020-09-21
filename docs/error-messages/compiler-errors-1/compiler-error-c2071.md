---
title: Błąd kompilatora C2071
ms.date: 11/04/2016
f1_keywords:
- C2071
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
ms.openlocfilehash: 7619d968379bfc35e98bd87071b75296d10c382c
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743285"
---
# <a name="compiler-error-c2071"></a>Błąd kompilatora C2071

"Identyfikator": niedozwolona Klasa magazynu

`identifier` został zadeklarowany za pomocą nieprawidłowej [klasy magazynu](../../c-language/c-storage-classes.md). Ten błąd może być spowodowany tym, że dla identyfikatora określono więcej niż jedną klasę magazynu, lub gdy definicja jest niezgodna z deklaracją klasy magazynu.

Aby rozwiązać ten problem, zapoznaj się z zamierzoną klasą magazynu identyfikatora — na przykład **`static`** lub **`extern`** — i popraw deklarację do dopasowania.

## <a name="examples"></a>Przykłady

Poniższy przykład generuje C2071.

```cpp
// C2071.cpp
// compile with: /c
struct C {
   extern int i;   // C2071
};
struct D {
   int i;   // OK, no extern on an automatic
};
```

Poniższy przykład generuje C2071.

```cpp
// C2071_b.cpp
// compile with: /c
typedef int x(int i) { return i; }   // C2071
typedef int (x)(int);   // OK, no local definition in typedef
```
