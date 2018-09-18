---
title: Kompilator ostrzeżenie (poziom 1) C4530 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4530
dev_langs:
- C++
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbfbc67377dd48eeb692bdd4cac1f113fbdf7f6a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110461"
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