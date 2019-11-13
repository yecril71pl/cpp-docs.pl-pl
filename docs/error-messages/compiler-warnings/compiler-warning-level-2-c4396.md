---
title: Ostrzeżenie kompilatora (poziom 2) C4396
ms.date: 11/04/2016
f1_keywords:
- C4396
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
ms.openlocfilehash: e874e00d44eef29240cca55541837facfcf64495
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052042"
---
# <a name="compiler-warning-level-2-c4396"></a>Ostrzeżenie kompilatora (poziom 2) C4396

"name": wbudowany specyfikator nie może być używany, gdy zaprzyjaźniona deklaracja odnosi się do specjalizacji szablonu funkcji

Specjalizacja szablonu funkcji nie może określać żadnego ze specyfikatorów [wbudowanych](../../cpp/inline-functions-cpp.md) . Kompilator wystawia ostrzeżenia C4396 i ignoruje Specyfikator wbudowany.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Usuń specyfikator `inline`, `__inline`lub `__forceinline` z deklaracji zaprzyjaźnionej funkcji.

## <a name="example"></a>Przykład

Poniższy przykład kodu przedstawia nieprawidłową deklarację zaprzyjaźnionej funkcji ze specyfikatorem `inline`.

```cpp
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