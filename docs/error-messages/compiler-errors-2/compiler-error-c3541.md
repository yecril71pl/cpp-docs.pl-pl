---
title: Błąd kompilatora C3541
ms.date: 11/04/2016
f1_keywords:
- C3541
helpviewer_keywords:
- C3541
ms.assetid: 252cfd4c-5fd2-415e-a17d-6b0c254350db
ms.openlocfilehash: 2d6179657462325a30de0c4548becff4b4cf86c9
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508073"
---
# <a name="compiler-error-c3541"></a>Błąd kompilatora C3541

"Type": nie można zastosować identyfikatora typeid do typu, który zawiera element "Auto"

Nie można zastosować operatora [typeid](../../extensions/typeid-cpp-component-extensions.md) do wskazanego typu, ponieważ zawiera on **`auto`** specyfikator.

## <a name="example"></a>Przykład

Poniższy przykład daje C3541.

```cpp
// C3541.cpp
// Compile with /Zc:auto
#include <typeinfo>
int main() {
    auto x = 123;
    typeid(x);    // OK
    typeid(auto); // C3541
    return 0;
}
```

## <a name="see-also"></a>Zobacz też

[Słowo kluczowe "Autouzupełnianie"](../../cpp/auto-cpp.md)<br/>
[/Zc: Auto(wywnioskowanie typu zmiennej)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[typeid](../../extensions/typeid-cpp-component-extensions.md)
