---
title: Błąd kompilatora C2397
ms.date: 11/04/2016
f1_keywords:
- C2397
ms.assetid: b418cf5a-d50d-4a6c-98a7-994ae35046d1
ms.openlocfilehash: 02a8bb09e0b22619bd61e6c4675057263a62a9d5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206018"
---
# <a name="compiler-error-c2397"></a>Błąd kompilatora C2397

Konwersja z "type_1" na "type_2" wymaga konwersji z zawężaniem

Znaleziono niejawną konwersję zawężaną podczas korzystania z jednolitej inicjalizacji.

Język C umożliwia niejawne zawężanie konwersji w przypisaniach C++ i inicjalizacji, a nawet w przypadku nieoczekiwanej zawężania jest przyczyną wystąpienia wielu błędów kodu. Aby kod był bezpieczniejszy, C++ Standard wymaga komunikatu diagnostycznego, gdy na liście inicjalizacji wystąpi konwersja wąski. W wizualizacji C++, Diagnostyka jest błędem kompilatora C2397, gdy jest używana składnia Jednolite inicjowanie obsługiwana na początku w programie Visual Studio 2015. Kompilator generuje [Ostrzeżenie kompilatora (poziom 1) C4838](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md) przy użyciu składni inicjalizacji listy lub agregacji obsługiwanej przez Visual Studio 2013.

Zawężanie konwersji może być odpowiednie, gdy wiadomo, że możliwy zakres przekonwertowanych wartości może pasować do obiektu docelowego. W takim przypadku wiadomo, że masz więcej niż kompilator. W przypadku zamierzonego zawężania konwersji należy zapewnić jawne użycie rzutowania statycznego. W przeciwnym razie ten komunikat o błędzie prawie zawsze wskazuje, że w kodzie wystąpi błąd. Możesz rozwiązać ten problem, upewniając się, że inicjowane obiekty mają wystarczająco duże typy, aby obsłużyć dane wejściowe.

Poniższy przykład generuje C2397 i pokazuje jeden ze sposobów rozwiązania tego problemu:

```
// C2397.cpp -- C++ narrowing conversion diagnostics
// Compile by using: cl /EHsc C2397.cpp
#include <vector>

struct S1 {
    int m1;
    double m2, m3;
};

void function_C2397(double d1) {
    char c1 { 127 };          // OK
    char c2 { 513 };          // error C2397

    std::vector<S1> vS1;
    vS1.push_back({ d1, 2, 3 }); // error C2397

    // Possible fix if you know d1 always fits in an int
    vS1.push_back({ static_cast<int>(d1), 2, 3 });
}
```
