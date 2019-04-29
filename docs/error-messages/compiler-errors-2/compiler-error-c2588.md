---
title: Błąd kompilatora C2588
ms.date: 11/04/2016
f1_keywords:
- C2588
helpviewer_keywords:
- C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
ms.openlocfilehash: 15f9ba62751d9b3cb17ab56659310292dab41adf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350455"
---
# <a name="compiler-error-c2588"></a>Błąd kompilatora C2588

":: ~ identyfikator": niedozwolony globalny — destruktor

Destruktor jest zdefiniowane dla coś innego niż klasy, struktury lub Unii. Jest to niedozwolone.

Ten błąd może być spowodowany przez Brak klasy, struktury lub Unii nazwę po lewej stronie rozpoznawania zakresu (`::`) — operator.

Poniższy przykład spowoduje wygenerowanie C2588:

```
// C2588.cpp
~F();   // C2588
```