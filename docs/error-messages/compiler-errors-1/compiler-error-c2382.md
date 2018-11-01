---
title: Błąd kompilatora C2382
ms.date: 11/04/2016
f1_keywords:
- C2382
helpviewer_keywords:
- C2382
ms.assetid: 4d4436f9-d0d6-4bd0-b8ec-767b89adfb2f
ms.openlocfilehash: 4115a01f9e4dcab31a05bb3994109e97694121e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593073"
---
# <a name="compiler-error-c2382"></a>Błąd kompilatora C2382

'Funkcja': zmiana definicji; różne specyfikacje wyjątków

W obszarze [/Za](../../build/reference/za-ze-disable-language-extensions.md), ten błąd wskazuje, że przeciążenia funkcji podjęto wyłącznie w systemach [Specyfikacja wyjątku](../../cpp/exception-specifications-throw-cpp.md).

Poniższy przykład spowoduje wygenerowanie C2382:

```
// C2382.cpp
// compile with: /Za /c
void f1(void) throw(int) {}
void f1(void) throw(char) {}   // C2382
void f2(void) throw(char) {}   // OK
```