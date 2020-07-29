---
title: Błąd kompilatora C2071
ms.date: 11/04/2016
f1_keywords:
- C2071
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
ms.openlocfilehash: cd815bf90b135f65072a56911c7c4b0f054fcfec
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87210075"
---
# <a name="compiler-error-c2071"></a>Błąd kompilatora C2071

"Identyfikator": niedozwolona Klasa magazynu

`identifier`został zadeklarowany za pomocą nieprawidłowej [klasy magazynu](../../c-language/c-storage-classes.md). Ten błąd może być spowodowany tym, że dla identyfikatora określono więcej niż jedną klasę magazynu, lub gdy definicja jest niezgodna z deklaracją klasy magazynu.

Aby rozwiązać ten problem, zapoznaj się z zamierzoną klasą magazynu identyfikatora — na przykład **`static`** lub **`extern`** — i popraw deklarację do dopasowania.

## <a name="example"></a>Przykład

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

## <a name="example"></a>Przykład

Poniższy przykład generuje C2071.

```cpp
// C2071_b.cpp
// compile with: /c
typedef int x(int i) { return i; }   // C2071
typedef int (x)(int);   // OK, no local definition in typedef
```
