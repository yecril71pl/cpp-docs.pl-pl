---
title: Błąd kompilatora C2803 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2803
dev_langs:
- C++
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7885735ebad1ff90afaf4ba8eaf6dfca9f3e0ab3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027044"
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