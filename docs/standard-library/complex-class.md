---
title: COMPLEX — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- complex/std::complex::value_type
- complex/std::complex::imag
- complex/std::complex::real
dev_langs:
- C++
helpviewer_keywords:
- std::complex [C++], value_type
- std::complex [C++], imag
- std::complex [C++], real
ms.assetid: d6492e1c-5eba-4bc5-835b-2a88001a5868
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f31d2e0fe0a58d2b1de4196bd1125c842731fb42
ms.sourcegitcommit: 8c2de32e96c84d0147af3cce1e89e4f28707ff12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/26/2018
ms.locfileid: "50143708"
---
# <a name="complex-class"></a>complex — Klasa

Klasa szablonu opisuje obiekt, który przechowuje dwa obiekty typu `Type`, jedna reprezentuje rzeczywistą część liczby zespolonej i jedną, która reprezentuje urojone części.

## <a name="syntax"></a>Składnia

```cpp
template <class Type>
class complex
```

## <a name="remarks"></a>Uwagi

Obiekt klasy `Type`:

- Ma publicznego konstruktora domyślnego, destruktor, Konstruktor kopiujący i operator przypisania z konwencjonalnych zachowanie.

- Liczba całkowita lub zmiennoprzecinkową wartości można przypisać lub wpisz Rzutowanie na takie wartości, z zachowaniem konwencjonalnych.

- Definiuje operatory arytmetyczne i funkcje matematyczne, zgodnie z potrzebami, które są zdefiniowane dla typów zmiennoprzecinkowych za pomocą konwencjonalnych zachowanie.

W szczególności nie subtelne może różnice między konstrukcja kopiowania i konstruowania domyślne następuje przypisanie. Brak operacji na obiekty klasy `Type` może zgłaszać wyjątki.

