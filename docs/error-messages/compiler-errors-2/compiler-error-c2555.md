---
title: Błąd kompilatora C2555
ms.date: 11/04/2016
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: cc6c3a3a29665ccf65b77a3d9866986cb0a46b9e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353231"
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

Poniższy przykład spowoduje wygenerowanie C2555:

```cpp
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