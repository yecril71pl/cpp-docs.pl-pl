---
title: Kompilator ostrzeżenie (poziom 4) C4937
ms.date: 11/04/2016
f1_keywords:
- C4937
helpviewer_keywords:
- C4937
ms.assetid: 2bb9f0e7-bbd6-4697-84de-95955e32ae29
ms.openlocfilehash: 64565ad37c965aa0af3b912988586b37270be6a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280272"
---
# <a name="compiler-warning-level-4-c4937"></a>Kompilator ostrzeżenie (poziom 4) C4937

"text1" i "Tekst2" są nierozróżnialne jako argumenty "dyrektywa"

Ze względu na sposób kompilator przetwarza argumenty dyrektywy, nazw, które mają znaczenie dla kompilatora, takich jak słowa kluczowe w wielu liczbami w postaci tekstu (podkreślenia jedno- i formularze), nie może być wyodrębnione.

Przykłady takich ciągów są __cdecl i \__forceinline.  Uwaga: w obszarze/za, są włączone tylko formularze podwójnym podkreśleniem.

Poniższy przykład spowoduje wygenerowanie C4937:

```
// C4937.cpp
// compile with: /openmp /W4
#include "omp.h"
int main() {
   #pragma omp critical ( __leave )   // C4937
   ;

   // OK
   #pragma omp critical ( leave )
   ;
}
```