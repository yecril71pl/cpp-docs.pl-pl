---
title: Błąd kompilatora C3541
ms.date: 11/04/2016
f1_keywords:
- C3541
helpviewer_keywords:
- C3541
ms.assetid: 252cfd4c-5fd2-415e-a17d-6b0c254350db
ms.openlocfilehash: 32926d0ef9343bad9ed73458e4d52d317b628109
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221045"
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

## <a name="see-also"></a>Zobacz także

[Słowo kluczowe "Autouzupełnianie"](../../cpp/auto-keyword.md)<br/>
[/Zc: Auto(wywnioskowanie typu zmiennej)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[typeid](../../extensions/typeid-cpp-component-extensions.md)
