---
title: Błąd kompilatora C3755
ms.date: 11/04/2016
f1_keywords:
- C3755
helpviewer_keywords:
- C3755
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
ms.openlocfilehash: cc4e5423dc8fc53a8f749e2392ff23658a0cb0f1
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685118"
---
# <a name="compiler-error-c3755"></a>Błąd kompilatora C3755

"delegat": delegat nie może być zdefiniowany

[Delegat (C++ Component Extensions)](../../extensions/delegate-cpp-component-extensions.md) może być zadeklarowany, ale nie zdefiniowany.

## <a name="examples"></a>Przykłady

Poniższy przykład generuje C3755.

```cpp
// C3755.cpp
// compile with: /clr /c
delegate void MyDel() {};   // C3755
```

C3755 może również wystąpić w przypadku próby utworzenia szablonu delegowania. Poniższy przykład generuje C3755.

```cpp
// C3755_b.cpp
// compile with: /clr /c
ref struct R {
   template<class T>
   delegate void D(int) {}   // C3755
};
```
