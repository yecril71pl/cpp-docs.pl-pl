---
title: Błąd kompilatora C3461
ms.date: 11/04/2016
f1_keywords:
- C3461
helpviewer_keywords:
- C3461
ms.assetid: bd66833a-545d-445a-bdfe-dee771a450a4
ms.openlocfilehash: d1bf4af63bac2aaee1da4bb98f23c3b15e98c671
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756633"
---
# <a name="compiler-error-c3461"></a>Błąd kompilatora C3461

"Type": tylko typ zarządzany może być przekazywany

Przekazywanie typu może wystąpić tylko w przypadku typów CLR.  Aby uzyskać więcej informacji [, zobacz klasy i struktury](../../extensions/classes-and-structs-cpp-component-extensions.md) .

Aby uzyskać więcej informacji, zobacz [przekazywanie typuC++(/CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład tworzy składnik.

```cpp
// C3461.cpp
// compile with: /clr /LD
public ref class R {};
```

## <a name="example"></a>Przykład

Poniższy przykład generuje C3461.

```cpp
// C3461b.cpp
// compile with: /clr /c
#using "C3461.dll"
class N {};
[assembly:TypeForwardedTo(N::typeid)];   // C3461
[assembly:TypeForwardedTo(R::typeid)];   // OK
```
