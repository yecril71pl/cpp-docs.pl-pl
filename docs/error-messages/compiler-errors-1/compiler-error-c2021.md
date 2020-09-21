---
title: Błąd kompilatora C2021
ms.date: 11/04/2016
f1_keywords:
- C2021
helpviewer_keywords:
- C2021
ms.assetid: 064f32e2-3794-48d5-9767-991003dcb36a
ms.openlocfilehash: 97d1776bb3b29b3691ae31bb060410a83d581e2d
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743298"
---
# <a name="compiler-error-c2021"></a>Błąd kompilatora C2021

oczekiwana wartość wykładnika, a nie "Character"

Znak używany jako wykładnik stałej zmiennoprzecinkowej nie jest prawidłową liczbą. Upewnij się, że używasz wykładnika, która znajduje się w zakresie.

## <a name="examples"></a>Przykłady

Poniższy przykład generuje C2021:

```cpp
// C2021.cpp
float test1=1.175494351E;   // C2021
```

Możliwe rozwiązanie:

```cpp
// C2021b.cpp
// compile with: /c
float test2=1.175494351E8;
```
