---
title: Błąd kompilatora C3068
ms.date: 11/04/2016
f1_keywords:
- C3068
helpviewer_keywords:
- C3068
ms.assetid: 613e3447-b4a8-4268-a661-297bed63ccdf
ms.openlocfilehash: 4790c9caafd28722f3631104cfe5cfc762cf6426
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406889"
---
# <a name="compiler-error-c3068"></a>Błąd kompilatora C3068

'Funkcja': funkcja "naked" nie może zawierać obiekty, które wymagałyby rozwinięcia gdy wystąpi wyjątek C++

Kompilator nie może wykonać odwijanie stosu w ["naked"](../../cpp/naked-cpp.md) funkcja, która zgłosiła wyjątek, ponieważ obiekt tymczasowy został utworzony w funkcji i obsługa wyjątków języka C++ ([/ehsc](../../build/reference/eh-exception-handling-model.md)) został określony.

Aby rozwiązać ten problem, wykonaj co najmniej jeden z następujących czynności:

- Nie można skompilować przy użyciu/ehsc.

- Nie oznaczaj funkcji jako `naked`.

- Nie należy tworzyć tymczasowego obiektu w funkcji.

Jeśli funkcja tworzy tymczasowy obiekt na stosie, funkcja zgłasza wyjątek, a obsługa wyjątków języka C++ jest włączona, kompilator Oczyszczanie stosu, jeśli wyjątek jest zgłaszany.

Gdy jest zgłaszany wyjątek, generowane przez kompilator kodu, nazywanych prologu i epilogu oraz tych, które nie są obecne w funkcji "naked", jest wykonywany dla funkcji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3068:

```
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