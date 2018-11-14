---
title: Ciągów i we / wy formatowanie (Modern C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
ms.openlocfilehash: 816eb71dae011f853a6e7ade1a1a2a8144a457c5
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326189"
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

- Bezpieczny: Typ bezpieczny i zgłasza wyjątek dla błędów — na przykład Specyfikacja zbyt małej lub zbyt wiele elementów.

- Rozszerzalne: Działa dowolny typ, który może być przesyłany strumieniowo.

- Wygoda: Standard Posix i podobne ciągi formatów.

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

[Witamy z powrotem w C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)<br/>
[\<iostream>](../standard-library/iostream.md)<br/>
[\<limits>](../standard-library/limits.md)<br/>
[\<iomanip >](../standard-library/iomanip.md)