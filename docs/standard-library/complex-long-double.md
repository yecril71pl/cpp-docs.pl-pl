---
title: złożone &lt; Long Double&gt;
ms.date: 11/04/2016
f1_keywords:
- std::complex<long double>
- complex<long double>
- std.complex<long double>
helpviewer_keywords:
- complex<long double> function
ms.assetid: 37591991-b385-46e9-b727-d534dbc10432
ms.openlocfilehash: 73027ba76d608424b1a6da346e861b10c66989fe
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228391"
---
# <a name="complexltlong-doublegt"></a>złożone &lt; Long Double&gt;

Ten jawnie wyspecjalizowany szablon klasy opisuje obiekt, który przechowuje uporządkowaną parę obiektów, obu typów **`long double`** , pierwsze reprezentujące rzeczywistą część liczby zespolonej i drugą reprezentującą część urojoną.

## <a name="syntax"></a>Składnia

```cpp
template <>
class complex<long double> {
public:
    constexpr complex(
    long double _RealVal = 0,
    long double _ImagVal = 0);

complex(
    constexpr complex<long double>& complexNum);

// rest same as class template complex
};
```

### <a name="parameters"></a>Parametry

*_RealVal*\
Wartość typu **`long double`** dla rzeczywistej części konstruowanej liczby zespolonej.

*_ImagVal*\
Wartość typu **`long double`** dla części urojonej konstruowanej liczby zespolonej.

*complexNum*\
Liczba złożona typu **`double`** lub typu, **`float`** którego elementy rzeczywiste i urojone są używane do zainicjowania złożonej liczby **`long double`** konstruowanych typów.

## <a name="return-value"></a>Wartość zwracana

Złożona liczba typu **`long double`** .

## <a name="remarks"></a>Uwagi

Jawna specjalizacja szablonu klasy `complex` do złożonej klasy typu **`long double`** różni się od szablonu klasy tylko w konstruktorach, które definiuje. Konwersja z **`long double`** do na **`float`** może być niejawna, ale konwersja z **`double`** do na **`long double`** jest wymagana **`explicit`** . Użycie **`explicit`** reguł inicjacji z konwersją typu przy użyciu składni przypisywania.

Aby uzyskać więcej informacji na temat szablonu klasy `complex` i jego elementów członkowskich, zobacz [Klasa złożona](../standard-library/complex-class.md).

**Specyficzne dla firmy Microsoft**: **`long double`** **`double`** typy i mają tę samą reprezentację, ale są różnymi typami. Aby uzyskać więcej informacji, zobacz [typy wbudowane](../cpp/fundamental-types-cpp.md).

## <a name="example"></a>Przykład

```cpp
// complex_comp_ld.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
    using namespace std;
    double pi = 3.14159265359;

    // The first constructor specifies real & imaginary parts
    complex<long double> c1( 4.0 , 5.0 );
    cout << "Specifying initial real & imaginary parts,\n"
        << " as type float gives c1 = " << c1 << endl;

    // The second constructor initializes values of the real &
    // imaginary parts using those of complex number of type float
    complex<float> c2float( 1.0 , 3.0 );
    complex<long double> c2longdouble ( c2float );
    cout << "Implicit conversion from type float to type long double,"
        << "\n gives c2longdouble = " << c2longdouble << endl;

    // The third constructor initializes values of the real &
    // imaginary parts using those of a complex number
    // of type double
    complex<double> c3double( 3.0 , 4.0 );
    complex<long double> c3longdouble( c3double );
    cout << "Implicit conversion from type long double to type float,"
        << "\n gives c3longdouble = " << c3longdouble << endl;

    // The modulus and argument of a complex number can be recovered
    double absc3 = abs( c3longdouble );
    double argc3 = arg( c3longdouble );
    cout << "The modulus of c3 is recovered from c3 using: abs( c3 ) = "
        << absc3 << endl;
    cout << "Argument of c3 is recovered from c3 using:\n arg( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
```

```Output
Specifying initial real & imaginary parts,
as type float gives c1 = (4,5)
Implicit conversion from type float to type long double,
gives c2longdouble = (1,3)
Implicit conversion from type long double to type float,
gives c3longdouble = (3,4)
The modulus of c3 is recovered from c3 using: abs( c3 ) = 5
Argument of c3 is recovered from c3 using:
arg( c3 ) = 0.927295 radians, which is 53.1301 degrees.
```

## <a name="requirements"></a>Wymagania

**Nagłówek**:\<complex>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Klasa złożona](../standard-library/complex-class.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
