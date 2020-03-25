---
title: Ostrzeżenie kompilatora (poziom 2) C4396
ms.date: 11/04/2016
f1_keywords:
- C4396
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
ms.openlocfilehash: f37fcc7ece09bb9028a522ec6baf85d0e0e585c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161818"
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
