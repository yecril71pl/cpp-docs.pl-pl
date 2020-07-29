---
title: Błąd kompilatora C2534
ms.date: 11/04/2016
f1_keywords:
- C2534
helpviewer_keywords:
- C2534
ms.assetid: 481f9f54-5b51-4aa0-8eea-218f10807705
ms.openlocfilehash: 202e3bbe2238b4cc2a5233ac4e093717d623f099
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87207904"
---
# <a name="compiler-error-c2534"></a>Błąd kompilatora C2534

"Identyfikator": Konstruktor nie może zwrócić wartości

Konstruktor nie może zwrócić wartości ani mieć zwracanego typu (nawet **`void`** typu zwracanego).

Ten błąd może zostać naprawiony przez usunięcie **`return`** instrukcji z definicji konstruktora.

Poniższy przykład generuje C2534:

```cpp
// C2534.cpp
class A {
public:
   int i;
   A() { return i; }   // C2534
};
```
