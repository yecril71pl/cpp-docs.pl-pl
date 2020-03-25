---
title: Ostrzeżenie kompilatora (poziom 1) C4272
ms.date: 11/04/2016
f1_keywords:
- C4272
helpviewer_keywords:
- C4272
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
ms.openlocfilehash: 747b9e60ad2b8b0036c6eac50d44c2d70277384f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163112"
---
# <a name="compiler-warning-level-1-c4272"></a>Ostrzeżenie kompilatora (poziom 1) C4272

"Function": jest oznaczona __declspec (dllimport); podczas importowania funkcji należy określić natywną konwencję wywoływania.

Wystąpił błąd podczas eksportowania funkcji oznaczonej konwencją wywoływania [__clrcall](../../cpp/clrcall.md) i kompilator wystawia to ostrzeżenie, jeśli próbujesz zaimportować funkcję oznaczoną jako `__clrcall`.

Poniższy przykład generuje C4272:

```cpp
// C4272.cpp
// compile with: /c /W1 /clr
__declspec(dllimport) void __clrcall Test();   // C4272
__declspec(dllimport) void Test2();   // OK
```
