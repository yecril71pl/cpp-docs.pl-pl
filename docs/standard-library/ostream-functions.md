---
title: '&lt;ostream&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 494c750ec80000ef9090824e0436f6e443593847
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107617"
---
# <a name="ltostreamgt-functions"></a>&lt;ostream&gt; funkcji

Są to funkcje globalne szablonu, zdefiniowanych w &lt;ostream&gt;. Dla funkcji składowych [basic_ostream — klasa](basic-ostream-class.md) dokumentacji.

||||
|-|-|-|
|[endl](#endl)|[kończy się](#ends)|[flush](#flush)|
|[swap](#swap)|

## <a name="endl"></a>endl

Kończy działanie wiersza i opróżnia bufor.

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& endl(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Parametry

*Elem*<br/>
Typ elementu.

*Ostr*<br/>
Obiekt typu **basic_ostream**.

*TR*<br/>
Cechy znaków.

### <a name="return-value"></a>Wartość zwracana

Obiekt typu **basic_ostream**.

### <a name="remarks"></a>Uwagi

Wywołania manipulator *Ostr*.[ Umieść](../standard-library/basic-ostream-class.md#put)(*Ostr*.[ mogą zostać poszerzone](../standard-library/basic-ios-class.md#widen)('\n')), a następnie wywołuje *Ostr*.[ Flush](../standard-library/basic-ostream-class.md#flush). Zwraca *Ostr*.

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

*Elem*<br/>
Typ elementu.

*Ostr*<br/>
Obiekt typu `basic_ostream`.

*TR*<br/>
Cechy znaków.

### <a name="return-value"></a>Wartość zwracana

Obiekt typu `basic_ostream`.

### <a name="remarks"></a>Uwagi

Wywołania manipulator *Ostr*.[ Umieść](../standard-library/basic-ostream-class.md#put)(*Elem*('\0')). Zwraca *Ostr*.

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

*Elem*<br/>
Typ elementu.

*Ostr*<br/>
Obiekt typu `basic_ostream`.

*TR*<br/>
Cechy znaków.

### <a name="return-value"></a>Wartość zwracana

Obiekt typu `basic_ostream`.

### <a name="remarks"></a>Uwagi

Wywołania manipulator *Ostr*.[ Flush](../standard-library/basic-ostream-class.md#flush). Zwraca *Ostr*.

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

Wymienia dwie wartości `basic_ostream` obiektów.

```cpp
template <class Elem, class Tr>
void swap(
   basic_ostream<Elem, Tr>& left,
   basic_ostream<Elem, Tr>& right);
```

### <a name="parameters"></a>Parametry

*Elem*<br/>
Typ elementu.

*TR*<br/>
Cechy znaków.

*left*<br/>
Odwołania wartościowanego lewostronnie do `basic_ostream` obiektu.

*right*<br/>
Odwołania wartościowanego lewostronnie do `basic_ostream` obiektu.

### <a name="remarks"></a>Uwagi

Funkcja szablonu `swap` wykonuje `left.swap(right)`.

## <a name="see-also"></a>Zobacz także

[\<ostream>](../standard-library/ostream.md)
