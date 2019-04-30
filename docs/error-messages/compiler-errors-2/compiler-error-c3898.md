---
title: Compiler Error C3898
ms.date: 11/04/2016
f1_keywords:
- C3898
helpviewer_keywords:
- C3898
ms.assetid: d9a90df6-87e4-4fe7-ab01-c226ee86bf10
ms.openlocfilehash: 503f295d62c598e3138b1a001d6b350c0d90ea84
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385449"
---
# <a name="compiler-error-c3898"></a>Compiler Error C3898

"var": składowe danych typu mogą być tylko składowymi typów zarządzanych

[Initonly](../../dotnet/initonly-cpp-cli.md) element członkowski danych została zadeklarowana w klasie natywnych.  `initonly` Element członkowski danych mogą być deklarowane tylko w klasie CLR.

Poniższy przykład spowoduje wygenerowanie C3898:

```
// C3898.cpp
// compile with: /clr
struct Y1 {
   initonly
   static int data_var = 9;   // C3898
};
```

Możliwe rozwiązanie:

```
// C3898b.cpp
// compile with: /clr /c
ref struct Y1 {
   initonly
   static int data_var = 9;
};
```