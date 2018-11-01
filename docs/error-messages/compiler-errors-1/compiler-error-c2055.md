---
title: Błąd kompilatora C2055
ms.date: 11/04/2016
f1_keywords:
- C2055
helpviewer_keywords:
- C2055
ms.assetid: 6cec79cc-6bec-443f-9897-fbf5452718c7
ms.openlocfilehash: 3c198168b4445e619148e5611621fa3ddba95d6b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597278"
---
# <a name="compiler-error-c2055"></a>Błąd kompilatora C2055

Oczekiwano formalnej listy parametrów, nie listy typów

Definicja funkcji zawiera listę typów parametrów zamiast formalnej listy parametrów. ANSI C wymaga parametrów formalnych w nazwanych, chyba że są one void lub wielokropkiem (`...`).

Poniższy przykład spowoduje wygenerowanie C2055:

```
// C2055.c
// compile with: /c
void func(int, char) {}  // C2055
void func (int i, char c) {}   // OK
```