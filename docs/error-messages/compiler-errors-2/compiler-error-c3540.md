---
title: Błąd kompilatora C3540
ms.date: 11/04/2016
f1_keywords:
- C3540
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
ms.openlocfilehash: 897defd5643a90234c2ae3b7bb4f58904864e858
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508077"
---
# <a name="compiler-error-c3540"></a>Błąd kompilatora C3540

"Type": nie można zastosować operatora sizeof do typu, który zawiera element "Auto"

Nie można zastosować operatora [sizeof](../../cpp/sizeof-operator.md) do wskazanego typu, ponieważ zawiera on **`auto`** specyfikator.

## <a name="example"></a>Przykład

Poniższy przykład daje C3540.

```cpp
// C3540.cpp
// Compile with /Zc:auto
int main() {
    auto x = 123;
    sizeof(x);    // OK
    sizeof(auto); // C3540
    return 0;
}
```

## <a name="see-also"></a>Zobacz też

[Słowo kluczowe "Autouzupełnianie"](../../cpp/auto-cpp.md)<br/>
[/Zc: Auto(wywnioskowanie typu zmiennej)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[sizeof — Operator](../../cpp/sizeof-operator.md)
