---
title: Ostrzeżenie kompilatora C4694
ms.date: 10/25/2017
f1_keywords:
- C4694
helpviewer_keywords:
- C4694
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
ms.openlocfilehash: 6164fd2e19e35233ba67feb84d117f1e4e01f20d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778842"
---
# <a name="compiler-warning-c4694"></a>Ostrzeżenie kompilatora C4694

> "*klasy*": zapieczętowana klasa abstrakcyjna nie może mieć klasy bazowej*element $base_class*"

Klasy abstrakcyjne i zapieczętowane nie może dziedziczyć z typu referencyjnego; Klasa zapieczętowany i abstrakcyjny nie można zaimplementować funkcje klasy bazowej ani mógł służyć jako klasę bazową.

Aby uzyskać więcej informacji, zobacz [abstrakcyjne](../../extensions/abstract-cpp-component-extensions.md), [zapieczętowanego](../../extensions/sealed-cpp-component-extensions.md), i [klas i struktur](../../extensions/classes-and-structs-cpp-component-extensions.md).

To ostrzeżenie zostanie automatycznie podwyższony do błędu. Jeśli chcesz zmienić to zachowanie, użyj [ostrzeżenie #pragma](../../preprocessor/warning.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4694.

```cpp
// C4694.cpp
// compile with: /c /clr
ref struct A {};
ref struct B sealed abstract : A {};   // C4694
```