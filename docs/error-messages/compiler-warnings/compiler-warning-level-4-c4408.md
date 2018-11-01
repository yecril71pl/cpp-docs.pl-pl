---
title: Kompilator ostrzeżenie (poziom 4) C4408
ms.date: 11/04/2016
f1_keywords:
- C4408
helpviewer_keywords:
- C4408
ms.assetid: 8488a186-ed1d-425c-aaeb-c72472c1da68
ms.openlocfilehash: 3c7613d42bbd0ac7fa58a0b95ba68efb60d9f50a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553871"
---
# <a name="compiler-warning-level-4-c4408"></a>Kompilator ostrzeżenie (poziom 4) C4408

anonymousstruct lub Unii nie zadeklarował żadnych składowych danych

Anonimowej struktury lub Unii musi mieć co najmniej jeden element członkowski danych.

Poniższy przykład spowoduje wygenerowanie C4408:

```
// C4408.cpp
// compile with: /W4 /LD
static union
{
   // int i;
};
// a named union can have no data members
// } MyUnion;
```