---
title: Błąd kompilatora C2071
ms.date: 11/04/2016
f1_keywords:
- C2071
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
ms.openlocfilehash: 95344b5ef675f566f433dfeaed9dee5c38ef77d4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598279"
---
# <a name="compiler-error-c2071"></a>Błąd kompilatora C2071

'Identyfikator': niedozwolona Klasa magazynu

`identifier` zadeklarowano z nieprawidłowym [klasę magazynu](../../c-language/c-storage-classes.md). Ten błąd może być spowodowany, gdy więcej niż jedną klasę magazynu jest określone dla identyfikatora, lub gdy definicja jest niezgodny z deklaracją klasy magazynowania.

Aby rozwiązać ten problem, należy zrozumieć klasy magazynu zamierzony identyfikatora — na przykład `static` lub `extern`— i popraw deklarację do dopasowania.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2071.

```
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

Poniższy przykład spowoduje wygenerowanie C2071.

```
// C2071_b.cpp
// compile with: /c
typedef int x(int i) { return i; }   // C2071
typedef int (x)(int);   // OK, no local definition in typedef
```