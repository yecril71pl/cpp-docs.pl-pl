---
title: Kompilator ostrzeżenie (poziom 4) C4516
ms.date: 11/04/2016
f1_keywords:
- C4516
helpviewer_keywords:
- C4516
ms.assetid: 6677bb1f-d26e-4ab9-8644-6b5a2a8f4ff8
ms.openlocfilehash: 8020103e8e20bf1a5e955cbfdfafc6a328b439e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564050"
---
# <a name="compiler-warning-level-4-c4516"></a>Kompilator ostrzeżenie (poziom 4) C4516

"class::symbol": deklaracje dostępu są przestarzałe; deklaracje using składowej zapewniają lepszą alternatywę

Komitet ANSI C++ zadeklarował deklaracje dostępu (zmienianie dostępu do elementu członkowskiego w klasie pochodnej bez [przy użyciu](../../cpp/using-declaration.md) — słowo kluczowe) będą nieaktualne. Deklaracje dostępu nie mogą być obsługiwane przez przyszłych wersji języka c++.

Poniższy przykład spowoduje wygenerowanie C4516:

```
// C4516.cpp
// compile with: /W4
class A
{
public:
   void x(char);
};

class B : protected A
{
public:
   A::x;  // C4516 on access-declaration
   // use the following line instead
   // using A::x; // using-declaration, ok
};

int main()
{
}
```