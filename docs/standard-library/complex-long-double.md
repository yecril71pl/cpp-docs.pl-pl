---
title: złożone&lt;long double&gt;
ms.date: 11/04/2016
f1_keywords:
- std::complex<long double>
- complex<long double>
- std.complex<long double>
helpviewer_keywords:
- complex<long double> function
ms.assetid: 37591991-b385-46e9-b727-d534dbc10432
ms.openlocfilehash: 5de4fc2305ef2ac6e523dcb02782455245b99429
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302344"
---
# <a name="complexltlong-doublegt"></a>złożone&lt;long double&gt;

Ten jawnie wyspecjalizowany szablon klasy opisuje obiekt, który przechowuje uporządkowaną parę obiektów, obie typu **Long Double**, pierwsze reprezentujące rzeczywistą część liczby zespolonej i sekundę reprezentującą część urojoną.

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
Wartość typu **Long Double** dla rzeczywistej części konstruowanej liczby zespolonej.

*_ImagVal*\
Wartość typu **Long Double** dla części urojonej konstruowanej liczby zespolonej.

*complexNum*\
Liczba zespolona typu **Double** lub typu **zmiennoprzecinkowego** , których elementy rzeczywiste i urojone są używane do zainicjowania złożonej liczby typu **Long Double** .

## <a name="return-value"></a>Wartość zwrócona

Złożona liczba typu **Long Double**.

## <a name="remarks"></a>Uwagi

Jawna specjalizacja szablonu klasy `complex` do złożonej klasy typu **Long Double** różni się od szablonu klasy tylko w konstruktorach, które definiuje. Konwersja z **Long Double** na **zmiennoprzecinkowe** może być niejawna, ale konwersja z **podwójnej** do **Long Double** musi być **jawna**. Użycie **jawnych** reguł inicjacji z konwersją typu przy użyciu składni przypisania.

Aby uzyskać więcej informacji na temat szablonu klasy `complex` i jego składowych, zobacz [Klasa złożona](../standard-library/complex-class.md).

**Specyficzne dla firmy Microsoft**: typy **Long Double** i **Double** mają tę samą reprezentację, ale są to różne typy. Aby uzyskać więcej informacji, zobacz [typy wbudowane](../cpp/fundamental-types-cpp.md).

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

**Nagłówek**: \<złożone >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Klasa złożona](../standard-library/complex-class.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
