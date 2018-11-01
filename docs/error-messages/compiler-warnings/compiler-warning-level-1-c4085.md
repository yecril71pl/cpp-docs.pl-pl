---
title: Kompilator ostrzeżenie (poziom 1) C4085
ms.date: 11/04/2016
f1_keywords:
- C4085
helpviewer_keywords:
- C4085
ms.assetid: 2bc6eb25-058f-4597-b351-fd69587b5170
ms.openlocfilehash: cfd2296d2e58899bf818281716af2074c2f0ce91
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640755"
---
# <a name="compiler-warning-level-1-c4085"></a>Kompilator ostrzeżenie (poziom 1) C4085

Oczekiwano wartości parametru pragma "on" lub "off"

Wymaga pragmy **na** lub **poza** parametru. Pragmy jest ignorowany.

Poniższy przykład spowoduje wygenerowanie C4085:

```
// C4085.cpp
// compile with: /W1 /LD
#pragma optimize( "t", maybe )  // C4085
```