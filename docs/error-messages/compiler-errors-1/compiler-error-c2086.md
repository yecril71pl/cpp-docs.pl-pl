---
title: Błąd kompilatora C2086
ms.date: 11/04/2016
f1_keywords:
- C2086
helpviewer_keywords:
- C2086
ms.assetid: 4329bf72-90c8-444c-8524-4ef75e6b2139
ms.openlocfilehash: 094a794627b886abc7db5ba4d74c6fe97ff82461
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649744"
---
# <a name="compiler-error-c2086"></a>Błąd kompilatora C2086

'Identyfikator': zmiana definicji

Identyfikator jest zdefiniowany więcej niż jeden raz lub deklaracji kolejnych różni się od poprzedniego.

C2086 może być również wynik kompilacji przyrostowych dla przywoływanego zestawu języka C#. Ponownie skompiluj zestawu języka C#, aby rozwiązać ten problem.

Poniższy przykład spowoduje wygenerowanie C2086:

```
// C2086.cpp
main() {
  int a;
  int a;   // C2086 not an error in ANSI C
}
```