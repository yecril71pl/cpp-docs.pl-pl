---
title: Błąd kompilatora C2555 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2555
dev_langs:
- C++
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f91ec33db2d3a7b6772556233a3c99b501ede76
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017342"
---
# <a name="compiler-error-c2555"></a>Błąd kompilatora C2555

"class1::function1": przesłanianie funkcji wirtualnej zwracanego typu różni się i nie jest kowariantne z "class2::function2"

Funkcja wirtualna pochodnej funkcja pomijania się list parametrów identyczne, ale różne typy zwracane. Przesłanianie funkcji w klasie pochodnej nie mogą się różnić od funkcji wirtualnej w klasie bazowej tylko przez jego typem zwracanym.

Aby rozwiązać ten problem, należy rzutować wartości zwróconej po wywołaniu funkcji wirtualnej.

Ten błąd może być też widoczny, jeśli kompilujesz z opcją/CLR.   Na przykład języka Visual C++ odpowiednikiem następującą deklarację C#:

```
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

is

```
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];
```

Aby uzyskać więcej informacji na temat C2555 zobacz artykuł bazy wiedzy Q240862.

Poniższy przykład spowoduje wygenerowanie C2555:

```
// C2555.cpp
// compile with: /c
struct X {
   virtual void func();
};
struct Y : X {
   char func();  // C2555
   void func2();   // OK
};
```