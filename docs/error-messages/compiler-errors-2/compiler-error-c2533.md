---
title: Błąd kompilatora C2533
ms.date: 11/04/2016
f1_keywords:
- C2533
helpviewer_keywords:
- C2533
ms.assetid: 5b335652-076c-4824-87c8-a741f64a3ce0
ms.openlocfilehash: b111448e7e9d8260a5101d05996a670013936894
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746412"
---
# <a name="compiler-error-c2533"></a>Błąd kompilatora C2533

"Identyfikator": konstruktory nie mogą być typem zwracanym

Konstruktor nie może mieć zwracanego typu (nawet `void` zwracanego typu).

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
