---
title: Operatory &lt;IStream&gt;
ms.date: 11/04/2016
f1_keywords:
- istream/std::operator&gt;&gt;
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
ms.openlocfilehash: 5ac5c61488530f99cdad38ca1bfca365b6ac0f8c
ms.sourcegitcommit: 4b0928a1a497648d0d327579c8262f25ed20d02e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72890172"
---
# <a name="ltistreamgt-operators"></a>Operatory &lt;IStream&gt;

## <a name="op_gt_gt"></a>&gt; operatora &gt;

Wyodrębnia znaki i ciągi ze strumienia.

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr,
    Elem* str);

template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr,
    Elem& Ch);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    signed char* str);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    signed char& Ch);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    unsigned char* str);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    unsigned char& Ch);

template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

### <a name="parameters"></a>Parametry

*Ch* \
Znak.

*Istr*\
Strumień.

*str* \
Ciąg.

*val* \
Typ.

### <a name="return-value"></a>Wartość zwracana

Strumień

### <a name="remarks"></a>Uwagi

Klasa `basic_istream` definiuje również kilka operatorów wyodrębniania. Aby uzyskać więcej informacji, zobacz [basic_istream:: operator > >](../standard-library/basic-istream-class.md#op_gt_gt).

Szablon funkcji:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem* str);
```

wyodrębnia do `N - 1` elementów i zapisuje je w tablicy, zaczynając od *str*. Jeśli `Istr.`[Szerokość](../standard-library/ios-base-class.md#width) jest większa od zera, *N* jest `Istr.width`; w przeciwnym razie jest to rozmiar największej tablicy `Elem`, która może być zadeklarowana. Funkcja zawsze przechowuje wartość `Elem()` po wyekstrahowanych elementach, które przechowuje. Ekstrakcja kończy się wczesnie na końcu pliku, na znaku o wartości `Elem(0)` (który nie został wyodrębniony) ani w żadnym elemencie (który nie został wyodrębniony), który zostałby odrzucony przez [usługę WS](../standard-library/istream-functions.md#ws). Jeśli funkcja nie wyodrębni żadnych elementów, wywołuje `Istr.`[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`. W każdym przypadku wywołuje `Istr.width(0)` i zwraca *ISTR*.

**Uwaga dotycząca zabezpieczeń** Ciąg zakończony znakiem null, który jest wyodrębniany ze strumienia wejściowego, nie może przekraczać rozmiaru docelowego *str*. Aby uzyskać więcej informacji, zobacz [unikanie przekroczeń buforu](/windows/win32/SecBP/avoiding-buffer-overruns).

Szablon funkcji:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

wyodrębnienie elementu, jeśli jest to możliwe, i zapisanie go w *ch*. W przeciwnym razie wywołuje `is.`[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`. W każdym przypadku zwraca *ISTR*.

Szablon funkcji:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char* str);
```

zwraca `Istr >> ( char * ) str`.

Szablon funkcji:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char& Ch);
```

zwraca `Istr >> ( char& ) Ch`.

Szablon funkcji:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char* str);
```

zwraca `Istr >> ( char * ) str`.

Szablon funkcji:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char& Ch);
```

zwraca `Istr >> ( char& ) Ch`.

Szablon funkcji:

```cpp
template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

zwraca `Istr >> val` (i konwertuje odwołanie rvalue na `Istr` do lvalue w procesie).

### <a name="example"></a>Przykład

```cpp
// istream_op_extract.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   ws( cin );
   char c[10];

   cin.width( 9 );
   cin >> c;
   cout << c << endl;
}
```

## <a name="see-also"></a>Zobacz także

[\<istream >](../standard-library/istream.md)
