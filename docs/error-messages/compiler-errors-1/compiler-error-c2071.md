---
title: Błąd kompilatora C2071
ms.date: 11/04/2016
f1_keywords:
- C2071
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
ms.openlocfilehash: 1dc9781bc0cf1bc6c7f879cc3971828983471c6f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757751"
---
# <a name="compiler-error-c2071"></a>Błąd kompilatora C2071

"Identyfikator": niedozwolona Klasa magazynu

`identifier` został zadeklarowany przy użyciu nieprawidłowej [klasy magazynu](../../c-language/c-storage-classes.md). Ten błąd może być spowodowany tym, że dla identyfikatora określono więcej niż jedną klasę magazynu, lub gdy definicja jest niezgodna z deklaracją klasy magazynu.

Aby rozwiązać ten problem, zapoznaj się z zamierzoną klasą magazynu identyfikatora — na przykład `static` lub `extern`— i popraw deklarację do dopasowania.

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
