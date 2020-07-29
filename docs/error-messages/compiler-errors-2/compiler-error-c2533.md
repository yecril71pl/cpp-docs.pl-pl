---
title: Błąd kompilatora C2533
ms.date: 11/04/2016
f1_keywords:
- C2533
helpviewer_keywords:
- C2533
ms.assetid: 5b335652-076c-4824-87c8-a741f64a3ce0
ms.openlocfilehash: 6c598c2c5b3ac6d88fb843534cae240c65a2d322
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87207917"
---
# <a name="compiler-error-c2533"></a>Błąd kompilatora C2533

"Identyfikator": konstruktory nie mogą być typem zwracanym

Konstruktor nie może mieć zwracanego typu (nawet **`void`** typu zwracanego).

Typowym źródłem tego błędu jest brak średnika między końcem definicji klasy a pierwszą implementacją konstruktora. Kompilator widzi klasę jako definicję zwracanego typu dla funkcji konstruktora i generuje C2533.

Poniższy przykład generuje C2533 i pokazuje, jak go naprawić:

```cpp
// C2533.cpp
// compile with: /c
class X {
public:
   X();
};

int X::X() {}   // C2533 - constructor return type not allowed
X::X() {}   // OK - fix by using no return type
```
