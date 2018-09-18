---
title: Błąd kompilatora C3883 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3883
dev_langs:
- C++
helpviewer_keywords:
- C3883
ms.assetid: cdd1c1f4-f268-4469-9c62-d52303114b0c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4387eacb4e35c82af5c2617771b8c887dae42c4e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045474"
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