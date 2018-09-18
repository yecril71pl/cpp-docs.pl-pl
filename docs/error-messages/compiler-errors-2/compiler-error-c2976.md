---
title: Błąd kompilatora C2976 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2976
dev_langs:
- C++
helpviewer_keywords:
- C2976
ms.assetid: d9bf9836-325e-4f72-a7e3-a67cf19d32e7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a82cbe896d44190c5d7e6ee098f0f5a7a27e9378
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072917"
---
# <a name="compiler-error-c2976"></a>Błąd kompilatora C2976

'Identyfikator': za mało argumentów typu

Brak co najmniej jeden rzeczywisty argument generyczny lub szablonu. Sprawdź deklaracji generyczny lub szablonu, aby znaleźć prawidłowej liczby parametrów.

Ten błąd może być spowodowany przez brak argumentów szablonu w składnikach standardowej biblioteki języka C++.

Poniższy przykład spowoduje wygenerowanie C2976:

```
// C2976.cpp
template <class T>
struct TC {
   T t;
};
int main() {
   TC<>* t;   // C2976
   TC<int>* t2;   // OK
}
```

C2976 może również wystąpić, gdy za pomocą typów ogólnych:

```
// C2976b.cpp
// compile with: /clr
generic <class T>
ref struct GC {
   T t;
};

int main() {
   GC<>^ g;   // C2976
   GC<int>^ g2;   // OK
}
```