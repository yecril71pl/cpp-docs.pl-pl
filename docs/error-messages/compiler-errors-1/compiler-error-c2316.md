---
title: Błąd kompilatora C2316 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2316
dev_langs:
- C++
helpviewer_keywords:
- C2316
ms.assetid: 9ad08eb5-060b-4eb0-8d66-0dc134f7bf67
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2868d3a81fcbc94d8b20adcdc775363eb0a8eaeb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033020"
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