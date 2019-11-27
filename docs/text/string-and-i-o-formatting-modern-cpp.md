---
title: Formatowanie ciągów i we/wy (Modern C++)
description: Opcje dla sformatowanego ciągu we/wy dostępne w C++nowoczesnej.
ms.date: 05/30/2019
ms.topic: conceptual
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
ms.openlocfilehash: facb0b62cc1e92ed09a9ba729d766e5db7404282
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74308176"
---
# <a name="string-and-io-formatting-modern-c"></a>Formatowanie ciągów i we/wy (Modern C++)

C++[\<iostream >](../standard-library/iostream.md) klasy, funkcje i operatory obsługują sformatowaną ciąg we/wy. Na przykład poniższy kod pokazuje, jak ustawić `cout` formatowania liczby całkowitej na dane wyjściowe w formacie szesnastkowym. Najpierw zapisuje bieżący stan, aby ponownie go resetować, ponieważ stan formatu jest przekazywać do `cout`, pozostaje taki sam, dopóki nie zostanie zmieniony. Nie dotyczy to tylko jednego wiersza kodu.

```cpp
#include <iostream>
#include <iomanip>

using namespace std;

int main()
{
    ios state(nullptr);

    cout << "The answer in decimal is: " << 42 << endl;

    state.copyfmt(cout); // save current formatting
    cout << "In hex: 0x" // now load up a bunch of formatting modifiers
        << hex
        << uppercase
        << setw(8)
        << setfill('0')
        << 42            // the actual value we wanted to print out
        << endl;
    cout.copyfmt(state); // restore previous formatting
}
```

Takie podejście jest bezpieczne dla typów i rozszerzalne, ale jest również złożone i pełne.

## <a name="alternative-format-options"></a>Opcje formatu alternatywnego

Alternatywnie można użyć `Boost.Format` z bibliotek zwiększania C++ poziomu, nawet jeśli jest to niestandardowa. Możesz pobrać dowolną bibliotekę zwiększaną z witryny sieci Web [zwiększanie](https://www.boost.org/) poziomu.

Niektóre zalety `Boost.Format` są następujące:

- Bezpieczny: bezpieczny dla typów i zgłasza wyjątek dla błędów, na przykład specyfikacja zbyt mała lub zbyt wiele elementów.

- Rozszerzalne: działa dla dowolnego typu, który może być przesyłany strumieniowo.

- Wygodne: standardowa wersja POSIX i podobne ciągi formatujące.

Chociaż `Boost.Format` jest oparta na C++ [\<iostream >](../standard-library/iostream-programming.md) , które są bezpieczne i rozszerzalne, nie są zoptymalizowane pod kątem wydajności. Gdy wymagasz optymalizacji wydajności, rozważ użycie języka C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) i [sprintf —](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), które są szybkie i łatwe w użyciu. Jednak nie są one rozszerzalne ani bezpieczne przed lukami w zabezpieczeniach. (Istnieją bezpieczne wersje, ale wiążą się one z niewielkimi karami za wydajność. Aby uzyskać więcej informacji, zobacz [printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md) i [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)).

Poniższy kod ilustruje niektóre z funkcji zwiększania formatowania.

```cpp
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );
    // s contains "hello hello world"

    for( auto i = 0; i < names.size(); ++i )
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321
```

## <a name="see-also"></a>Zobacz także

[Zapraszamy ponownie doC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)<br/>
[\<iostream >](../standard-library/iostream.md)<br/>
[limity \<>](../standard-library/limits.md)<br/>
[\<iomanip >](../standard-library/iomanip.md)
