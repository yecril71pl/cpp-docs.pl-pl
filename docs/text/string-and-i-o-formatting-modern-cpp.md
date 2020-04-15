---
title: Formatowanie ciągów i we/wy (Modern C++)
description: Opcje dla sformatowanych ciągów we/wy dostępne w nowoczesnym języku C++.
ms.date: 05/30/2019
ms.topic: conceptual
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
ms.openlocfilehash: a3fc93b0baf414759eb50c787c4057fb85dcb370
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375773"
---
# <a name="string-and-io-formatting-modern-c"></a>Formatowanie ciągów i we/wy (Modern C++)

C++ [ \<iostream>](../standard-library/iostream.md) klas, funkcji i operatorów obsługuje sformatowany ciąg We/Wy. Na przykład poniższy kod pokazuje, jak ustawić `cout` formatowanie liczby całkowitej do danych wyjściowych w szesnastkowej. Po pierwsze, zapisuje bieżący stan, aby zresetować go `cout`później, ponieważ po przejściu stanu formatu do , pozostaje w ten sposób, aż do zmiany. Nie dotyczy tylko jednego wiersza kodu.

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

Takie podejście jest bezpieczne dla typu i rozszerzalne, ale jest również złożone i pełne.

## <a name="alternative-format-options"></a>Alternatywne opcje formatu

Alternatywnie można użyć `Boost.Format` z bibliotek Boost C++, nawet jeśli jest to niestandardowe. Możesz pobrać dowolną bibliotekę Boost ze strony [Boost.](https://www.boost.org/)

Niektóre zalety `Boost.Format` to:

- Bezpieczne: Type-safe i zgłasza wyjątek dla błędów, na przykład specyfikacji zbyt mało lub zbyt wiele elementów.

- Rozszerzalny: Działa dla każdego typu, który może być przesyłany strumieniowo.

- Wygoda: Standardowe POSIX i podobne ciągi formatu.

Chociaż `Boost.Format` jest zbudowany na C++ [ \<iostream>](../standard-library/iostream-programming.md) obiektów, które są bezpieczne i rozszerzalne, nie są one zoptymalizowane pod względem wydajności. Jeśli potrzebujesz optymalizacji wydajności, należy wziąć pod uwagę [C printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) i [sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), które są szybkie i łatwe w użyciu. Nie są one jednak rozszerzalne ani bezpieczne przed lukami w zabezpieczeniach. (Istnieją bezpieczne wersje, ale ponoszą niewielką karę za wydajność. Aby uzyskać więcej informacji, zobacz [printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md) i [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)).

Poniższy kod przedstawia niektóre funkcje formatowania Boost.

```cpp
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );
    // s contains "hello hello world"

    for( auto i = 0; i < names.size(); ++i )
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321
```

## <a name="see-also"></a>Zobacz też

[Witamy z powrotem w języku C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Odwołanie do języka języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka języka C++](../standard-library/cpp-standard-library-reference.md)<br/>
[\<>iostream](../standard-library/iostream.md)<br/>
[\<limity>](../standard-library/limits.md)<br/>
[\<>iomanip](../standard-library/iomanip.md)
