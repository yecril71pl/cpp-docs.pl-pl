---
title: Kompilator ostrzeżenie (poziom 2) C4396
ms.date: 11/04/2016
f1_keywords:
- C4396
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
ms.openlocfilehash: 84045ea2c285be8b1c1c9d1fd62b417db00dd29c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445321"
---
# <a name="compiler-warning-level-2-c4396"></a>Kompilator ostrzeżenie (poziom 2) C4396

"name": wbudowany specyfikator nie można użyć, gdy zaprzyjaźniona deklaracja odnosi się do specjalizacji szablonu funkcji

Specjalizacja szablonu funkcji nie można określić dowolną z [wbudowane](../../cpp/inline-functions-cpp.md) specyfikatorów. Kompilator generuje ostrzeżenie C4396 i ignoruje wbudowany specyfikator.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Usuń `inline`, `__inline`, lub `__forceinline` specyfikator w deklaracji funkcji friend.

## <a name="example"></a>Przykład

Nieprawidłowy friend funkcji deklaracji z ilustruje poniższy przykład kodu `inline` specyfikator.

```
// C4396.cpp
// compile with: /W2 /c

class X;
template<class T> void Func(T t, int i);

class X {
    friend inline void Func<char>(char t, int i);  //C4396
// try the following line instead
//    friend void Func<char>(char t, int i);
    int i;
};
```