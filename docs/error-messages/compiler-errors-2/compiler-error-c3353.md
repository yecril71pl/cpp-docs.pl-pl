---
title: Błąd kompilatora C3353
ms.date: 11/04/2016
f1_keywords:
- C3353
helpviewer_keywords:
- C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
ms.openlocfilehash: 332e0b253aed53f2adadf448b6a9c0681abc825e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747454"
---
# <a name="compiler-error-c3353"></a>Błąd kompilatora C3353

"delegat": delegat może być utworzony tylko z globalnej funkcji lub funkcji składowej typu zarządzanego lub WinRT

Delegaty zadeklarowane za pomocą słowa kluczowego [delegata](../../extensions/delegate-cpp-component-extensions.md) mogą być deklarowane tylko w zakresie globalnym.

Poniższy przykład generuje C3353:

```cpp
// C3353.cpp
// compile with: /clr
delegate int f;   // C3353
```
