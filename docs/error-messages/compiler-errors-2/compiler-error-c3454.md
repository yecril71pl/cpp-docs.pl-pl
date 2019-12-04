---
title: Błąd kompilatora C3454
ms.date: 11/04/2016
f1_keywords:
- C3454
helpviewer_keywords:
- C3454
ms.assetid: dc4e6d57-5b4d-4114-8d6f-22f9ae62925b
ms.openlocfilehash: 1909dc772413c16d39271dc839a0ec0db206da03
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756685"
---
# <a name="compiler-error-c3454"></a>Błąd kompilatora C3454

[Attribute] nie jest dozwolony w deklaracji klasy

Klasa musi być zdefiniowana, aby mogła być atrybutem.

Aby uzyskać więcej informacji, zobacz [atrybut](../../windows/attributes/attribute.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3454.

```cpp
// C3454.cpp
// compile with: /clr /c
using namespace System;

[attribute]   // C3454
ref class Attr1;

[attribute]   // OK
ref class Attr2 {};
```
