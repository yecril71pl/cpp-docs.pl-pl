---
title: Błąd kompilatora C2279
ms.date: 11/04/2016
f1_keywords:
- C2279
helpviewer_keywords:
- C2279
ms.assetid: 1b5c88ef-2336-49b8-9ddb-d61f97c73e14
ms.openlocfilehash: f35e384a5b242eb28427e1ff62ac55a3e9b206c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666228"
---
# <a name="compiler-error-c2279"></a>Błąd kompilatora C2279

Specyfikacja wyjątku nie może występować w deklaracji typedef

W obszarze **/Za**, [specyfikacje wyjątków](../../cpp/exception-specifications-throw-cpp.md) nie są dozwolone w deklaracji typedef.

Poniższy przykład spowoduje wygenerowanie C2279:

```
// C2279.cpp
// compile with: /Za /c
typedef int (*xy)() throw(...);   // C2279
typedef int (*xyz)();   // OK
```