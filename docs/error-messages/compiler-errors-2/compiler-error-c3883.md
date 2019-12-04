---
title: Błąd kompilatora C3883
ms.date: 11/04/2016
f1_keywords:
- C3883
helpviewer_keywords:
- C3883
ms.assetid: cdd1c1f4-f268-4469-9c62-d52303114b0c
ms.openlocfilehash: 9dbb0328aa1810d55f2d974aed822992b53101b5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736662"
---
# <a name="compiler-error-c3883"></a>Błąd kompilatora C3883

"var": statyczna składowa danych initonly musi być zainicjowana

Zmienna oznaczona przy użyciu [initonly](../../dotnet/initonly-cpp-cli.md) nie została poprawnie zainicjowana.

Poniższy przykład generuje C3883:

```cpp
// C3883.cpp
// compile with: /clr
ref struct Y1 {
   initonly
   static int staticConst1;   // C3883
};
```

Poniższy przykład demonstruje możliwe rozwiązanie:

```cpp
// C3883b.cpp
// compile with: /clr /c
ref struct Y1 {
   initonly
   static int staticConst2 = 0;
};
```

Poniższy przykład pokazuje, jak zainicjować w konstruktorze statycznym:

```cpp
// C3883c.cpp
// compile with: /clr /LD
ref struct Y1 {
   initonly
   static int staticConst1;

   static Y1() {
      staticConst1 = 0;
   }
};
```
