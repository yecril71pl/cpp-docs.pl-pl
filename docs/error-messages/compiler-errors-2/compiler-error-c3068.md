---
title: Błąd kompilatora C3068
ms.date: 11/04/2016
f1_keywords:
- C3068
helpviewer_keywords:
- C3068
ms.assetid: 613e3447-b4a8-4268-a661-297bed63ccdf
ms.openlocfilehash: 9e20333a4fc18219f7f2514f3aefe73b81f284a6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759493"
---
# <a name="compiler-error-c3068"></a>Błąd kompilatora C3068

"Function": funkcja "owies" nie może zawierać obiektów, które wymagałyby odwinięcia w C++ przypadku wystąpienia wyjątku

Kompilator nie może wykonać odwinięcia stosu dla funkcji [owies](../../cpp/naked-cpp.md) , która wywołała wyjątek, ponieważ został utworzony obiekt tymczasowy w funkcji i C++ obsłudze wyjątków ([/EHsc](../../build/reference/eh-exception-handling-model.md)).

Aby rozwiązać ten problem, należy wykonać co najmniej jedną z następujących czynności:

- Nie Kompiluj z/EHsc.

- Nie zaznaczaj funkcji jako `naked`.

- Nie należy tworzyć obiektu tymczasowego w funkcji.

Jeśli funkcja tworzy obiekt tymczasowy na stosie, jeśli funkcja zgłasza wyjątek, a jeśli C++ obsługa wyjątków jest włączona, kompilator wyczyści stos, jeśli zostanie zgłoszony wyjątek.

Gdy wyjątek jest zgłaszany, kod wygenerowany przez kompilator, nazywany prologiem i epilogu, które nie są obecne w funkcji owies, jest wykonywany dla funkcji.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3068:

```cpp
// C3068.cpp
// compile with: /EHsc
// processor: x86
class A {
public:
   A(){}
   ~A(){}
};

void b(A){}

__declspec(naked) void c() {
   b(A());   // C3068
};
```
