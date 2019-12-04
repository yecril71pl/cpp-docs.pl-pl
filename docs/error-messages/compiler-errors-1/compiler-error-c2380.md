---
title: Błąd kompilatora C2380
ms.date: 11/04/2016
f1_keywords:
- C2380
helpviewer_keywords:
- C2380
ms.assetid: 717b1e6e-ddfe-4bac-a5f3-7f9a4dcb1572
ms.openlocfilehash: ca249bc592bd66c2e461a37fdc18204077f51db2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745437"
---
# <a name="compiler-error-c2380"></a>Błąd kompilatora C2380

Typ (-y) poprzedzający "identifier" (Konstruktor z typem zwracanym lub niedozwolone ponowne zdefiniowanie bieżącej nazwy klasy?)

Konstruktor zwraca wartość lub ponownie definiuje nazwę klasy.

Poniższy przykład generuje C2326:

```cpp
// C2380.cpp
// compile with: /c
class C {
public:
   int C();   // C2380, specifies an int return
   int C;   // C2380, redefinition of i
   C();   // OK
};
```
