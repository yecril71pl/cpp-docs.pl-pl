---
title: Błąd kompilatora C3541 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3541
dev_langs:
- C++
helpviewer_keywords:
- C3541
ms.assetid: 252cfd4c-5fd2-415e-a17d-6b0c254350db
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a0f9cb18089bcf8ce1688cabb261f91f868da247
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021723"
---
# <a name="compiler-error-c3541"></a>Błąd kompilatora C3541

"type": typeid nie można zastosować do typu, który zawiera "auto"

[Typeid](../../windows/typeid-cpp-component-extensions.md) nie można zastosować operatora do wskazanego typu, ponieważ zawiera ona `auto` specyfikator.

## <a name="example"></a>Przykład

Poniższy przykład daje się C3541.

```
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

[Auto, słowo kluczowe](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (Dedukuj typ zmiennej)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[TypeID](../../windows/typeid-cpp-component-extensions.md)