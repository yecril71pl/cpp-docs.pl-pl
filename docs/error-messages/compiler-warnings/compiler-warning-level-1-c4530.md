---
title: Kompilator ostrzeżenie (poziom 1) C4530
ms.date: 11/04/2016
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: a542f9b6bb73e561592e1e779aa6ee493612e6ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160721"
---
# <a name="compiler-warning-level-1-c4530"></a>Kompilator ostrzeżenie (poziom 1) C4530

Obsługa wyjątków języka C++, używane, ale semantyka rozwinięć nie są włączone. Określ/ehsc

Została użyta Obsługa wyjątków języka C++, ale [/ehsc](../../build/reference/eh-exception-handling-model.md) nie został wybrany.

Nie włączono opcji/ehsc, obiekt z automatycznego przechowywania w ramce, między funkcje, wykonując throw i przechwytywanie throw, nie zostać zniszczone. Jednak obiekt przy użyciu automatycznego przechowywania utworzony w **spróbuj** lub **catch** bloku zostaną zniszczone.

Poniższy przykład spowoduje wygenerowanie C4530:

```
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

Skompiluj próbki z/ehsc, aby rozwiązać ostrzeżenia.