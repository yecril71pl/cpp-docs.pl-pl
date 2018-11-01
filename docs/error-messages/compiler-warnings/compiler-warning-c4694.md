---
title: Ostrzeżenie kompilatora C4694
ms.date: 10/25/2017
f1_keywords:
- C4694
helpviewer_keywords:
- C4694
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
ms.openlocfilehash: 6eaaa4c1f16e2ac2c5029511430a145fd9b943e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428345"
---
# <a name="compiler-warning-c4694"></a>Ostrzeżenie kompilatora C4694

> "*klasy*": zapieczętowana klasa abstrakcyjna nie może mieć klasy bazowej*element $base_class*"

Klasy abstrakcyjne i zapieczętowane nie może dziedziczyć z typu referencyjnego; Klasa zapieczętowany i abstrakcyjny nie można zaimplementować funkcje klasy bazowej ani mógł służyć jako klasę bazową.

Aby uzyskać więcej informacji, zobacz [abstrakcyjne](../../windows/abstract-cpp-component-extensions.md), [zapieczętowanego](../../windows/sealed-cpp-component-extensions.md), i [klas i struktur](../../windows/classes-and-structs-cpp-component-extensions.md).

To ostrzeżenie zostanie automatycznie podwyższony do błędu. Jeśli chcesz zmienić to zachowanie, użyj [ostrzeżenie #pragma](../../preprocessor/warning.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4694.

```cpp
// C4694.cpp
// compile with: /c /clr
ref struct A {};
ref struct B sealed abstract : A {};   // C4694
```