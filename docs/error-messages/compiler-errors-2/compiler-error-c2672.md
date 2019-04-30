---
title: Błąd kompilatora C2672
ms.date: 10/24/2017
f1_keywords:
- C2672
helpviewer_keywords:
- C2672
ms.assetid: 7e86338a-2d4b-40fe-9dd2-ac6886f3f31a
ms.openlocfilehash: df0f656c9db23739ec62629088b9cc5f7950a92d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386866"
---
# <a name="compiler-error-c2672"></a>Błąd kompilatora C2672

> "*funkcja*": nie zgodnej przeciążonej funkcji, o których odnaleźć

Kompilator nie może odnaleźć przeciążonej funkcji, który odpowiada określonej funkcji. Żadna funkcja nie został znaleziony, że przyjmuje pasujących do parametrów lub brak pasującego funkcji ma wymagane ułatwień dostępu w kontekście.

Gdy jest używana przez niektóre kontenery standardowej biblioteki lub algorytmów, typów należy podać dostępne elementy Członkowskie lub Friend — funkcje, które spełniają wymagania kontenera lub algorytm. Na przykład typów iteratora powinien pochodzić od `std::iterator<>`. Typ jest traktowany jako po lewej stronie i prawostronny operand może wymagać operacji porównania lub używanie innych operatorów dla typów elementu kontenera. Użyj tego typu, jak prawostronny operand może wymagać wykonania operatora w funkcji składowej typu.

## <a name="example"></a>Przykład

Wersji kompilatora Visual Studio 2017 r. nie wykonał dostępu, sprawdzając kwalifikowane nazwy w niektórych kontekstach szablonów. Może to zakłócać oczekiwane zachowanie SFINAE, gdzie podstawienia może zakończyć się niepowodzeniem z powodu inaccessibility nazwy. To może potencjalnie spowodowały awarię lub nieoczekiwane zachowanie w czasie wykonywania, ponieważ kompilator niepoprawnie wywoływania niewłaściwego przeciążenia operatora. W programie Visual Studio 2017 zgłaszany jest błąd kompilatora.

W tym przykładzie kompiluje w programie Visual Studio 2015, ale zgłasza błąd w programie Visual Studio 2017. Aby rozwiązać ten problem, należy wprowadzić elementu członkowskiego parametr szablonu, które są dostępne, gdzie jest oceniany.

```cpp
#include <type_traits>

template <class T> class S {
// public:    // Uncomment this line to fix
    typedef typename T type;
};

template <class T, std::enable_if<std::is_integral<typename S<T>::type>::value, T> * = 0>
bool f(T x)
{
    return (x == 0);
}

int main()
{
    f(10); // C2672: No matching overloaded function found.
}
```