---
title: complex&lt;double&gt;
ms.date: 11/04/2016
f1_keywords:
- complex/std::complex<double>
helpviewer_keywords:
- complex<double> function
ms.assetid: 0d0b9d2a-9b9b-410b-82a0-86b6df127e47
ms.openlocfilehash: 565a2e6b5ee4eb495cb4cc3241bb8ce72de538a2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453151"
---
# <a name="complexltdoublegt"></a>complex&lt;double&gt;

Opisuje obiekt, który przechowuje uporządkowaną parę obiektów typu **Double**, pierwszej reprezentującej rzeczywistą część liczby zespolonej, a drugą reprezentującą część urojoną.

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
// rest same as template class complex
};
```

### <a name="parameters"></a>Parametry

*RealVal*\
Wartość typu **Double** dla rzeczywistej części konstruowanej liczby zespolonej.

*ImagVal*\
Wartość typu **Double** dla części urojonej konstruowanej liczby zespolonej.

*complexNum*\
Liczba zespolona typu **zmiennoprzecinkowego** lub typu **Long podwójnie** , których elementy rzeczywiste i urojone są używane do zainicjowania złożonej liczby typu **Double** .

## <a name="return-value"></a>Wartość zwracana

Złożona liczba typu **Double**.

## <a name="remarks"></a>Uwagi

Jawna specjalizacja klasy szablonu złożonej do złożonej klasy typu **Double** różni się od klasy szablonu tylko w konstruktorach, które definiuje. Konwersja z wartości **zmiennoprzecinkowej** na **Double** może być niejawna, ale konwersja z typu **Long Double** do **Double** musi być **jawna**. Użycie jawnych  reguł inicjacji z konwersją typu przy użyciu składni przypisania.

Aby uzyskać więcej informacji na temat klasy `complex`szablonu, zobacz [Klasa złożona](../standard-library/complex-class.md). Aby uzyskać listę elementów członkowskich klasy `complex`szablonu, zobacz.

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

**Nagłówek**: \<złożony >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Klasa złożona](../standard-library/complex-class.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
