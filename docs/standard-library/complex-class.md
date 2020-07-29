---
title: complex — Klasa
ms.date: 03/27/2019
f1_keywords:
- complex/std::complex::value_type
- complex/std::complex::imag
- complex/std::complex::real
helpviewer_keywords:
- std::complex [C++], value_type
- std::complex [C++], imag
- std::complex [C++], real
ms.assetid: d6492e1c-5eba-4bc5-835b-2a88001a5868
ms.openlocfilehash: db2f8b2f889d9454db737cf5b2a39b414f1d67f1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230094"
---
# <a name="complex-class"></a>complex — Klasa

Szablon klasy opisuje obiekt przechowujący dwa obiekty typu `Type` , taki, który reprezentuje rzeczywistą część liczby zespolonej i jeden, który reprezentuje część urojoną.

## <a name="syntax"></a>Składnia

```cpp
template <class Type>
class complex
```

## <a name="remarks"></a>Uwagi

Obiekt klasy `Type` :

- Ma publiczny Konstruktor domyślny, destruktor, Konstruktor kopiujący i operator przypisania z zachowaniem konwencjonalnym.

- Można przypisać wartości całkowite lub zmiennoprzecinkowe lub wpisać rzutowanie na takie wartości z zachowaniem konwencjonalnym.

- Definiuje operatory arytmetyczne i funkcje matematyczne w razie potrzeby, które są zdefiniowane dla typów zmiennoprzecinkowych z zachowaniem konwencjonalnym.

W szczególności nie mogą istnieć żadne delikatne różnice między konstrukcją kopiowania i domyślną konstrukcją, po którym następuje przypisanie. Żadna z operacji na obiektach klasy `Type` nie może zgłosić wyjątków.

