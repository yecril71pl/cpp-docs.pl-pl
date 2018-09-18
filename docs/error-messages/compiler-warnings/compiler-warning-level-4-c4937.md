---
title: Kompilator ostrzeżenie (poziom 4) C4937 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4937
dev_langs:
- C++
helpviewer_keywords:
- C4937
ms.assetid: 2bb9f0e7-bbd6-4697-84de-95955e32ae29
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e7bc6232458b357f41e859c58d4b6b77f78ef2a7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118300"
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