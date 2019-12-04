---
title: Błąd kompilatora C3675
ms.date: 11/04/2016
f1_keywords:
- C3675
helpviewer_keywords:
- C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
ms.openlocfilehash: 6772572d29765370d6cdbf52ed8470ff2f3f054e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758076"
---
# <a name="compiler-error-c3675"></a>Błąd kompilatora C3675

"Function": jest zarezerwowana, ponieważ zdefiniowano Właściwość "Property"

Gdy deklarujesz prostą właściwość, kompilator generuje metody dostępu get i Set, a te nazwy są obecne w zakresie programu.  Nazwy wygenerowane przez kompilator są tworzone przez oczekujące get_ i set_ do nazwy właściwości.  W związku z tym nie można zadeklarować funkcji o takiej samej nazwie jak dla metod dostępu generowanych przez kompilator.

Aby uzyskać więcej informacji, zobacz [Właściwość](../../extensions/property-cpp-component-extensions.md) .

## <a name="example"></a>Przykład

Poniższy przykład generuje C3675.

```cpp
// C3675.cpp
// compile with: /clr /c
ref struct C {
public:
   property int Size;
   int get_Size() { return 0; }   // C3675
};
```
