---
title: Błąd kompilatora C2768
ms.date: 11/04/2016
f1_keywords:
- C2768
helpviewer_keywords:
- C2768
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
ms.openlocfilehash: 9c0fb8fb0a98830aaf061ba980e7bdd7903f25e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626177"
---
# <a name="compiler-error-c2768"></a>Błąd kompilatora C2768

'Funkcja': niedozwolone użycie argumentów jawnego szablonu

Kompilator nie może określić, jeśli definicja funkcji została powinien być jawna specjalizacja szablonu funkcji lub definicji funkcji została powinna być dla nowych funkcji.

Ten błąd został wprowadzony w Visual Studio .NET 2003 w jako część ulepszenia zgodności kompilatora.

Poniższy przykład spowoduje wygenerowanie C2768:

```
// C2768.cpp
template<typename T>
void f(T) {}

void f<int>(int) {}   // C2768

// an explicit specialization
template<>
void f<int>(int) {}

// global nontemplate function overload
void f(int) {}
```