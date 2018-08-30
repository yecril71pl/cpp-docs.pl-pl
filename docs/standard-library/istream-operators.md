---
title: '&lt;IStream&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- istream/std::operator&gt;&gt;
dev_langs:
- C++
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1fdad6f34fed49ec851f027cba4c53ea08b48902
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195406"
---
# <a name="ltistreamgt-operators"></a>&lt;IStream&gt; operatorów

## <a name="op_gt_gt"></a>  Operator&gt;&gt;

Wyodrębnia znaki oraz ciągi znaków ze strumienia.

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

*Ch* znak.

*Istr* strumienia.

*str* ciągu.

*Val* typu.

### <a name="return-value"></a>Wartość zwracana

Strumień

### <a name="remarks"></a>Uwagi

`basic_istream` Klasa definiuje również kilka operatorów wyodrębniania. Aby uzyskać więcej informacji, zobacz [basic_istream::operator >>](../standard-library/basic-istream-class.md#op_gt_gt).

Funkcja szablonu:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem* str);
```

wyodrębnia maksymalnie *N* - 1 elementy i przechowuje je w tablicy, zaczynając od _ *Str*. If `Istr`. [szerokość](../standard-library/ios-base-class.md#width) jest większa od zera, *N* jest `Istr`. **szerokość**; w przeciwnym razie jest rozmiar największego tablicę `Elem` mogą być deklarowane. Funkcja zawsze przechowuje wartość `Elem()` po wyodrębnieniu dowolne elementy, które są przechowywane. Wyodrębnianie wcześnie zatrzymuje się na końcu pliku, na znak o wartości **Elem**(0) (który jest nie wyodrębnić), lub w dowolnym elemencie, (która nie jest wyodrębniany), który będzie odrzucany przez [ws](../standard-library/istream-functions.md#ws). Jeśli funkcja wyodrębnia żadnych elementów, wywołuje metodę `Istr`. [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). W każdym przypadku wywoływanych przez nią `Istr`. **szerokość**(0) i zwraca *Istr*.

**Uwaga dotycząca zabezpieczeń** ciąg zakończony zerem wyodrębniania ze strumienia wejściowego, nie może przekraczać rozmiaru bufora docelowego *str*. Aby uzyskać więcej informacji, zobacz [unikanie przepełnień bufora](/windows/desktop/SecBP/avoiding-buffer-overruns).

Funkcja szablonu:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

wyodrębnia element, jeśli jest to możliwe i zapisuje go w *Ch*. W przeciwnym razie wywoływanych przez nią **jest**. [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**). W każdym przypadku zwraca *Istr*.

Funkcja szablonu:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char* str);
```

Zwraca `Istr >> ( char * ) str`.

Funkcja szablonu:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char& Ch);
```

Zwraca `Istr >> ( char& ) Ch`.

Funkcja szablonu:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char* str);
```

Zwraca `Istr >> ( char * ) str`.

Funkcja szablonu:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char& Ch);
```

Zwraca `Istr >> ( char& ) Ch`.

Funkcja szablonu:

```cpp
template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

Zwraca `Istr >> val` (i konwertuje odwołania rvalue do `Istr` z wartościowaniem lewostronnym w procesie).

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

[\<istream>](../standard-library/istream.md)<br/>
