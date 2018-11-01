---
title: Błąd kompilatora C2803
ms.date: 11/04/2016
f1_keywords:
- C2803
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
ms.openlocfilehash: d20b8dde9f4134273adcba0f947f685f7ce7d213
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447271"
---
# <a name="compiler-error-c2803"></a>Błąd kompilatora C2803

"operator operator" musi mieć co najmniej jeden formalny parametr typu klasy

Przeciążony operator nie ma parametr typu klasy.

Należy przekazać co najmniej jeden parametr według odwołania (bez użycia wskaźników, lecz przywołuje) lub według wartości, aby można było zapisać "< b" (typ klasy A i b).

Jeśli oba parametry są wskaźnikami będzie czysty porównania adresów wskaźnika i nie będzie używać konwersja zdefiniowana przez użytkownika.

Poniższy przykład spowoduje wygenerowanie C2803:

```
// C2803.cpp
// compile with: /c
class A{};
bool operator< (const A *left, const A *right);   // C2803
// try the following line instead
// bool operator< (const A& left, const A& right);
```