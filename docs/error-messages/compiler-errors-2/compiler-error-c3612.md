---
title: Błąd kompilatora C3612
ms.date: 11/04/2016
f1_keywords:
- C3612
helpviewer_keywords:
- C3612
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
ms.openlocfilehash: 499c31b0c02bd72695cd6118612609a70316f0ae
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755749"
---
# <a name="compiler-error-c3612"></a>Błąd kompilatora C3612

"Type": Klasa zapieczętowana nie może być abstrakcyjna

Typy zdefiniowane za pomocą `value` są zapieczętowane domyślnie, a Klasa jest abstrakcyjna, chyba że implementuje wszystkie metody jej bazy. Zapieczętowana Klasa abstrakcyjna nie może być klasą bazową ani nie można jej utworzyć.

Aby uzyskać więcej informacji, zobacz [klasy i struktury](../../extensions/classes-and-structs-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3612:

```cpp
// C3612.cpp
// compile with: /clr /c
value struct V: public System::ICloneable {};   // C3612

// OK
value struct V2: public System::ICloneable {
   Object^ Clone();
};
```
