---
title: Błąd kompilatora C2797
ms.date: 11/04/2016
f1_keywords:
- C2797
helpviewer_keywords:
- C2797
ms.assetid: 9fb26d35-eb5c-46fc-9ff5-756fba5bdaff
ms.openlocfilehash: 9973ddcccc69e85bdf79e0623fa4bcc1d6689032
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202086"
---
# <a name="compiler-error-c2797"></a>Błąd kompilatora C2797

Zbędn Inicjalizacja listy wewnątrz listy inicjatorów składowych lub inicjatora niestatycznej składowej danych nie jest zaimplementowana.

To ostrzeżenie jest przestarzałe w programie Visual Studio 2015. W Visual Studio 2013 i wcześniejszych wersjach kompilator firmy Microsoft C++ nie implementuje inicjalizacji listy wewnątrz listy inicjatorów składowych lub inicjatora niestatycznej składowej danych. Przed Visual Studio 2013 Update 3, zostało to dyskretnie skonwertowane do wywołania funkcji, co może prowadzić do nieprawidłowego generowania kodu. Visual Studio 2013 Update 3 raportuje jako błąd.

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

Aby rozwiązać ten problem, można użyć jawnej konstrukcji list wewnętrznych. Na przykład:

```
#include <vector>
typedef std::vector<int> Vector;
struct S {
    S() : v1(Vector{1}) {}

    Vector v1;
    Vector v2 = Vector{1, 2};
};
```

Jeśli nie jest wymagane inicjowanie listy:

```
struct S {
    S() : s1("") {}

    std::string s1;
    std::string s2 = std::string("");
};
```

(Kompilator w Visual Studio 2013 robi to niejawnie przed Visual Studio 2013 Update 3).
