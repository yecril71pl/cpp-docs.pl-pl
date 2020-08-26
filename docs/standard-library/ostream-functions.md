---
title: '&lt;&gt;funkcje ostream'
ms.date: 11/04/2016
f1_keywords:
- ostream/std::swap
- ostream/std::endl
- ostream/std::ends
- ostream/std::flush
ms.assetid: d6e56cc0-c8df-4dbe-be10-98e14c35ed3a
helpviewer_keywords:
- std::swap [C++]
- std::endl [C++]
- std::ends [C++]
- std::flush [C++]
ms.openlocfilehash: 4db966797202b16911aa67b6fda7c81785d98166
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842640"
---
# <a name="ltostreamgt-functions"></a>&lt;&gt;funkcje ostream

Są to funkcje szablonu globalnego zdefiniowane w &lt; ostream &gt; . W przypadku funkcji Członkowskich zapoznaj się z dokumentacją [klasy basic_ostream](basic-ostream-class.md) .

[endl](#endl)\
[celów](#ends)\
[płukan](#flush)\
[wymiany](#swap)

## <a name="endl"></a>endl

Kończy wiersz i opróżnia bufor.

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& endl(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Parametry

*Elem*\
Typ elementu.

*Ostr*\
Obiekt typu **basic_ostream**.

*Zdawczy*\
Cechy znaków.

### <a name="return-value"></a>Wartość zwracana

Obiekt typu **basic_ostream**.

### <a name="remarks"></a>Uwagi

Manipulator wywołuje *ostr*. [Put](../standard-library/basic-ostream-class.md#put)(*ostr*.[ Rozszerz](../standard-library/basic-ios-class.md#widen)("\n")), a następnie wywoła *ostr*. [opróżnianie](../standard-library/basic-ostream-class.md#flush). Zwraca *ostr*.

### <a name="example"></a>Przykład

```cpp
// ostream_endl.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "testing" << endl;
}
```

```Output
testing
```

## <a name="ends"></a>graniczne

Kończy ciąg.

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& ends(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Parametry

*Elem*\
Typ elementu.

*Ostr*\
Obiekt typu `basic_ostream`.

*Zdawczy*\
Cechy znaków.

### <a name="return-value"></a>Wartość zwracana

Obiekt typu `basic_ostream`.

### <a name="remarks"></a>Uwagi

Manipulator wywołuje *ostr*. [Put](../standard-library/basic-ostream-class.md#put)(*elem*(' \ 0 ')). Zwraca *ostr*.

### <a name="example"></a>Przykład

```cpp
// ostream_ends.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "a";
   cout << "b" << ends;
   cout << "c" << endl;
}
```

```Output
ab c
```

## <a name="flush"></a>opróżnianie

Opróżnia bufor.

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& flush(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Parametry

*Elem*\
Typ elementu.

*Ostr*\
Obiekt typu `basic_ostream`.

*Zdawczy*\
Cechy znaków.

### <a name="return-value"></a>Wartość zwracana

Obiekt typu `basic_ostream`.

### <a name="remarks"></a>Uwagi

Manipulator wywołuje *ostr*. [opróżnianie](../standard-library/basic-ostream-class.md#flush). Zwraca *ostr*.

### <a name="example"></a>Przykład

```cpp
// ostream_flush.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "testing" << flush;
}
```

```Output
testing
```

## <a name="swap"></a>swap

Wymienia wartości dwóch `basic_ostream` obiektów.

```cpp
template <class Elem, class Tr>
void swap(
   basic_ostream<Elem, Tr>& left,
   basic_ostream<Elem, Tr>& right);
```

### <a name="parameters"></a>Parametry

*Elem*\
Typ elementu.

*Zdawczy*\
Cechy znaków.

*lewym*\
Odwołanie lvalue do `basic_ostream` obiektu.

*Kliknij*\
Odwołanie lvalue do `basic_ostream` obiektu.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest `swap` wykonywana `left.swap(right)` .

## <a name="see-also"></a>Zobacz też

[\<ostream>](../standard-library/ostream.md)
