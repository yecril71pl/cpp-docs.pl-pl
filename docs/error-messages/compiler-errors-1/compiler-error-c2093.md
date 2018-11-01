---
title: Błąd kompilatora C2093
ms.date: 11/04/2016
f1_keywords:
- C2093
helpviewer_keywords:
- C2093
ms.assetid: 17529a70-9169-46b5-9fc6-57a5ce224e6a
ms.openlocfilehash: d57b452e63f7bf76051ef6a23c5f8f6ba81aed1e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511153"
---
# <a name="compiler-error-c2093"></a>Błąd kompilatora C2093

"variable1": nie można zainicjować przy użyciu adresu automatycznej zmiennej "variable2"

Podczas kompilowania za pomocą [/Za](../../build/reference/za-ze-disable-language-extensions.md), program dotarła do adresu automatycznej zmiennej jako inicjatora.

Poniższy przykład spowoduje wygenerowanie C2093:

```
// C2093.c
// compile with: /Za /c
void func() {
   int li;   // an implicit auto variable
   int * s[]= { &li };   // C2093 address is not a constant

   // OK
   static int li2;
   int * s2[]= { &li2 };
}
```