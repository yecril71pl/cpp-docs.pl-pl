---
title: złożona &lt; Podwójna&gt;
ms.date: 11/04/2016
f1_keywords:
- complex/std::complex<double>
helpviewer_keywords:
- complex<double> function
ms.assetid: 0d0b9d2a-9b9b-410b-82a0-86b6df127e47
ms.openlocfilehash: b9bf4780dd78800653804762301b36ff6bb30a92
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230081"
---
# <a name="complexltdoublegt"></a>złożona &lt; Podwójna&gt;

Opisuje obiekt, który przechowuje uporządkowaną parę obiektów typu **`double`** , pierwszą reprezentującą rzeczywistą część liczby zespolonej i drugą reprezentującą część urojoną.

## <a name="syntax"></a>Składnia

```cpp
template <>
class complex<double> {
public:
    constexpr complex(
    double RealVal = 0,
    double ImagVal = 0);

constexpr complex(const complex<double>& complexNum);

constexpr explicit complex(const complex<long double>& complexNum);
// rest same as class template complex
};
```

### <a name="parameters"></a>Parametry

*RealVal*\
Wartość typu **`double`** dla rzeczywistej części konstruowanej liczby zespolonej.

*ImagVal*\
Wartość typu **`double`** dla części urojonej konstruowanej liczby zespolonej.

*complexNum*\
Liczba złożona typu **`float`** lub typu, **`long double`** którego elementy rzeczywiste i urojone są używane do zainicjowania złożonej liczby **`double`** konstruowanych typów.

## <a name="return-value"></a>Wartość zwracana

Złożona liczba typu **`double`** .

## <a name="remarks"></a>Uwagi

Jawna specjalizacja szablonu klasy złożonego do złożonej klasy typu **`double`** różni się od szablonu klasy tylko w konstruktorach, które definiuje. Konwersja z **`float`** do na **`double`** może być niejawna, ale konwersja z **`long double`** do na **`double`** jest wymagana **`explicit`** . Użycie **`explicit`** reguł inicjacji z konwersją typu przy użyciu składni przypisywania.

Aby uzyskać więcej informacji na temat szablonu klasy `complex` , zobacz [Klasa złożona](../standard-library/complex-class.md). Aby uzyskać listę elementów członkowskich szablonu klasy `complex` , zobacz.

## <a name="example"></a>Przykład

```cpp
// complex_comp_dbl.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // The first constructor specifies real & imaginary parts
   complex <double> c1 ( 4.0 , 5.0 );
   cout << "Specifying initial real & imaginary parts,\n"
        << "as type double gives c1 = " << c1 << endl;

   // The second constructor initializes values of the real &
   // imaginary parts using those of complex number of type float
   complex <float> c2float ( 4.0 , 5.0 );
   complex <double> c2double ( c2float );
   cout << "Implicit conversion from type float to type double,"
        << endl << "gives c2double = " << c2double << endl;

   // The third constructor initializes values of the real &
   // imaginary parts using those of a complex number
   // of type long double
   complex <long double> c3longdouble ( 4.0 , 5.0 );
   complex <double> c3double ( c3longdouble );
   cout << "Explicit conversion from type float to type double,"
        << endl << "gives c3longdouble = " << c3longdouble << endl;

   // The modulus and argument of a complex number can be recovered
   double absc3 = abs ( c3longdouble );
   double argc3 = arg ( c3longdouble );
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "
        << absc3 << endl;
   cout << "Argument of c3 is recovered from c3 using:" << endl
        << "arg ( c3 ) = " << argc3 << " radians, which is "
        << argc3 * 180 / pi << " degrees." << endl;
}
/* Output:
Specifying initial real & imaginary parts,
as type double gives c1 = (4,5)
Implicit conversion from type float to type double,
gives c2double = (4,5)
Explicit conversion from type float to type double,
gives c3longdouble = (4,5)
The modulus of c3 is recovered from c3 using: abs ( c3 ) = 6.40312
Argument of c3 is recovered from c3 using:
arg ( c3 ) = 0.896055 radians, which is 51.3402 degrees.
*/
```

## <a name="requirements"></a>Wymagania

**Nagłówek**:\<complex>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Klasa złożona](../standard-library/complex-class.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
