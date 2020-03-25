---
title: Ostrzeżenie kompilatora (poziom 3) C4197
ms.date: 11/04/2016
f1_keywords:
- C4197
helpviewer_keywords:
- C4197
ms.assetid: f766feef-82b0-4d81-8a65-33628c7db196
ms.openlocfilehash: fbc3fbf7f7408f854b1de969688dfbd25e826d84
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161597"
---
# <a name="compiler-warning-level-3-c4197"></a>Ostrzeżenie kompilatora (poziom 3) C4197

"Type": nietrwały element Top-Level w rzutowaniu jest ignorowany

Kompilator wykrył rzutowanie na typ wartości r, który jest kwalifikowany za pomocą [volatile](../../cpp/volatile-cpp.md), lub rzutowanie typu r-Value na typ, który jest kwalifikowany z nietrwałym. Zgodnie ze standardem C (6.5.3), właściwości skojarzone z kwalifikowanymi typami są zrozumiałe tylko dla wyrażeń l-wartości.

Poniższy przykład generuje C4197:

```cpp
// C4197.cpp
// compile with: /W3
#include <stdio.h>
#include <signal.h>
#include <stdlib.h>

void sigproc(int);
struct S
{
   int i;
} s;

int main()
{
   signal(SIGINT, sigproc);
   s.i = 1;
   S *pS = &s;
   for ( ; (volatile int)pS->i ; )   // C4197
      break;
   // for ( ; *(volatile int *)&pS->i ; )   // OK
   //    break;
}

void sigproc(int) // ctrl-C
{
   signal(SIGINT, sigproc);
   s.i = 0;
}
```
