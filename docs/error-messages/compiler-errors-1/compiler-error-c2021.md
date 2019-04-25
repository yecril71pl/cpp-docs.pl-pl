---
title: Błąd kompilatora C2021
ms.date: 11/04/2016
f1_keywords:
- C2021
helpviewer_keywords:
- C2021
ms.assetid: 064f32e2-3794-48d5-9767-991003dcb36a
ms.openlocfilehash: 6492dfffbb5a2f80ea543d4248c0f77759c0a521
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303609"
---
# <a name="compiler-error-c2021"></a>Błąd kompilatora C2021

Oczekiwana wartość wykładnika, a nie "character"

Znak używany jako wykładnika zmiennoprzecinkowej stałej nie jest prawidłową liczbą. Pamiętaj użyć wykładnik, który znajduje się w zakresie.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2021:

```
// C2021.cpp
float test1=1.175494351E;   // C2021
```

## <a name="example"></a>Przykład

Możliwe rozwiązanie:

```
// C2021b.cpp
// compile with: /c
float test2=1.175494351E8;
```