---
title: złożone&lt;typu long double&gt; | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- std::complex<long double>
- complex<long double>
- std.complex<long double>
dev_langs:
- C++
helpviewer_keywords:
- complex<long double> function
ms.assetid: 37591991-b385-46e9-b727-d534dbc10432
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 92b0a7c9ae697bc28ad9fe3bd89d37f22d7a8cdc
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313471"
---
# <a name="complexltlong-doublegt"></a>złożone&lt;typu long double&gt;

Opisuje obiekt, który przechowuje uporządkowana para obiektów zarówno typu **typu long double**, najpierw reprezentujących część liczby zespolonej, a druga rzeczywista reprezentujący urojone części.

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
// rest same as template class complex
};
```

### <a name="parameters"></a>Parametry

*_RealVal*<br/>
Wartość typu **typu long double** rzeczywistych część liczby zespolonej budowany.

*_ImagVal*<br/>
Wartość typu **typu long double** dla urojone części liczb zespolonych budowany.

*complexNum*<br/>
Liczby zespolonej typu **double** lub typu **float** którego rzeczywiste i urojone części są stosowane do inicjalizacji liczby zespolonej typu **typu long double** budowany.

## <a name="return-value"></a>Wartość zwracana

Liczby zespolonej typu **typu long double**.

## <a name="remarks"></a>Uwagi

Jawna specjalizacja szablonu klasy złożone i klasy złożone typu **typu long double** różni się od klasy szablonu, tylko w konstruktorach definiuje. Konwersja z **typu long double** do **float** może być niejawne, ale konwersja z **double** do **typu long double** jest wymagana jako **jawne**. Korzystanie z **jawne** wyklucza rozpoczęcia z konwersję typu przy użyciu składni przypisania.

Aby uzyskać więcej informacji na temat klasy szablonu `complex`, zobacz [complex — klasa](../standard-library/complex-class.md). Aby uzyskać listę elementów członkowskich klasy szablonu `complex`, zobacz.

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
   complex <long double> c1 ( 4.0 , 5.0 );
   cout << "Specifying initial real & imaginary parts,\n"
        << " as type float gives c1 = " << c1 << endl;

   // The second constructor initializes values of the real &
   // imaginary parts using those of complex number of type float
   complex <float> c2float ( 1.0 , 3.0 );
   complex <long double> c2longdouble ( c2float );
   cout << "Implicit conversion from type float to type long double,"
        << "\n gives c2longdouble = " << c2longdouble << endl;

   // The third constructor initializes values of the real &
   // imaginary parts using those of a complex number
   // of type double
   complex <double> c3double ( 3.0 , 4.0 );
   complex <long double> c3longdouble ( c3double );
   cout << "Implicit conversion from type long double to type float,"
        << "\n gives c3longdouble = " << c3longdouble << endl;

   // The modulus and argument of a complex number can be recovered
   double absc3 = abs ( c3longdouble );
   double argc3 = arg ( c3longdouble );
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "
        << absc3 << endl;
   cout << "Argument of c3 is recovered from c3 using:\n arg ( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
/* Output:
Specifying initial real & imaginary parts,
as type float gives c1 = (4,5)
Implicit conversion from type float to type long double,
gives c2longdouble = (1,3)
Implicit conversion from type long double to type float,
gives c3longdouble = (3,4)
The modulus of c3 is recovered from c3 using: abs ( c3 ) = 5
Argument of c3 is recovered from c3 using:
arg ( c3 ) = 0.927295 radians, which is 53.1301 degrees.
*/
```

## <a name="requirements"></a>Wymagania

**Nagłówek**: \<złożonych >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[complex, klasa](../standard-library/complex-class.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
