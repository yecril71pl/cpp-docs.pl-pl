---
title: Błąd kompilatora C2092
ms.date: 11/04/2016
f1_keywords:
- C2092
helpviewer_keywords:
- C2092
ms.assetid: 037e44ae-16c8-489a-a512-dcdf7f7795a6
ms.openlocfilehash: 8f2b83b4099308ea1d0bb127d8cea377ab65da96
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90741894"
---
# <a name="compiler-error-c2092"></a>Błąd kompilatora C2092

Typ elementu tablicy "Array Name" nie może być funkcją

Tablice funkcji są niedozwolone. Użyj tablicy wskaźników do funkcji.

## <a name="examples"></a>Przykłady

Poniższy przykład generuje C2092:

```cpp
// C2092.cpp
typedef void (F) ();
typedef F AT[10];   // C2092
```

Możliwe rozwiązanie:

```cpp
// C2092b.cpp
// compile with: /c
typedef void (F) ();
typedef F * AT[10];
```