Jawne specjalizacje złożone szablonu klas istnieją dla trzech typów zmiennoprzecinkowych. W tej implementacji wartość dowolnego innego typu `Type` jest rzutowanie do **`double`** rzeczywistej obliczeń, a **`double`** wynik jest przypisywany z powrotem do przechowywanego obiektu typu `Type` .

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[złożonych](#complex)|Konstruuje liczbę zespoloną z określonymi częściami rzeczywistymi i urojonymi albo jako kopię innej liczby zespolonej.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[value_type](#value_type)|Typ, który reprezentuje typ danych używany do reprezentowania rzeczywistych i urojonych części liczby zespolonej.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[imag](#imag)|Wyodrębnia część urojoną liczby zespolonej.|
|[real](#real)|Wyodrębnia prawdziwy składnik liczby zespolonej.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator * =](#op_star_eq)|Mnoży docelowy liczbę zespoloną przez współczynnik, który może być złożony lub być tego samego typu, co są częścią rzeczywistą i urojoną liczby zespolonej.|
|[operator + =](#op_add_eq)|Dodaje liczbę do docelowej liczby zespolonej, w której dodana liczba może być złożona lub tego samego typu co są częścią rzeczywistą i urojoną liczby zespolonej, do której jest dodawany.|
|[operator-=](#operator-_eq)|Odejmuje liczbę od docelowej liczby zespolonej, w której liczba odejmowanych może być złożona lub tego samego typu co są częścią rzeczywistą i urojoną liczby zespolonej, do której jest dodawany.|
|[operator/=](#op_div_eq)|Dzieli docelowy liczbę zespoloną przez dzielnik, który może być złożony lub być tego samego typu co wartości rzeczywiste i urojone części liczby zespolonej.|
|[operator =](#op_eq)|Przypisuje liczbę do docelowego numeru zespolonego, gdzie przypisana liczba może być złożona lub tego samego typu, co jest częścią rzeczywistą i urojoną liczby zespolonej, do której jest przypisany.|

## <a name="complex"></a><a name="complex"></a>złożonych

Konstruuje liczbę zespoloną z określonymi częściami rzeczywistymi i urojonymi albo jako kopię innej liczby zespolonej.

```cpp
constexpr complex(
    const T& _RealVal = 0,
    const T& _ImagVal = 0);

template <class Other>
constexpr complex(
    const complex<Other>& complexNum);
```

### <a name="parameters"></a>Parametry

*_RealVal*\
Wartość części rzeczywistej użytej do zainicjowania konstruowanej liczby zespolonej.

*_ImagVal*\
Wartość części urojonej użytej do zainicjowania konstruowanej liczby zespolonej.

*complexNum*\
Liczba zespolona, której części rzeczywiste i urojone są używane do inicjowania konstruowanej liczby zespolonej.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje przechowywaną część rzeczywistą do * \_ RealVal* i magazynowaną część urojoną do * \_ Imagval*. Drugi Konstruktor inicjuje przechowywaną część rzeczywistą do `complexNum.real()` i przechowywaną część urojoną do `complexNum.imag()` .

W tej implementacji, jeśli Translator nie obsługuje funkcji szablonu elementu członkowskiego, szablon:

```cpp
template <class Other>
complex(const complex<Other>& right);
```

zamieniono na:

```cpp
complex(const complex& right);
```

który jest konstruktorem kopiującym.

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

## <a name="imag"></a><a name="imag"></a>imag

Wyodrębnia część urojoną liczby zespolonej.

```cpp
T imag() const;

T imag(const T& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Liczba złożona, której wartość urojona ma zostać wyodrębniona.

### <a name="return-value"></a>Wartość zwracana

Część urojona liczby zespolonej.

### <a name="remarks"></a>Uwagi

W przypadku liczby zespolonej *a + bi*części urojonej lub składnika to *komunikator (a + bi) = b*.

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

## <a name="operator"></a><a name="op_star_eq"></a>operator * =

Mnoży docelowy liczbę zespoloną przez współczynnik, który może być złożony lub być tego samego typu, co są częścią rzeczywistą i urojoną liczby zespolonej.

```cpp
template <class Other>
complex& operator*=(const complex<Other>& right);

complex<Type>& operator*=(const Type& right);

complex<Type>& operator*=(const complex<Type>& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Liczba złożona lub liczba, która jest tego samego typu co parametr docelowego numeru zespolonego.

### <a name="return-value"></a>Wartość zwracana

Liczba złożona, która została pomnożona przez liczbę określoną jako parametr.

### <a name="remarks"></a>Uwagi

Operacja jest przeciążona, tak aby proste operacje arytmetyczne mogły być wykonywane bez konwersji danych do określonego formatu.

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

## <a name="operator"></a><a name="op_add_eq"></a>operator + =

Dodaje liczbę do docelowej liczby zespolonej, w której dodana liczba może być złożona lub tego samego typu co są częścią rzeczywistą i urojoną liczby zespolonej, do której jest dodawany.

```cpp
template <class Other>
complex<Type>& operator+=(const complex<Other>& right);

complex<Type>& operator+=(const Type& right);

complex<Type>& operator+=(const complex<Type>& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Liczba złożona lub liczba, która jest tego samego typu co parametr docelowego numeru zespolonego.

### <a name="return-value"></a>Wartość zwracana

Liczba złożona, która ma numer określony jako parametr dodany.

### <a name="remarks"></a>Uwagi

Operacja jest przeciążona, tak aby proste operacje arytmetyczne mogły być wykonywane bez konwersji danych do określonego formatu.

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

## <a name="operator-"></a><a name="operator-_eq"></a>operator-=

Odejmuje liczbę od docelowej liczby zespolonej, w której liczba odejmowanych może być złożona lub tego samego typu co są częścią rzeczywistą i urojoną liczby zespolonej, do której jest dodawany.

```cpp
template <class Other>
complex<Type>& operator-=(const complex<Other>& complexNum);

complex<Type>& operator-=(const Type& _RealPart);

complex<Type>& operator-=(const complex<Type>& complexNum);
```

### <a name="parameters"></a>Parametry

*complexNum*\
Liczba zespolona, która ma zostać odjęta od docelowego numeru zespolonego.

*_RealPart*\
Liczba rzeczywista, która ma zostać odjęta od docelowego numeru zespolonego.

### <a name="return-value"></a>Wartość zwracana

Liczba złożona, która ma numer określony jako parametr odejmowany od niego.

### <a name="remarks"></a>Uwagi

Operacja jest przeciążona, tak aby proste operacje arytmetyczne mogły być wykonywane bez konwersji danych do określonego formatu.

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

## <a name="operator"></a><a name="op_div_eq"></a>operator/=

Dzieli docelowy liczbę zespoloną przez dzielnik, który może być złożony lub być tego samego typu co wartości rzeczywiste i urojone części liczby zespolonej.

```cpp
template <class Other>
complex<Type>& operator/=(const complex<Other>& complexNum);

complex<Type>& operator/=(const Type& _RealPart);

complex<Type>& operator/=(const complex<Type>& complexNum);
```

### <a name="parameters"></a>Parametry

*complexNum*\
Liczba zespolona, która ma zostać odjęta od docelowego numeru zespolonego.

*_RealPart*\
Liczba rzeczywista, która ma zostać odjęta od docelowego numeru zespolonego.

### <a name="return-value"></a>Wartość zwracana

Liczba złożona, która została podzielona przez liczbę określoną jako parametr.

### <a name="remarks"></a>Uwagi

Operacja jest przeciążona, tak aby proste operacje arytmetyczne mogły być wykonywane bez konwersji danych do określonego formatu.

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

## <a name="operator"></a><a name="op_eq"></a>operator =

Przypisuje liczbę do docelowego numeru zespolonego, gdzie przypisana liczba może być złożona lub tego samego typu, co jest częścią rzeczywistą i urojoną liczby zespolonej, do której jest przypisany.

```cpp
template <class Other>
complex<Type>& operator=(const complex<Other>& right);

complex<Type>& operator=(const Type& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Liczba złożona lub liczba, która jest tego samego typu co parametr docelowego numeru zespolonego.

### <a name="return-value"></a>Wartość zwracana

Liczba złożona, która ma przypisany numer określony jako parametr.

### <a name="remarks"></a>Uwagi

Operacja jest przeciążona, tak aby proste operacje arytmetyczne mogły być wykonywane bez konwersji danych do określonego formatu.

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

## <a name="real"></a><a name="real"></a>czasie rzeczywistym

Pobiera lub ustawia prawdziwy składnik liczby zespolonej.

```cpp
constexpr T real() const;

T real(const T& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Liczba złożona, której rzeczywista wartość ma zostać wyodrębniona.

### <a name="return-value"></a>Wartość zwracana

Rzeczywista część liczby zespolonej.

### <a name="remarks"></a>Uwagi

W przypadku liczby zespolonej *a + bi*część rzeczywista lub składnik jest *re (a + bi) = a*.

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

## <a name="value_type"></a><a name="value_type"></a>value_type

Typ, który reprezentuje typ danych używany do reprezentowania rzeczywistych i urojonych części liczby zespolonej.

```cpp
typedef Type value_type;
```

### <a name="remarks"></a>Uwagi

`value_type`jest synonimem dla parametru szablonu złożonego klasy `Type` .

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

[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
