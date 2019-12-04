---
title: Błąd kompilatora C3222
ms.date: 11/04/2016
f1_keywords:
- C3222
helpviewer_keywords:
- C3222
ms.assetid: 5624bde8-2fd0-4b8b-92ce-5dfbaf91cf93
ms.openlocfilehash: 96a6b1b81d2d82328dcb4ceaca376f247f785c13
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737949"
---
# <a name="compiler-error-c3222"></a>Błąd kompilatora C3222

"parameter": nie można zadeklarować domyślnych argumentów dla funkcji składowych typu zarządzanego lub generycznego lub funkcji ogólnych

Deklarowanie parametru metody z domyślnym argumentem nie jest dozwolone. Przeciążona forma metody to jeden ze sposobów obejścia tego problemu. Oznacza to, że należy zdefiniować metodę o tej samej nazwie bez parametrów, a następnie zainicjować zmienną w treści metody.

Poniższy przykład generuje C3222:

```cpp
// C3222_2.cpp
// compile with: /clr
public ref class G {
   void f( int n = 0 );   // C3222
};
```
