---
title: Błąd kompilatora C2178 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/08/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2178
dev_langs:
- C++
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af9efdb3258e6793a17a26b552df8ba4e63c9107
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102342"
---
# <a name="compiler-error-c2178"></a>Błąd kompilatora C2178

"*identyfikator*"nie może być zadeklarowana z"*specyfikator*" Specyfikator

A `mutable` specyfikator został użyty w deklaracji, ale specyfikator jest niedozwolony w tym kontekście.

`mutable` Specyfikator mogą być stosowane tylko do nazwy elementów członkowskich danych klasy i nie można zastosować do nazwy zadeklarowane `const` lub `static`i nie można zastosować do odwoływać się do elementów członkowskich.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak może wystąpić C2178 i jak go naprawić.

```
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```
