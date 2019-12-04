---
title: Błąd kompilatora C3100
ms.date: 11/04/2016
f1_keywords:
- C3100
helpviewer_keywords:
- C3100
ms.assetid: 7a9c9eaf-08ef-442d-94a0-e457beee8549
ms.openlocfilehash: 4a0e0995b1a4dcbc92f02de03920893f884c2c7c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750042"
---
# <a name="compiler-error-c3100"></a>Błąd kompilatora C3100

"target": nieznany kwalifikator atrybutu

Określono nieprawidłowy element docelowy atrybutu.

Aby uzyskać więcej informacji, zobacz [atrybuty zdefiniowane przez użytkownika](../../extensions/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3100.

```cpp
// C3100.cpp
// compile with: /clr /c
using namespace System;
[AttributeUsage(AttributeTargets::All)]
public ref class Attr : public Attribute {
public:
   Attr(int t) : m_t(t) {}
   int m_t;
};

[invalid_target:Attr(10)];   // C3100
[assembly:Attr(10)];   // OK
```
