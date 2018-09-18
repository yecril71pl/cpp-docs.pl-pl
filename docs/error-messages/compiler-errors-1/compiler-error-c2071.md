---
title: Błąd kompilatora C2071 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2071
dev_langs:
- C++
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 757110c88d3279964ab0c26f753e4d3b1f2889d5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025867"
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