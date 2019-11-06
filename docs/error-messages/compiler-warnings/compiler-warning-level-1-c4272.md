---
title: Ostrzeżenie kompilatora (poziom 1) C4272
ms.date: 11/04/2016
f1_keywords:
- C4272
helpviewer_keywords:
- C4272
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
ms.openlocfilehash: 13c56c2261cd069e7edec63921c198e2bee56c95
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626698"
---
# <a name="compiler-warning-level-1-c4272"></a>Ostrzeżenie kompilatora (poziom 1) C4272

"Function": jest oznaczona jako __declspec (dllimport); podczas importowania funkcji należy określić natywną konwencję wywoływania.

Wystąpił błąd podczas eksportowania funkcji oznaczonej konwencją wywoływania [__clrcall](../../cpp/clrcall.md) , a kompilator generuje to ostrzeżenie, jeśli próbujesz zaimportować funkcję oznaczoną jako `__clrcall`.

Poniższy przykład generuje C4272:

```cpp
// C4272.cpp
// compile with: /c /W1 /clr
__declspec(dllimport) void __clrcall Test();   // C4272
__declspec(dllimport) void Test2();   // OK
```