---
title: Błąd kompilatora C3755
ms.date: 11/04/2016
f1_keywords:
- C3755
helpviewer_keywords:
- C3755
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
ms.openlocfilehash: 0150693ae84b45dc62c11cfdc59369eb25a819cd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757283"
---
# <a name="compiler-error-c3755"></a>Błąd kompilatora C3755

"delegat": delegat nie może być zdefiniowany

[Delegat (C++ rozszerzenia składników)](../../extensions/delegate-cpp-component-extensions.md) może być zadeklarowany, ale nie zdefiniowany.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3755.

```cpp
// C3755.cpp
// compile with: /clr /c
delegate void MyDel() {};   // C3755
```

## <a name="example"></a>Przykład

C3755 może również wystąpić w przypadku próby utworzenia szablonu delegowania. Poniższy przykład generuje C3755.

```cpp
// C3755_b.cpp
// compile with: /clr /c
ref struct R {
   template<class T>
   delegate void D(int) {}   // C3755
};
```
