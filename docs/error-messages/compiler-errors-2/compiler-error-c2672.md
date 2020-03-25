---
title: Błąd kompilatora C2672
ms.date: 10/24/2017
f1_keywords:
- C2672
helpviewer_keywords:
- C2672
ms.assetid: 7e86338a-2d4b-40fe-9dd2-ac6886f3f31a
ms.openlocfilehash: 9f844b54285a7df69bfb4387a7afcc82dfef9252
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177134"
---
# <a name="compiler-error-c2672"></a>Błąd kompilatora C2672

> "*Function*": nie znaleziono zgodnej przeciążonej funkcji

Kompilator nie może odnaleźć przeciążonej funkcji zgodnej z określoną funkcją. Nie znaleziono funkcji, która pobiera zgodne parametry lub żadna zgodna funkcja nie ma wymaganego dostępu w kontekście.

W przypadku użycia przez niektóre standardowe kontenery biblioteki lub algorytmy typy muszą zapewnić dostępnym członkom lub znajomym funkcjom, które spełniają wymagania kontenera lub algorytmu. Na przykład typy iteratorów powinny pochodzić od `std::iterator<>`. Operacje porównania lub użycie innych operatorów w typach elementów kontenera mogą wymagać, aby typ był traktowany jako po lewej stronie i po prawej stronie. Użycie typu jako argumentu operacji po prawej stronie może wymagać implementacji operatora jako funkcji nienależącej do elementu członkowskiego typu.

## <a name="example"></a>Przykład

Wersje kompilatora przed Visual Studio 2017 nie wykonywały sprawdzenia dostępu do nazw kwalifikowanych w niektórych kontekstach szablonów. Może to zakłócać oczekiwane zachowanie SFINAE, w którym zastępowanie oczekuje się niepowodzeniem z powodu niedostępności nazwy. Może to spowodować awarię lub nieoczekiwane zachowanie w czasie wykonywania, ponieważ kompilator niepoprawnie wywołuje nieprawidłowe Przeciążenie operatora. W programie Visual Studio 2017 został zgłoszony błąd kompilatora.

Ten przykład kompiluje się w programie Visual Studio 2015, ale zgłasza błąd w programie Visual Studio 2017. Aby rozwiązać ten problem, należy udostępnić element członkowski parametru szablonu w przypadku jego oceny.

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
