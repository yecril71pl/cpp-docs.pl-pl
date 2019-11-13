---
title: Ostrzeżenie kompilatora (poziom 3) C4357
ms.date: 11/04/2016
f1_keywords:
- C4357
helpviewer_keywords:
- C4357
ms.assetid: 9259c633-3c02-4900-b94a-2d8d366d61cd
ms.openlocfilehash: 7a1d9f30c4b95236294b67804d57a03873c05143
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051621"
---
# <a name="compiler-warning-level-3-c4357"></a>Ostrzeżenie kompilatora (poziom 3) C4357

argument tablicy parametrów na liście formalnych argumentów dla delegata "del" został zignorowany podczas generowania "Function"

Atrybut `ParamArray` został zignorowany, a `function` nie można wywołać za pomocą argumentów zmiennych.

Poniższy przykład generuje C4357:

```cpp
// C4357.cpp
// compile with: /clr /W3 /c
using namespace System;
public delegate void f(int i, ... array<Object^>^ varargs);   // C4357

public delegate void g(int i, array<Object^>^ varargs);   // OK
```