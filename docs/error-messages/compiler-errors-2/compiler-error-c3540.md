---
title: Błąd kompilatora C3540
ms.date: 11/04/2016
f1_keywords:
- C3540
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
ms.openlocfilehash: 57e4145557272f76a890a356c79982346cd74d7e
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345481"
---
# <a name="compiler-error-c3540"></a>Błąd kompilatora C3540

"type": nie można zastosować operatora sizeof do typu, który zawiera "auto"

[Sizeof](../../cpp/sizeof-operator.md) nie można zastosować operatora do wskazanego typu, ponieważ zawiera ona `auto` specyfikator.

## <a name="example"></a>Przykład

Poniższy przykład daje C3540.

```
// C3540.cpp
// Compile with /Zc:auto
int main() {
    auto x = 123;
    sizeof(x);    // OK
    sizeof(auto); // C3540
    return 0;
}
```

## <a name="see-also"></a>Zobacz także

[Auto, słowo kluczowe](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (Dedukuj typ zmiennej)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[sizeof, operator](../../cpp/sizeof-operator.md)