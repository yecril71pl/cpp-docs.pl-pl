---
title: Ciągów i we / wy formatowanie (Modern C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
ms.openlocfilehash: c051a7d70042456d30bee0ebb2b362c5d05b8e37
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266923"
---
# <a name="string-and-io-formatting-modern-c"></a>Formatowanie ciągów i we/wy (Modern C++)

C++ [iostreams](../standard-library/iostream.md) są w stanie sformatować ciąg we/wy. Na przykład poniższy kod przedstawia sposób ustawiania cout do formatowania liczby całkowitej w danych wyjściowych w formacie szesnastkowym, najpierw zapisując stan bieżący, a następnie później, ponieważ gdy stan formatowania zostanie przekazany do cout, pozostaje on w ten sposób, dopóki zmianie, nie tylko dla jednej linii kodu.

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

Może to być zbyt kłopotliwe w wielu przypadkach. Jako alternatywę można użyć Boost.Format z biblioteki Boost C++, nawet jeśli nie jest to standardowe. Możesz pobrać każdą bibliotekę Boost z [Boost](http://www.boost.org/) witryny sieci Web.

Niektóre zalety Boost.Format są:

- Bezpieczny: Bezpieczny i zgłasza wyjątek dla błędów — na przykład Specyfikacja zbyt małej lub zbyt wiele elementów.

- Rozszerzalne: Działa w przypadku dowolnego typu, który może być przesyłany strumieniowo.

- Wygodne: Standard Posix i podobne ciągi formatów.

Chociaż Boost.Format jest zbudowany na C++ [iostreams](../standard-library/iostream-programming.md), które są bezpieczne i rozszerzalne, nie są zoptymalizowane pod kątem wydajności. Jeśli potrzebujesz, aby zoptymalizować wydajność, należy wziąć pod uwagę C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) i [sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), które są szybkie i łatwe w użyciu. Jednak nie są one rozszerzalne ani pozbawione luk w zabezpieczeniach. (Istnieją wersje bezpieczne, ale mogą spowodować zmniejszenie wydajności niewielkie. Aby uzyskać więcej informacji, zobacz [printf_s, _printf_s_l —, wprintf_s —, _wprintf_s_l —](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md) i [sprintf_s —, _sprintf_s_l —, swprintf_s —, _swprintf_s_l —](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)).

Poniższy kod ilustruje część zwiększenia funkcji formatowania.

```cpp
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );
    // s contains "hello hello world"

    for( auto i = 0; i < names.size(); ++i )
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321
```

## <a name="see-also"></a>Zobacz także

[Witaj z powrotem w języku C++ (Modern C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)<br/>
[\<iostream>](../standard-library/iostream.md)<br/>
[\<limits>](../standard-library/limits.md)<br/>
[\<iomanip >](../standard-library/iomanip.md)
