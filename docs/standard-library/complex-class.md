---
title: COMPLEX — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: baedaa5300ccc069be3222192ba0e8f3ccf6f6f0
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="complex-class"></a>complex — Klasa

Klasa szablonu opisuje obiekt, który przechowuje dwa obiekty typu **typu**, jedna reprezentuje rzeczywistą część liczbą i taki, który reprezentuje część urojony.

## <a name="syntax"></a>Składnia

```

template <class
Type>
class complex
```

## <a name="remarks"></a>Uwagi

Obiekt klasy **typu**:

- Ma publicznego konstruktora domyślnego, destruktor, konstruktora kopiującego i operatora przypisania z konwencjonalnej zachowanie.

- Można przypisać liczbą całkowitą lub wartości zmiennoprzecinkowych, lub wpisz Rzutowanie na takie wartości z konwencjonalnej zachowanie.

- Definiuje operatory arytmetyczne i funkcje matematyczne, zgodnie z potrzebami, które są zdefiniowane dla typów zmiennoprzecinkowych z konwencjonalnej zachowanie.

W szczególności nie niewielkie różnice mogą istnieć między konstruowania kopiowania i konstrukcji domyślne następuje przypisania. Żadna z operacji w obiektach klasy **typu** może zgłaszać wyjątków.

