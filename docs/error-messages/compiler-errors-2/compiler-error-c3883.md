---
title: Błąd kompilatora C3883
ms.date: 11/04/2016
f1_keywords:
- C3883
helpviewer_keywords:
- C3883
ms.assetid: cdd1c1f4-f268-4469-9c62-d52303114b0c
ms.openlocfilehash: 51ecf5fbc793c02a23e2aa02fb08e37ebe4b0ad0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559773"
---
# <a name="compiler-error-c3883"></a>Błąd kompilatora C3883

"var": statyczna składowa danych initonly musi zostać zainicjowany

Zmienna jest oznaczona za pomocą [initonly](../../dotnet/initonly-cpp-cli.md) nie został poprawnie zainicjowany.

Poniższy przykład spowoduje wygenerowanie C3883:

```
// C3883.cpp
// compile with: /clr
ref struct Y1 {
   initonly
   static int staticConst1;   // C3883
};
```

W poniższym przykładzie pokazano możliwe rozwiązania:

```
// C3883b.cpp
// compile with: /clr /c
ref struct Y1 {
   initonly
   static int staticConst2 = 0;
};
```

Poniższy przykład pokazuje, jak zainicjować w konstruktorze statycznym:

```
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