---
title: Błąd kompilatora C3452
ms.date: 11/04/2016
f1_keywords:
- C3452
helpviewer_keywords:
- C3452
ms.assetid: e5293dcf-cb70-4133-ae2a-0bb496950ba0
ms.openlocfilehash: c491217f01d8e78375401b54faa48d9db410ccad
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756724"
---
# <a name="compiler-error-c3452"></a>Błąd kompilatora C3452

członek argumentu listy nie jest stałą

Argument został przekazano do atrybutu, który oczekiwał stałej, wartość, która może być oceniona w czasie kompilacji.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3452.

```cpp
// C3452.cpp
// compile with: /c
int i;
[module( name="mod", type=dll, custom={i} ) ];   // C3452
// try the following line instead
// [module( name="mod", type=dll, custom={"a"} ) ];
```
