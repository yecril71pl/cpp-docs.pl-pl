---
title: Kompilator ostrzeżenie (poziom 1) C4545
ms.date: 11/04/2016
f1_keywords:
- C4545
helpviewer_keywords:
- C4545
ms.assetid: 43f8f34f-ed46-4661-95c0-c588c577ff73
ms.openlocfilehash: 59e8bf18302d94ac609773e36a782f1457c8db6e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490873"
---
# <a name="compiler-warning-level-1-c4545"></a>Kompilator ostrzeżenie (poziom 1) C4545

wyrażenie przed przecinkiem daje w wyniku funkcję, dla której brakuje listy argumentów

Kompilator wykrył wyrażenie przecinkowe źle sformułowane.

To ostrzeżenie jest domyślnie wyłączona. Aby uzyskać więcej informacji, zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

Poniższy przykład spowoduje wygenerowanie C4545:

```
// C4545.cpp
// compile with: /W1
#pragma warning (default : 4545)

void f() { }

int main()
{
   *(&f), 10;   // C4545
   // try the following line instead
   // (*(&f))(), 10;
}
```