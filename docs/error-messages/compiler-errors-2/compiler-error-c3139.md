---
title: Błąd kompilatora C3139
ms.date: 11/04/2016
f1_keywords:
- C3139
helpviewer_keywords:
- C3139
ms.assetid: 95c92263-10ac-4ff3-b385-6312dd92adbc
ms.openlocfilehash: 274f3cdb3425a8a0e1e282ca6e9ca79f70077233
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761262"
---
# <a name="compiler-error-c3139"></a>Błąd kompilatora C3139

"struct": nie można eksportować UDT bez składowych

Podjęto próbę zastosowania atrybutu [eksportu](../../windows/export.md) do pustego UDT (typu zdefiniowanego przez użytkownika). Na przykład:

```cpp
// C3139.cpp
#include "unknwn.h"
[emitidl];
[module(name=xx)];

[export] struct MyStruct {   // C3139 empty type
};
int main(){}
```
