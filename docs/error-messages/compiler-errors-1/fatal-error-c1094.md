---
title: Błąd krytyczny C1094
ms.date: 11/04/2016
f1_keywords:
- C1094
helpviewer_keywords:
- C1094
ms.assetid: 9e1193b2-cb95-44f9-bf6f-019e0d41dd97
ms.openlocfilehash: 23891a783a018f6d84ea820af98992f61632984c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469657"
---
# <a name="fatal-error-c1094"></a>Błąd krytyczny C1094

"-Zmval1": opcja wiersza polecenia jest niespójna z wartością używany do tworzenia prekompilowanego pliku nagłówkowego ("-Zmval2")

Wartość, która jest przekazywana do [/Yc](../../build/reference/yc-create-precompiled-header-file.md) musi być taka sama jak wartość jest przekazywana do [/Yu](../../build/reference/yu-use-precompiled-header-file.md) (**/Zm** wartości muszą być takie same we wszystkich kompilacjach, które użycia lub utwórz taki sam prekompilowanych Plik nagłówkowy).

Poniższy przykład spowoduje wygenerowanie C1094:

```
// C1094.h
int func1();
```

Następnie wyszukaj maszynę

```
// C1094.cpp
// compile with: /Yc"C1094.h" /Zm200
int u;
int main() {
   int sd = 32;
}
#include "C1094.h"
```

Następnie wyszukaj maszynę

```
// C1094b.cpp
// compile with: /Yu"C1094.h" /Zm300 /c
#include "C1094.h"   // C1094 compile with /Zm200
void Test() {}
```