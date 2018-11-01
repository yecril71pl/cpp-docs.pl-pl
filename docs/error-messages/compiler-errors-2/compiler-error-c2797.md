---
title: Błąd kompilatora C2797
ms.date: 11/04/2016
f1_keywords:
- C2797
helpviewer_keywords:
- C2797
ms.assetid: 9fb26d35-eb5c-46fc-9ff5-756fba5bdaff
ms.openlocfilehash: 8ae8c4b8755e6f9c89c0706b0644f220761bd9c2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616245"
---
# <a name="compiler-error-c2797"></a>Błąd kompilatora C2797

(Przestarzałe) Inicjowanie listy wewnątrz listy inicjatorów składowych lub inicjatora składowej danych niestatycznych nie jest zaimplementowana.

To ostrzeżenie jest przestarzała w programie Visual Studio 2015. W programie Visual Studio 2013 i wcześniejszych wersjach kompilator języka Visual C++ nie implementuje Inicjowanie listy wewnątrz listy inicjatorów składowej lub inicjatora składowej danych niestatycznych. Przed Visual Studio 2013 Update 3 to był dyskretnie konwertowane wywołanie funkcji, która może spowodować wygenerowanie złego kodu. Visual Studio 2013 Update 3 to raporty jako błąd.

Ten przykład generuje C2797:

```
#include <vector>
struct S {
    S() : v1{1} {} // C2797, VS2013 RTM incorrectly calls 'vector(size_type)'

    std::vector<int> v1;
    std::vector<int> v2{1, 2}; // C2797, VS2013 RTM incorrectly calls 'vector(size_type, const int &)'
};

```

Ten przykład generuje również C2797:

```
struct S1 {
    int i;
};

struct S2 {
    S2() : s1{0} {} // C2797, VS2013 RTM interprets as S2() : s1(0) {} causing C2664
    S1 s1;
    S1 s2{0}; // C2797, VS2013 RTM interprets as S1 s2 = S1(0); causing C2664
};

```

Aby rozwiązać ten problem, można użyć konstrukcji jawnych list wewnętrzny. Na przykład:

```
#include <vector>
typedef std::vector<int> Vector;
struct S {
    S() : v1(Vector{1}) {}

    Vector v1;
    Vector v2 = Vector{1, 2};
};

```

Jeśli nie potrzebujesz inicjalizacji listy:

```
struct S {
    S() : s1("") {}

    std::string s1;
    std::string s2 = std::string("");
};

```

(Kompilator programu Visual Studio 2013 robi to niejawnie przed Visual Studio 2013 Update 3.)