Jawne specjalizacje szablonu klasy złożone istnieje dla trzech typów zmiennoprzecinkowych. W tej implementacji wartość innego typu **typu** jest rzutowanie typu do **podwójne** rzeczywiste obliczenia z **podwójne** wynik przypisany do obiektu przechowywane Typ **typu**`.`

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[complex](#complex)|Tworzy liczbą z określonej części rzeczywistych i urojony lub kopię inny numer złożone.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[value_type](#value_type)|Typ, który reprezentuje typ danych używany do reprezentowania rzeczywistą i urojony części liczbą.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[imag](#imag)|Wyodrębnia urojony składnik liczbą.|
|[rzeczywiste](#real)|Wyodrębnia rzeczywistych składnik liczbą.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator*=](#op_star_eq)|Mnoży liczbą docelowego przez współczynnik, który może być skomplikowane lub być tego samego typu są prawdziwe i urojony część liczby złożonej.|
|[operator+=](#op_add_eq)|Dodaje numer liczbą docelowej, w przypadku, gdy liczba dodana może być złożony lub tego samego typu co są części rzeczywistych i urojony liczby złożonej, do którego jest dodawany.|
|[operator-=](#operator-_eq)|Odejmuje liczbę z zakresu od liczby złożonej docelowej, w przypadku, gdy liczba odejmować może być złożony lub tego samego typu co są części rzeczywistych i urojony liczby złożonej, do którego jest dodawany.|
|[/ = — operator](#op_div_eq)|Dzieli liczbą docelowego przez dzielnik, która może być skomplikowane lub być tego samego typu są prawdziwe i urojony część liczby złożonej.|
|[operator=](#op_eq)|Przypisuje liczbę docelowych liczbą, gdzie numer przypisany może być skomplikowane lub tego samego typu co są prawdziwe i urojony część liczby złożonej, do której jest ona obecnie przypisywana.|

## <a name="requirements"></a>Wymagania

**Nagłówek**: \<złożonych >

**Namespace:** Standard

## <a name="complex"></a>  COMPLEX::Complex

Tworzy liczbą z określonej części rzeczywistych i urojony lub kopię inny numer złożone.

```cpp
constexpr complex(
    const T&
    _RealVal = 0  ,
    const T&
    _ImagVal = 0);

    template <class Other>
constexpr complex(
    const complex<Other>&
    complexNum);
```

### <a name="parameters"></a>Parametry

`_RealVal` Wartość część rzeczywista używaną do inicjalizacji liczby złożonej tworzona.

`_ImagVal` Wartość części urojony używaną do inicjalizacji liczby złożonej tworzona.

`complexNum` Liczby złożonej, w których części rzeczywistą i urojony są używane do zainicjowania liczby złożonej tworzona.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje zapisana rzeczywistym należą do _ *RealVal* i przechowywane części urojony do \_ *Imagval*. Drugi Konstruktor inicjuje zapisana rzeczywistym należą do `complexNum` **.real**() i przechowywane części urojony do `complexNum` **.imag**().

W tej implementacji, jeśli translatora nie obsługuje funkcji szablonu elementu członkowskiego, szablon:

```cpp
template <class Other>
complex(const complex<Other>& right);
```

jest zastępowany:

```

complex(const complex& right);
```

Konstruktor kopiujący jest.

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
   complex <double> c1 ( 4.0 , 5.0 );
   cout << "Specifying initial real & imaginary parts,"
        << "c1 = " << c1 << endl;

   // The second constructor initializes values of the real &
   // imaginary parts using those of another complex number
   complex <double> c2 ( c1 );
   cout << "Initializing with the real and imaginary parts of c1,"
        << " c2 = " << c2 << endl;

   // Complex numbers can be initialized in polar form
   // but will be stored in Cartesian form
   complex <double> c3 ( polar ( sqrt( (double)8 ) , pi / 4 ) );
   cout << "c3 = polar ( sqrt ( 8 ) , pi / 4 ) = " << c3 << endl;

   // The modulus and argument of a complex number can be recovered
   double absc3 = abs ( c3 );
   double argc3 = arg ( c3 );
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "
        << absc3 << endl;
   cout << "Argument of c3 is recovered from c3 using:\n arg ( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
```

## <a name="imag"></a>  COMPLEX::imag

Wyodrębnia urojony składnik liczbą.

```cpp
T imag() const;


T imag(const T& right);
```

### <a name="parameters"></a>Parametry

`right` Liczba złożonych jest którego urojony wartość do wyodrębnienia.

### <a name="return-value"></a>Wartość zwracana

Wyrażenie Liczba_zespolona część liczby złożonej.

### <a name="remarks"></a>Uwagi

Dla liczbą *+ analizy biznesowej*, urojony części lub składnika jest *Im(a + bi) = b.*

### <a name="example"></a>Przykład

```cpp
// complex_imag.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;

   complex <double> c1 ( 4.0 , 3.0 );
   cout << "The complex number c1 = " << c1 << endl;

   double dr1 = c1.real ( );
   cout << "The real part of c1 is c1.real ( ) = "
        << dr1 << "." << endl;

   double di1 = c1.imag ( );
   cout << "The imaginary part of c1 is c1.imag ( ) = "
        << di1 << "." << endl;
}
```

```Output
The complex number c1 = (4,3)
The real part of c1 is c1.real ( ) = 4.
The imaginary part of c1 is c1.imag ( ) = 3.
```

## <a name="op_star_eq"></a>  COMPLEX::operator * =

Mnoży liczbą docelowego przez współczynnik, który może być skomplikowane lub być tego samego typu są prawdziwe i urojony część liczby złożonej.

```cpp
template <class Other>
complex& operator*=(const complex<Other>& right);

complex<Type>& operator*=(const Type& right);

complex<Type>& operator*=(const complex<Type>& right);
```

### <a name="parameters"></a>Parametry

`right` Liczbą lub liczby, która jest tego samego typu jako parametru liczby zespolonej docelowej.

### <a name="return-value"></a>Wartość zwracana

Liczba złożonych, która została pomnożona przez liczbę określony jako parametr.

### <a name="remarks"></a>Uwagi

Operacja jest przeciążona, dzięki czemu można wykonywać proste operacje arytmetyczne bez konwersji danych do określonego formatu.

### <a name="example"></a>Przykład

```cpp
// complex_op_me.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main() {
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> multiplied by type complex<double>
   complex <double> cl1 ( polar ( 3.0 , pi / 6 ) );
   complex <double> cr1 ( polar ( 2.0 , pi / 3 ) );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex <double> cs1 = cl1 * cr1;
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
   complex <double> cl2 ( polar ( 3.0 , pi / 6 ) );
   double cr2 = 5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex <double> cs2 = cl2 * cr2;
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

Dodaje numer liczbą docelowej, w przypadku, gdy liczba dodana może być złożony lub tego samego typu co są części rzeczywistych i urojony liczby złożonej, do którego jest dodawany.

```cpp
template <class Other>
complex<Type>& operator+=(const complex<Other>& right);

complex<Type>& operator+=(const Type& right);

complex<Type>& operator+=(const complex<Type>& right);
```

### <a name="parameters"></a>Parametry

`right` Liczbą lub liczby, która jest tego samego typu jako parametru liczby zespolonej docelowej.

### <a name="return-value"></a>Wartość zwracana

Liczby złożonej, który miał podano jako parametr dodany.

### <a name="remarks"></a>Uwagi

Operacja jest przeciążona, dzięki czemu można wykonywać proste operacje arytmetyczne bez konwersji danych do określonego formatu.

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
   complex <double> cl1 ( 3.0 , 4.0 );
   complex <double> cr1 ( 2.0 , -1.0 );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex <double> cs1 = cl1 + cr1;
   cout << "The sum of the two complex numbers is: cs1 = cl1 + cr1 = "
        << cs1 << endl;

   // This is equivalent to the following operation
   cl1 += cr1;
   cout << "The complex number cr1 added to the complex number cl1 is:"
        << "\n cl1 += cr1 = " << cl1 << endl;

   double abscl1 = abs ( cl1 );
   double argcl1 = arg ( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type double added to type complex<double>
   complex <double> cl2 ( -2 , 4 );
   double cr2 =5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex <double> cs2 = cl2 + cr2;
   cout << "The sum of the two complex numbers is: cs2 = cl2 + cr2 = "
        << cs2 << endl;

   // This is equivalent to the following operation
   cl2 += cr2;
   cout << "The complex number cr2 added to the complex number cl2 is:"
        << "\n cl2 += cr2 = " << cl2 << endl;

   double abscl2 = abs ( cl2 );
   double argcl2 = arg ( cl2 );
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

Odejmuje liczbę z zakresu od liczby złożonej docelowej, w przypadku, gdy liczba odejmować może być złożony lub tego samego typu co są części rzeczywistych i urojony liczby złożonej, do którego jest dodawany.

```cpp
template <class Other>
complex<Type>& operator-=(const complex<Other>& complexNum);

complex<Type>& operator-=(const Type& _RealPart);

complex<Type>& operator-=(const complex<Type>& complexNum);
```

### <a name="parameters"></a>Parametry

`complexNum` Liczby złożonej do odjęta od liczby złożonej docelowej.

`_RealPart` Liczba rzeczywista odjęta od liczby złożonej docelowej.

### <a name="return-value"></a>Wartość zwracana

Liczby złożonej, który miał podano jako parametr odjęta od niego.

### <a name="remarks"></a>Uwagi

Operacja jest przeciążona, dzięki czemu można wykonywać proste operacje arytmetyczne bez konwersji danych do określonego formatu.

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
   complex <double> cl1 ( 3.0 , 4.0 );
   complex <double> cr1 ( 2.0 , -1.0 );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex <double> cs1 = cl1 - cr1;
   cout << "The difference between the two complex numbers is:"
        << "\n cs1 = cl1 - cr1 = " << cs1 << endl;

   // This is equivalent to the following operation
   cl1 -= cr1;
   cout << "Complex number cr1 subtracted from complex number cl1 is:"
        << "\n cl1 -= cr1 = " << cl1 << endl;

   double abscl1 = abs ( cl1 );
   double argcl1 = arg ( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type double subtracted from type complex<double>
   complex <double> cl2 ( 2.0 , 4.0 );
   double cr2 = 5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex <double> cs2 = cl2 - cr2;
   cout << "The difference between the two complex numbers is:"
        << "\n cs2 = cl2 - cr2 = " << cs2 << endl;

   // This is equivalent to the following operation
   cl2  -= cr2;
   cout << "Complex number cr2 subtracted from complex number cl2 is:"
        << "\n cl2 -= cr2 = " << cl2 << endl;

   double abscl2 = abs ( cl2 );
   double argcl2 = arg ( cl2 );
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

Dzieli liczbą docelowego przez dzielnik, która może być skomplikowane lub być tego samego typu są prawdziwe i urojony część liczby złożonej.

```cpp
template <class Other>
complex<Type>& operator/=(const complex<Other>& complexNum);

complex<Type>& operator/=(const Type& _RealPart);

complex<Type>& operator/=(const complex<Type>& complexNum);
```

### <a name="parameters"></a>Parametry

`complexNum` Liczby złożonej do odjęta od liczby złożonej docelowej.

`_RealPart` Liczba rzeczywista odjęta od liczby złożonej docelowej.

### <a name="return-value"></a>Wartość zwracana

Liczby złożonej, który został podzielony przez liczbę określony jako parametr.

### <a name="remarks"></a>Uwagi

Operacja jest przeciążona, dzięki czemu można wykonywać proste operacje arytmetyczne bez konwersji danych do określonego formatu.

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
   complex <double> cl1 ( polar (3.0 , pi / 6 ) );
   complex <double> cr1 ( polar (2.0 , pi / 3 ) );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex <double> cs1 = cl1 / cr1;
   cout << "The quotient of the two complex numbers is: cs1 = cl1 /cr1 = "
        << cs1 << endl;

   // This is equivalent to the following operation
   cl1 /= cr1;
   cout << "Quotient of two complex numbers is also: cl1 /= cr1 = "
        << cl1 << endl;

   double abscl1 = abs ( cl1 );
   double argcl1 = arg ( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type complex<double> divided by type double
   complex <double> cl2 ( polar (3.0 , pi / 6 ) );
   double cr2 =5;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex <double> cs2 = cl2 / cr2;
   cout << "The quotient of the two complex numbers is: cs2 /= cl2 cr2 = "
        << cs2 << endl;

   // This is equivalent to the following operation
   cl2 /= cr2;
   cout << "Quotient of two complex numbers is also: cl2 = /cr2 = "
        << cl2 << endl;

   double abscl2 = abs ( cl2 );
   double argcl2 = arg ( cl2 );
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

Przypisuje liczbę docelowych liczbą, gdzie numer przypisany może być skomplikowane lub tego samego typu co są prawdziwe i urojony część liczby złożonej, do której jest ona obecnie przypisywana.

```cpp
template <class Other>
complex<Type>& operator=(const complex<Other>& right);

complex<Type>& operator=(const Type& right);
```

### <a name="parameters"></a>Parametry

`right` Liczbą lub liczby, która jest tego samego typu jako parametru liczby zespolonej docelowej.

### <a name="return-value"></a>Wartość zwracana

Liczba złożonych przypisany numer określony jako parametr.

### <a name="remarks"></a>Uwagi

Operacja jest przeciążona, dzięki czemu można wykonywać proste operacje arytmetyczne bez konwersji danych do określonego formatu.

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
   complex <double> cl1 ( 3.0 , 4.0 );
   complex <double> cr1 ( 2.0 , -1.0 );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   cl1  = cr1;
   cout << "The complex number cr1 assigned to the complex number cl1 is:"
        << "\n cl1 = cr1 = " << cl1 << endl;

   // Example of the second member function
   // type double assigned to type complex<double>
   complex <double> cl2 ( -2 , 4 );
   double cr2 =5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   cl2 = cr2;
   cout << "The complex number cr2 assigned to the complex number cl2 is:"
        << "\n cl2 = cr2 = " << cl2 << endl;

   cl2 = complex<double>(3.0, 4.0);
   cout << "The complex number (3, 4) assigned to the complex number cl2 is:"
        << "\n cl2 = " << cl2 << endl;
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

Pobiera lub ustawia składnik rzeczywistych liczbą.

```cpp
constexpr T real() const;


T real(const T& right);
```

### <a name="parameters"></a>Parametry

`right` Liczba złożonych, którego wartość rzeczywista jest do wyodrębnienia.

### <a name="return-value"></a>Wartość zwracana

Część rzeczywista liczby złożonej.

### <a name="remarks"></a>Uwagi

Dla liczbą *+ analizy biznesowej*, część rzeczywista lub składnik jest *Re(a + bi) =.*

### <a name="example"></a>Przykład

```cpp
// complex_class_real.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;

   complex <double> c1 ( 4.0 , 3.0 );
   cout << "The complex number c1 = " << c1 << endl;

   double dr1 = c1.real ( );
   cout << "The real part of c1 is c1.real ( ) = "
        << dr1 << "." << endl;

   double di1 = c1.imag ( );
   cout << "The imaginary part of c1 is c1.imag ( ) = "
        << di1 << "." << endl;
}
```

```Output
The complex number c1 = (4,3)
The real part of c1 is c1.real ( ) = 4.
The imaginary part of c1 is c1.imag ( ) = 3.
```

## <a name="value_type"></a>  COMPLEX::value_type

Typ, który reprezentuje typ danych używany do reprezentowania rzeczywistą i urojony części liczbą.

```

typedef Type value_type;
```

### <a name="remarks"></a>Uwagi

`value_type` jest synonimem klasy złożone **typu** parametru szablonu.

### <a name="example"></a>Przykład

```cpp
// complex_valuetype.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   complex <double>::value_type a = 3, b = 4;

   complex <double> c1 ( a , b );
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

[złożonych elementów członkowskich](http://msdn.microsoft.com/en-us/d5c4466c-43a0-4817-aca1-9a5d492dae28)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
