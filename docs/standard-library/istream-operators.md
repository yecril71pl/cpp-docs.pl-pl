---
title: '&lt;operatorzy&gt; istream'
ms.date: 11/04/2016
f1_keywords:
- istream/std::operator&gt;&gt;
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
ms.openlocfilehash: 3b9521fde1b5a03389bfc1ad3e35fa407d9d6ac0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363038"
---
# <a name="ltistreamgt-operators"></a>&lt;operatorzy&gt; istream

## <a name="operatorgtgt"></a><a name="op_gt_gt"></a>Operator&gt;&gt;

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

*Ch*\
Znak.

*Istr*\
Strumień.

*Str*\
Ciąg.

*Val*\
Typ.

### <a name="return-value"></a>Wartość zwracana

Strumień

### <a name="remarks"></a>Uwagi

Klasa `basic_istream` definiuje również kilka operatorów ekstrakcji. Aby uzyskać więcej informacji, zobacz [basic_istream::operator>>](../standard-library/basic-istream-class.md#op_gt_gt).

Szablon funkcji:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem* str);
```

wyodrębnia do `N - 1` elementów i przechowuje je w tablicy, począwszy od *ul.* Jeśli `Istr.` [szerokość](../standard-library/ios-base-class.md#width) jest większa od zera, *N* jest `Istr.width`; w przeciwnym razie jest to rozmiar `Elem` największej tablicy, która może być zadeklarowana. Funkcja zawsze przechowuje `Elem()` wartość po wyodrębnionych elementów, które przechowuje. Wyodrębnianie zatrzymuje się na początku na `Elem(0)` końcu pliku, na znaku o wartości (która nie jest wyodrębniona) lub na dowolnym elemencie (który nie jest wyodrębniany), który zostałby odrzucony przez [ws](../standard-library/istream-functions.md#ws). Jeśli funkcja nie wyodrębni żadnych `Istr.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`elementów, wywołuje . W każdym razie `Istr.width(0)` wywołuje i zwraca *Istr*.

**Uwaga dotycząca zabezpieczeń** Ciąg zakończony zerem wyodrębniany ze strumienia wejściowego nie może przekraczać rozmiaru docelowego *buforu str*. Aby uzyskać więcej informacji, zobacz [Unikanie przekroczenia buforu](/windows/win32/SecBP/avoiding-buffer-overruns).

Szablon funkcji:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

wyodrębnia element, jeśli to możliwe, i przechowuje go w *Ch*. W przeciwnym `is.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`razie wywołuje . W każdym razie zwraca *Istr*.

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

zwraca `Istr >> val` (i konwertuje odwołanie rvalue `Istr` na wartość lvalue w procesie).

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

## <a name="see-also"></a>Zobacz też

[\<>istream](../standard-library/istream.md)
