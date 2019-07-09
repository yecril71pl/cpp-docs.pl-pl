---
title: Błąd kompilatora C2316
ms.date: 07/08/2019
f1_keywords:
- C2316
helpviewer_keywords:
- C2316
ms.assetid: 9ad08eb5-060b-4eb0-8d66-0dc134f7bf67
ms.openlocfilehash: 5a3d9052775a5e1cbedfd58ccaaf0ff039a8475d
ms.sourcegitcommit: 07b34ca1c1fecced9fadc95de15dc5fee4f31e5a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67693444"
---
# <a name="compiler-error-c2316"></a>Błąd kompilatora C2316

> "*class_type*": nie można przechwycić elementu, ponieważ destruktor i/lub Konstruktor kopiujący są niedostępne lub zostały usunięte

Wyjątek został zgłoszony przez wartość lub przez odwołanie, ale Konstruktor kopiujący, operator przypisania lub obie były niedostępne.

## <a name="remarks"></a>Uwagi

Ten błąd, Zastosuj do instrukcji catch uszkodzonych wyjątków MFC pochodną wprowadzone zmiany zgodności w programie Visual Studio 2015 `CException`. Ponieważ `CException` ma konstruktora dziedziczone prywatnej kopii, klasa i jej pochodnych nie są możliwe do kopiowania i nie mogą być przekazywane przez wartość, co oznacza, nie może zostać przechwycony przez wartość. CATCH, instrukcje, które przechwycono wyjątków MFC według wartości, które wcześniej doprowadziło do nieprzechwyconych wyjątków w czasie wykonywania. Teraz kompilator poprawnie identyfikuje tę sytuację i zgłasza błąd C2316. Aby rozwiązać ten problem, zaleca się użycie makr MFC TRY/CATCH zamiast możesz napisać własne programy obsługi wyjątków. Jeśli nie jest odpowiednia dla kodu, przechwytywać wyjątków MFC przez odwołanie.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2316 i pokazuje sposób, aby rozwiązać ten problem:

```cpp
// C2316.cpp
// compile with: /EHsc
#include <stdio.h>

struct B
{
public:
    B() {}
    // Delete the following line to resolve.
private:
    // copy constructor
    B(const B&) {}
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
    catch (B b)    // C2316
    {
        printf_s("Caught an exception!\n");
    }
}
```
