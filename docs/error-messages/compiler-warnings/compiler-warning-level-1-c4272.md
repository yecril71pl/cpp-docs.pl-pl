---
title: Ostrzeżenie kompilatora (poziom 1) C4272
ms.date: 11/04/2016
f1_keywords:
- C4272
helpviewer_keywords:
- C4272
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
ms.openlocfilehash: 26e136aa395729d520f4a71a06b6dc212cf21f8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208314"
---
# <a name="compiler-warning-level-1-c4272"></a>Ostrzeżenie kompilatora (poziom 1) C4272

'Funkcja': jest oznaczony jako __declspec(dllimport); należy określić natywną Konwencję wywoływania podczas importu funkcji.

Jest to błąd, aby wyeksportować oznaczona za pomocą funkcji [__clrcall](../../cpp/clrcall.md) wywoływania Konwencji i kompilator generuje ostrzeżenie, jeśli próba zaimportowania funkcji oznaczonej `__clrcall`.

Poniższy przykład spowoduje wygenerowanie C4272:

```
// C4272.cpp
// compile with: /c /W1 /clr
__declspec(dllimport) void __clrcall Test();   // C4272
__declspec(dllimport) void Test2();   // OK
```