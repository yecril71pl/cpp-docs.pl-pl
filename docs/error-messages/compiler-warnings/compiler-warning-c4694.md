---
title: Ostrzeżenie kompilatora C4694
ms.date: 10/25/2017
f1_keywords:
- C4694
helpviewer_keywords:
- C4694
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
ms.openlocfilehash: daf5423588d08260239c3cff5a68532a358d07b2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165122"
---
# <a name="compiler-warning-c4694"></a>Ostrzeżenie kompilatora C4694

> "*Class*": zapieczętowana Klasa abstrakcyjna nie może mieć klasy bazowej "*BASE_CLASS*"

Klasa abstrakcyjna i zapieczętowana nie może dziedziczyć z typu referencyjnego; Klasa zapieczętowana i abstrakcyjna nie może implementować funkcji klasy bazowej ani nie zezwalać na używanie jej jako klasy bazowej.

Aby uzyskać więcej informacji, zobacz [abstrakcyjne](../../extensions/abstract-cpp-component-extensions.md), [zapieczętowane](../../extensions/sealed-cpp-component-extensions.md)i [klasy i struktury](../../extensions/classes-and-structs-cpp-component-extensions.md).

To ostrzeżenie jest automatycznie podwyższana do błędu. Jeśli chcesz zmodyfikować to zachowanie, użyj [#pragma ostrzeżenie](../../preprocessor/warning.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C4694.

```cpp
// C4694.cpp
// compile with: /c /clr
ref struct A {};
ref struct B sealed abstract : A {};   // C4694
```
