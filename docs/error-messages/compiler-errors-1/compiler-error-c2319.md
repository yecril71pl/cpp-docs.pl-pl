---
title: Błąd kompilatora C2319
ms.date: 11/04/2016
f1_keywords:
- C2319
helpviewer_keywords:
- C2319
ms.assetid: 25263e6e-f5ba-4d2c-8727-8c2d8ca2e5ce
ms.openlocfilehash: b3da0297558a9b8281f9c4756a54a577cc78a682
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747920"
---
# <a name="compiler-error-c2319"></a>Błąd kompilatora C2319

po instrukcji "try/catch" musi występować złożona instrukcja. Brak znaku "{"

Nie znaleziono bloku `try` lub `catch` po instrukcji `try` lub `catch`. Blok musi być ujęty w nawiasy klamrowe.

Poniższy przykład generuje C2319:

```cpp
// C2319.cpp
// compile with: /EHsc
#include <eh.h>
class C {};
int main() {
   try {
      throw "ooops!";
   }
   catch( C ) ;    // C2319
   // try the following line instead
   // catch( C ) {}
}
```