Jawne specjalizacje szablonu klasy złożone dla istnieją trzy typy zmiennoprzecinkowe. W tej implementacji wartość innego typu `Type` jest rzutowanie typu do **double** rzeczywiste obliczenia z **double** wynik przypisana z powrotem do przechowywany obiekt typu `Type`.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[complex](#complex)|Tworzy liczby zespolonej z określonym rzeczywiste i urojone części lub jako kopię inne liczby zespolonej.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[value_type](#value_type)|Typ, który reprezentuje typ danych używany do reprezentowania rzeczywiste i urojone części liczb zespolonych.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[imag](#imag)|Wyodrębnia urojone części liczby zespolonej.|
|[rzeczywiste](#real)|Wyodrębnia rzeczywisty składnik liczby zespolonej.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator*=](#op_star_eq)|Mnoży docelowej liczby zespolonej przez współczynnik, który może być złożonym procesem, lub być tego samego typu są rzeczywiste i urojone części liczb zespolonych.|
|[operator+=](#op_add_eq)|Dodaje numer docelowej liczby zespolonej, w przypadku, gdy liczba dodawane mogą być skomplikowane, lub tego samego typu co są rzeczywiste i urojone części liczb zespolonych, do którego zostanie dodany.|
|[operator-=](#operator-_eq)|Odejmuje liczbę od liczby zespolonej docelowego, w przypadku, gdy liczba odejmowana mogą być skomplikowane, lub tego samego typu co są rzeczywiste i urojone części liczb zespolonych, do którego zostanie dodany.|
|[operator / =](#op_div_eq)|Dzieli docelowej liczby zespolonej przez dzielnik, która może być złożonym procesem lub być tego samego typu są rzeczywiste i urojone części liczb zespolonych.|
|[operator=](#op_eq)|Przypisuje numer docelowej liczby zespolonej, gdzie mogą być skomplikowane numer przypisany lub tego samego typu co są rzeczywiste i urojone części liczb zespolonych, które są przypisane.|

## <a name="requirements"></a>Wymagania

**Nagłówek**: \<złożonych >

**Namespace:** standardowe

## <a name="complex"></a>  COMPLEX::Complex

Tworzy liczby zespolonej z określonym rzeczywiste i urojone części lub jako kopię inne liczby zespolonej.

```cpp
constexpr complex(
    const T& _RealVal = 0,
    const T& _ImagVal = 0);

template <class Other>
constexpr complex(
    const complex<Other>& complexNum);
```

### <a name="parameters"></a>Parametry

*_RealVal*<br/>
Wartość rzeczywistego części, używane do zainicjowania liczby zespolonej budowany.

*_ImagVal*<br/>
Wartość urojone części, używane do zainicjowania liczby zespolonej budowany.

*complexNum*<br/>
Liczby zespolonej, którego rzeczywiste i urojone części są stosowane do inicjalizacji liczby zespolonej budowany.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje przechowywany rzeczywiste należą do  *\_RealVal* i przechowywanych urojone części do  *\_Imagval*. Drugi Konstruktor inicjuje przechowywany rzeczywiste należą do `complexNum.real()` i przechowywanych urojone części do `complexNum.imag()`.

W tej implementacji, jeśli translator nie obsługuje funkcji szablonów elementów członkowskich, szablon:

```cpp
template <class Other>
complex(const complex<Other>& right);
```

zostaje zastąpiona opcją:

```
complex(const complex& right);
```

jest to Konstruktor kopiujący.

### <a name="example"></a>Przykład

```cpp
// complex_complex.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
    using namespace std;
    double pi = 3.14159265359;

    // The first constructor specifies real & imaginary parts
    complex<double> c1( 4.0 , 5.0 );
    cout << "Specifying initial real & imaginary parts,"
        << "c1 = " << c1 << endl;

    // The second constructor initializes values of the real &
    // imaginary parts using those of another complex number
    complex<double> c2( c1 );
    cout << "Initializing with the real and imaginary parts of c1,"
        << " c2 = " << c2 << endl;

    // Complex numbers can be initialized in polar form
    // but will be stored in Cartesian form
    complex<double> c3( polar( sqrt( (double)8 ) , pi / 4 ) );
    cout << "c3 = polar( sqrt( 8 ) , pi / 4 ) = " << c3 << endl;

    // The modulus and argument of a complex number can be recovered
    double absc3 = abs( c3 );
    double argc3 = arg( c3 );
    cout << "The modulus of c3 is recovered from c3 using: abs( c3 ) = "
        << absc3 << endl;
    cout << "Argument of c3 is recovered from c3 using:\n arg( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
```

## <a name="imag"></a>  COMPLEX::imag

Wyodrębnia urojone części liczby zespolonej.

```cpp
T imag() const;

T imag(const T& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Liczby zespolonej, którego urojone wartość do wyodrębnienia.

### <a name="return-value"></a>Wartość zwracana

Urojone części liczb zespolonych.

### <a name="remarks"></a>Uwagi

Dla liczby zespolonej *+ bi*, urojone części lub składnik jest *Im(a + bi) = b*.

### <a name="example"></a>Przykład

```cpp
// complex_imag.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
    using namespace std;

    complex<double> c1( 4.0 , 3.0 );
    cout << "The complex number c1 = " << c1 << endl;

    double dr1 = c1.real();
    cout << "The real part of c1 is c1.real() = "
        << dr1 << "." << endl;

    double di1 = c1.imag();
    cout << "The imaginary part of c1 is c1.imag() = "
        << di1 << "." << endl;
}
```

```Output
The complex number c1 = (4,3)
The real part of c1 is c1.real() = 4.
The imaginary part of c1 is c1.imag() = 3.
```

## <a name="op_star_eq"></a>  COMPLEX::operator * =

Mnoży docelowej liczby zespolonej przez współczynnik, który może być złożonym procesem, lub być tego samego typu są rzeczywiste i urojone części liczb zespolonych.

```cpp
template <class Other>
complex& operator*=(const complex<Other>& right);

complex<Type>& operator*=(const Type& right);

complex<Type>& operator*=(const complex<Type>& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Liczbą lub liczbą, która jest tego samego typu co parametr liczby zespolonej docelowego.

### <a name="return-value"></a>Wartość zwracana

Liczby zespolonej, który ma zostać pomnożona przez numer, który został określony jako parametr.

### <a name="remarks"></a>Uwagi

Operacji jest przeciążona, tak aby proste operacje arytmetyczne, mogą być wykonywane bez konwersji danych do określonego formatu.

### <a name="example"></a>Przykład

```cpp
// complex_op_me.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main()
{
    using namespace std;
    double pi = 3.14159265359;

    // Example of the first member function
    // type complex<double> multiplied by type complex<double>
    complex<double> cl1( polar ( 3.0 , pi / 6 ) );
    complex<double> cr1( polar ( 2.0 , pi / 3 ) );
    cout << "The left-side complex number is cl1 = " << cl1 << endl;
    cout << "The right-side complex number is cr1 = " << cr1 << endl;

    complex<double> cs1 = cl1 * cr1;
    cout << "Quotient of two complex numbers is: cs1 = cl1 * cr1 = "
        << cs1 << endl;

    // This is equivalent to the following operation
    cl1 *= cr1;
    cout << "Quotient of two complex numbers is also: cl1 *= cr1 = "
        << cl1 << endl;

    double abscl1 = abs ( cl1 );
    double argcl1 = arg ( cl1 );
    cout << "The modulus of cl1 is: " << abscl1 << endl;
    cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

    // Example of the second member function
    // type complex<double> multiplied by type double
    complex<double> cl2 ( polar ( 3.0 , pi / 6 ) );
    double cr2 = 5.0;
    cout << "The left-side complex number is cl2 = " << cl2 << endl;
    cout << "The right-side complex number is cr2 = " << cr2 << endl;

    complex<double> cs2 = cl2 * cr2;
    cout << "Quotient of two complex numbers is: cs2 = cl2 * cr2 = "
        << cs2 << endl;

    // This is equivalent to the following operation
    cl2 *= cr2;
    cout << "Quotient of two complex numbers is also: cl2 *= cr2 = "
        << cl2 << endl;

    double abscl2 = abs ( cl2 );
    double argcl2 = arg ( cl2 );
    cout << "The modulus of cl2 is: " << abscl2 << endl;
    cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl;
}
```

## <a name="op_add_eq"></a>  COMPLEX::operator +=

Dodaje numer docelowej liczby zespolonej, w przypadku, gdy liczba dodawane mogą być skomplikowane, lub tego samego typu co są rzeczywiste i urojone części liczb zespolonych, do którego zostanie dodany.

```cpp
template <class Other>
complex<Type>& operator+=(const complex<Other>& right);

complex<Type>& operator+=(const Type& right);

complex<Type>& operator+=(const complex<Type>& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Liczbą lub liczbą, która jest tego samego typu co parametr liczby zespolonej docelowego.

### <a name="return-value"></a>Wartość zwracana

Liczby zespolonej, który miał numer, który został określony jako parametr dodany.

### <a name="remarks"></a>Uwagi

Operacji jest przeciążona, tak aby proste operacje arytmetyczne, mogą być wykonywane bez konwersji danych do określonego formatu.

### <a name="example"></a>Przykład

```cpp
// complex_op_pe.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> added to type complex<double>
   complex<double> cl1( 3.0 , 4.0 );
   complex<double> cr1( 2.0 , -1.0 );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex<double> cs1 = cl1 + cr1;
   cout << "The sum of the two complex numbers is: cs1 = cl1 + cr1 = "
        << cs1 << endl;

   // This is equivalent to the following operation
   cl1 += cr1;
   cout << "The complex number cr1 added to the complex number cl1 is:"
        << "\n cl1 += cr1 = " << cl1 << endl;

   double abscl1 = abs( cl1 );
   double argcl1 = arg( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type double added to type complex<double>
   complex<double> cl2( -2 , 4 );
   double cr2 =5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex<double> cs2 = cl2 + cr2;
   cout << "The sum of the two complex numbers is: cs2 = cl2 + cr2 = "
        << cs2 << endl;

   // This is equivalent to the following operation
   cl2 += cr2;
   cout << "The complex number cr2 added to the complex number cl2 is:"
        << "\n cl2 += cr2 = " << cl2 << endl;

   double abscl2 = abs( cl2 );
   double argcl2 = arg( cl2 );
   cout << "The modulus of cl2 is: " << abscl2 << endl;
   cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
The left-side complex number is cl1 = (3,4)
The right-side complex number is cr1 = (2,-1)
The sum of the two complex numbers is: cs1 = cl1 + cr1 = (5,3)
The complex number cr1 added to the complex number cl1 is:
cl1 += cr1 = (5,3)
The modulus of cl1 is: 5.83095
The argument of cl1 is: 0.54042 radians, which is 30.9638 degrees.

The left-side complex number is cl2 = (-2,4)
The right-side complex number is cr2 = 5
The sum of the two complex numbers is: cs2 = cl2 + cr2 = (3,4)
The complex number cr2 added to the complex number cl2 is:
cl2 += cr2 = (3,4)
The modulus of cl2 is: 5
The argument of cl2 is: 0.927295 radians, which is 53.1301 degrees.
```

## <a name="complex__operator-_eq"></a>  COMPLEX::operator-=

Odejmuje liczbę od liczby zespolonej docelowego, w przypadku, gdy liczba odejmowana mogą być skomplikowane, lub tego samego typu co są rzeczywiste i urojone części liczb zespolonych, do którego zostanie dodany.

```cpp
template <class Other>
complex<Type>& operator-=(const complex<Other>& complexNum);

complex<Type>& operator-=(const Type& _RealPart);

complex<Type>& operator-=(const complex<Type>& complexNum);
```

### <a name="parameters"></a>Parametry

*complexNum*<br/>
Liczby zespolonej odjęta od liczby zespolonej docelowego.

*_RealPart*<br/>
Liczba rzeczywista jest odejmowana od liczby zespolonej docelowego.

### <a name="return-value"></a>Wartość zwracana

Liczby zespolonej, który miał numer, który został określony jako parametr odejmowany od niego.

### <a name="remarks"></a>Uwagi

Operacji jest przeciążona, tak aby proste operacje arytmetyczne, mogą być wykonywane bez konwersji danych do określonego formatu.

### <a name="example"></a>Przykład

```cpp
// complex_op_se.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> subtracted from type complex<double>
   complex<double> cl1( 3.0 , 4.0 );
   complex<double> cr1( 2.0 , -1.0 );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex<double> cs1 = cl1 - cr1;
   cout << "The difference between the two complex numbers is:"
        << "\n cs1 = cl1 - cr1 = " << cs1 << endl;

   // This is equivalent to the following operation
   cl1 -= cr1;
   cout << "Complex number cr1 subtracted from complex number cl1 is:"
        << "\n cl1 -= cr1 = " << cl1 << endl;

   double abscl1 = abs( cl1 );
   double argcl1 = arg( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type double subtracted from type complex<double>
   complex<double> cl2( 2.0 , 4.0 );
   double cr2 = 5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex<double> cs2 = cl2 - cr2;
   cout << "The difference between the two complex numbers is:"
        << "\n cs2 = cl2 - cr2 = " << cs2 << endl;

   // This is equivalent to the following operation
   cl2  -= cr2;
   cout << "Complex number cr2 subtracted from complex number cl2 is:"
        << "\n cl2 -= cr2 = " << cl2 << endl;

   double abscl2 = abs( cl2 );
   double argcl2 = arg( cl2 );
   cout << "The modulus of cl2 is: " << abscl2 << endl;
   cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
The left-side complex number is cl1 = (3,4)
The right-side complex number is cr1 = (2,-1)
The difference between the two complex numbers is:
cs1 = cl1 - cr1 = (1,5)
Complex number cr1 subtracted from complex number cl1 is:
cl1 -= cr1 = (1,5)
The modulus of cl1 is: 5.09902
The argument of cl1 is: 1.3734 radians, which is 78.6901 degrees.

The left-side complex number is cl2 = (2,4)
The right-side complex number is cr2 = 5
The difference between the two complex numbers is:
cs2 = cl2 - cr2 = (-3,4)
Complex number cr2 subtracted from complex number cl2 is:
cl2 -= cr2 = (-3,4)
The modulus of cl2 is: 5
The argument of cl2 is: 2.2143 radians, which is 126.87 degrees.
```

## <a name="op_div_eq"></a>  COMPLEX::operator / =

Dzieli docelowej liczby zespolonej przez dzielnik, która może być złożonym procesem lub być tego samego typu są rzeczywiste i urojone części liczb zespolonych.

```cpp
template <class Other>
complex<Type>& operator/=(const complex<Other>& complexNum);

complex<Type>& operator/=(const Type& _RealPart);

complex<Type>& operator/=(const complex<Type>& complexNum);
```

### <a name="parameters"></a>Parametry

*complexNum*<br/>
Liczby zespolonej odjęta od liczby zespolonej docelowego.

*_RealPart*<br/>
Liczba rzeczywista jest odejmowana od liczby zespolonej docelowego.

### <a name="return-value"></a>Wartość zwracana

Liczby zespolonej, który został podzielony przez liczbę, określony jako parametr.

### <a name="remarks"></a>Uwagi

Operacji jest przeciążona, tak aby proste operacje arytmetyczne, mogą być wykonywane bez konwersji danych do określonego formatu.

### <a name="example"></a>Przykład

```cpp
// complex_op_de.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> divided by type complex<double>
   complex<double> cl1( polar (3.0 , pi / 6 ) );
   complex<double> cr1( polar (2.0 , pi / 3 ) );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex<double> cs1 = cl1 / cr1;
   cout << "The quotient of the two complex numbers is: cs1 = cl1 /cr1 = "
        << cs1 << endl;

   // This is equivalent to the following operation
   cl1 /= cr1;
   cout << "Quotient of two complex numbers is also: cl1 /= cr1 = "
        << cl1 << endl;

   double abscl1 = abs( cl1 );
   double argcl1 = arg( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type complex<double> divided by type double
   complex<double> cl2( polar(3.0 , pi / 6 ) );
   double cr2 =5;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex<double> cs2 = cl2 / cr2;
   cout << "The quotient of the two complex numbers is: cs2 /= cl2 cr2 = "
        << cs2 << endl;

   // This is equivalent to the following operation
   cl2 /= cr2;
   cout << "Quotient of two complex numbers is also: cl2 = /cr2 = "
        << cl2 << endl;

   double abscl2 = abs( cl2 );
   double argcl2 = arg( cl2 );
   cout << "The modulus of cl2 is: " << abscl2 << endl;
   cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
The left-side complex number is cl1 = (2.59808,1.5)
The right-side complex number is cr1 = (1,1.73205)
The quotient of the two complex numbers is: cs1 = cl1 /cr1 = (1.29904,-0.75)
Quotient of two complex numbers is also: cl1 /= cr1 = (1.29904,-0.75)
The modulus of cl1 is: 1.5
The argument of cl1 is: -0.523599 radians, which is -30 degrees.

The left-side complex number is cl2 = (2.59808,1.5)
The right-side complex number is cr2 = 5
The quotient of the two complex numbers is: cs2 /= cl2 cr2 = (0.519615,0.3)
Quotient of two complex numbers is also: cl2 = /cr2 = (0.519615,0.3)
The modulus of cl2 is: 0.6
The argument of cl2 is: 0.523599 radians, which is 30 degrees.
```

## <a name="op_eq"></a>  COMPLEX::operator =

Przypisuje numer docelowej liczby zespolonej, gdzie mogą być skomplikowane numer przypisany lub tego samego typu co są rzeczywiste i urojone części liczb zespolonych, które są przypisane.

```cpp
template <class Other>
complex<Type>& operator=(const complex<Other>& right);

complex<Type>& operator=(const Type& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Liczbą lub liczbą, która jest tego samego typu co parametr liczby zespolonej docelowego.

### <a name="return-value"></a>Wartość zwracana

Liczby zespolonej, który został przypisany numer, który został określony jako parametr.

### <a name="remarks"></a>Uwagi

Operacji jest przeciążona, tak aby proste operacje arytmetyczne, mogą być wykonywane bez konwersji danych do określonego formatu.

### <a name="example"></a>Przykład

```cpp
// complex_op_as.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> assigned to type complex<double>
   complex<double> cl1( 3.0 , 4.0 );
   complex<double> cr1( 2.0 , -1.0 );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   cl1  = cr1;
   cout << "The complex number cr1 assigned to the complex number cl1 is:"
        << "\ncl1 = cr1 = " << cl1 << endl;

   // Example of the second member function
   // type double assigned to type complex<double>
   complex<double> cl2( -2 , 4 );
   double cr2 =5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   cl2 = cr2;
   cout << "The complex number cr2 assigned to the complex number cl2 is:"
        << "\ncl2 = cr2 = " << cl2 << endl;

   cl2 = complex<double>(3.0, 4.0);
   cout << "The complex number (3, 4) assigned to the complex number cl2 is:"
        << "\ncl2 = " << cl2 << endl;
}
```

```Output
The left-side complex number is cl1 = (3,4)
The right-side complex number is cr1 = (2,-1)
The complex number cr1 assigned to the complex number cl1 is:
cl1 = cr1 = (2,-1)
The left-side complex number is cl2 = (-2,4)
The right-side complex number is cr2 = 5
The complex number cr2 assigned to the complex number cl2 is:
cl2 = cr2 = (5,0)
The complex number (3, 4) assigned to the complex number cl2 is:
cl2 = (3,4)
```

## <a name="real"></a>  COMPLEX::Real

Pobiera lub ustawia rzeczywisty składnik liczby zespolonej.

```cpp
constexpr T real() const;

T real(const T& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Liczby zespolonej, którego rzeczywistą wartość do wyodrębnienia.

### <a name="return-value"></a>Wartość zwracana

Rzeczywiste część liczby zespolonej.

### <a name="remarks"></a>Uwagi

Dla liczby zespolonej *+ bi*, część rzeczywista lub składnik jest *Re(a + bi) =*.

### <a name="example"></a>Przykład

```cpp
// complex_class_real.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;

   complex<double> c1( 4.0 , 3.0 );
   cout << "The complex number c1 = " << c1 << endl;

   double dr1 = c1.real();
   cout << "The real part of c1 is c1.real() = "
        << dr1 << "." << endl;

   double di1 = c1.imag();
   cout << "The imaginary part of c1 is c1.imag() = "
        << di1 << "." << endl;
}
```

```Output
The complex number c1 = (4,3)
The real part of c1 is c1.real() = 4.
The imaginary part of c1 is c1.imag() = 3.
```

## <a name="value_type"></a>  COMPLEX::value_type

Typ, który reprezentuje typ danych używany do reprezentowania rzeczywiste i urojone części liczb zespolonych.

```
typedef Type value_type;
```

### <a name="remarks"></a>Uwagi

`value_type` jest synonimem dla klasy złożone `Type` parametru szablonu.

### <a name="example"></a>Przykład

```cpp
// complex_valuetype.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
    using namespace std;
    complex<double>::value_type a = 3, b = 4;

    complex<double> c1 ( a , b );
    cout << "Specifying initial real & imaginary parts"
        << "\nof type value_type: "
        << "c1 = " << c1 << "." << endl;
}
```

```Output
Specifying initial real & imaginary parts
of type value_type: c1 = (3,4).
```

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
