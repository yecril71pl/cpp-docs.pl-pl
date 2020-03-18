---
title: '&lt;funkcje&gt; ostream'
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
ms.openlocfilehash: 8d93e46b0323058d93c6d0bd8c1ee566998aef61
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419708"
---
# <a name="ltostreamgt-functions"></a>&lt;funkcje&gt; ostream

Są to funkcje szablonu globalnego zdefiniowane w &lt;ostream&gt;. W przypadku funkcji Członkowskich zapoznaj się z dokumentacją [klasy basic_ostream](basic-ostream-class.md) .

||||
|-|-|-|
|[endl](#endl)|[celów](#ends)|[płukan](#flush)|
|[wymiany](#swap)|

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

\ *TR*
Cechy znaków.

### <a name="return-value"></a>Wartość zwrócona

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

\ *TR*
Cechy znaków.

### <a name="return-value"></a>Wartość zwrócona

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

\ *TR*
Cechy znaków.

### <a name="return-value"></a>Wartość zwrócona

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

\ *TR*
Cechy znaków.

\ *lewo*
Odwołanie lvalue do obiektu `basic_ostream`.

*prawa*\
Odwołanie lvalue do obiektu `basic_ostream`.

### <a name="remarks"></a>Uwagi

Funkcja szablonu `swap` wykonuje `left.swap(right)`.

## <a name="see-also"></a>Zobacz też

[\<ostream >](../standard-library/ostream.md)
