---
title: Błąd kompilatora C2316
ms.date: 11/04/2016
f1_keywords:
- C2316
helpviewer_keywords:
- C2316
ms.assetid: 9ad08eb5-060b-4eb0-8d66-0dc134f7bf67
ms.openlocfilehash: 53e7743ec0d84451feb1dc1cd8849439aa142336
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345725"
---
# <a name="compiler-error-c2316"></a>Błąd kompilatora C2316

> "*wyjątek*": nie można przechwycić elementu, ponieważ destruktor i/lub Konstruktor kopiujący są niedostępne.

Wyjątek został zgłoszony przez wartość lub przez odwołanie, ale Konstruktor kopiujący i/lub operator przypisania były niedostępne.

Ten kod został zaakceptowany przez wersje programu Visual C++ przed Visual Studio 2003, ale teraz powoduje błąd.

Ten błąd, Zastosuj do instrukcji catch uszkodzonych wyjątków MFC pochodną wprowadzone zmiany zgodności w programie Visual Studio 2015 `CException`. Ponieważ `CException` ma konstruktora dziedziczone prywatnej kopii, klasa i jej pochodne są niekopiowalnych i nie mogą być przekazywane przez wartość, co oznacza, nie może zostać przechwycony przez wartość. CATCH, instrukcje, które przechwycono wyjątków MFC według wartości, które wcześniej doprowadziło do nieprzechwyconych wyjątków w czasie wykonywania, ale teraz kompilator poprawnie identyfikuje tej sytuacji i raporty błędów C2316. Aby rozwiązać ten problem, zalecane jest użycie makr MFC TRY/CATCH, zamiast pisania własnych programów obsługi wyjątków, ale jeśli nie jest odpowiednia dla kodu, przechwytywać wyjątków MFC przez odwołanie zamiast tego.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2316:

```
// C2316.cpp
// compile with: /EHsc
#include <stdio.h>

extern "C" int printf_s(const char*, ...);

struct B
{
public:
    B() {}
    // Delete the following line to resolve.
private:
    // copy constructor
    B(const B&)
    {
    }
};

void f(const B&)
{
}

int main()
{
    try
    {
        B aB;
        f(aB);
    }
    catch (B b) {   // C2316
        printf_s("Caught an exception!\n");
    }
}
```