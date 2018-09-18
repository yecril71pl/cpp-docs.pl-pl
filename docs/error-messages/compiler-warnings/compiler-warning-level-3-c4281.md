---
title: Kompilator ostrzeżenie (poziom 3) C4281 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4281
dev_langs:
- C++
helpviewer_keywords:
- C4281
ms.assetid: a9771261-5725-4fc6-87b6-16cf92113a25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 106269be7d63126854aa1396bd6045532b4102ed
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079144"
---
# <a name="compiler-warning-level-3-c4281"></a>Kompilator ostrzeżenie (poziom 3) C4281

"operator ->" rekursja wystąpiła za pośrednictwem typu "type"

Kod umożliwia **operator ->** można wywoływać samego siebie.

Poniższy przykład spowoduje wygenerowanie C4281:

```
// C4281.cpp
// compile with: /W3 /WX
struct A;
struct B;
struct C;

struct A
{
   int z;
   B& operator->();
};

struct B
{
   C& operator->();
};

struct C
{
   A& operator->();
};

void f(A p)
{
   int i = p->z; // C4281
}
```