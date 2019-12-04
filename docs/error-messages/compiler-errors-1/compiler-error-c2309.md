---
title: Błąd kompilatora C2309
ms.date: 11/04/2016
f1_keywords:
- C2309
helpviewer_keywords:
- C2309
ms.assetid: 6303d5b5-72cf-42b8-92ce-b1eb48e80d48
ms.openlocfilehash: 2567562b5d8a75a40afcb4a94ad453ee65709a00
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759038"
---
# <a name="compiler-error-c2309"></a>Błąd kompilatora C2309

program obsługi catch oczekiwał deklaracji wyjątku ujętego w nawiasy

Procedura obsługi catch nie ma typu w nawiasach.

Poniższy przykład generuje C2309:

```cpp
// C2309.cpp
// compile with: /EHsc
#include <eh.h>
class C {};
int main() {
   try {
      throw "ooops!";
   }
   catch C {}   // C2309
   // try the following line instead
   // catch( C ) {}
}
```
