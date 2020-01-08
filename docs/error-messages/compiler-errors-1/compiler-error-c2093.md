---
title: Błąd kompilatora C2093
ms.date: 11/04/2016
f1_keywords:
- C2093
helpviewer_keywords:
- C2093
ms.assetid: 17529a70-9169-46b5-9fc6-57a5ce224e6a
ms.openlocfilehash: 52fcd69e631f1ca24664cde06478ae33ca2a37f2
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301954"
---
# <a name="compiler-error-c2093"></a>Błąd kompilatora C2093

"variable1": nie można zainicjować przy użyciu adresu automatycznej zmiennej "variable2"

Podczas kompilowania z [/za](../../build/reference/za-ze-disable-language-extensions.md), program próbował użyć adresu zmiennej automatycznej jako inicjatora.

Poniższy przykład generuje C2093:

```c
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
