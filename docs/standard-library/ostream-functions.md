---
title: '&lt;ostream&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ostream/std::swap
- ostream/std::endl
- ostream/std::ends
- ostream/std::flush
ms.assetid: d6e56cc0-c8df-4dbe-be10-98e14c35ed3a
caps.latest.revision: "15"
manager: ghogen
helpviewer_keywords:
- std::swap [C++]
- std::endl [C++]
- std::ends [C++]
- std::flush [C++]
ms.openlocfilehash: 9b9f64f67b1649c1c2f3d65f63636fd62601d06a
ms.sourcegitcommit: a7e4956c1150273e8dd39fda8b41655a6cf2cb98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2017
---
# <a name="ltostreamgt-functions"></a>&lt;ostream&gt; funkcji

Są to globalne szablonu funkcji zdefiniowanych w &lt;ostream&gt;. Dla funkcji Członkowskich [basic_ostream — klasa](basic-ostream-class.md) dokumentacji.

||||
|-|-|-|
|[endl](#endl)|[kończy się](#ends)|[Flush](#flush)|
|[swap](#swap)|

## <a name="endl"></a>endl

Przerywa wiersza i opróżnia bufor.

```cpp
template class<Elem, Tr> 
basic_ostream<Elem, Tr>& endl(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Parametry

*Element*  
Typ elementu.

*OSTR*  
Obiekt typu **basic_ostream —**.

*TR*  
Cechy znaków.

### <a name="return-value"></a>Wartość zwracana

Obiekt typu **basic_ostream —**.

### <a name="remarks"></a>Uwagi

Wywołania manipulatora *Ostr*.[ Umieść](../standard-library/basic-ostream-class.md#put)(*Ostr*.[ widen](../standard-library/basic-ios-class.md#widen)(\n)), a następnie wywołuje *Ostr*.[ Flush](../standard-library/basic-ostream-class.md#flush). Zwraca *Ostr*.

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

Kończy się ciągiem.

```cpp
template class<Elem, Tr> 
basic_ostream<Elem, Tr>& ends(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Parametry

*Element*  
Typ elementu.

*OSTR*  
Obiekt typu **basic_ostream —**.

*TR*  
Cechy znaków.

### <a name="return-value"></a>Wartość zwracana

Obiekt typu **basic_ostream —**.

### <a name="remarks"></a>Uwagi

Wywołania manipulatora *Ostr*.[ Umieść](../standard-library/basic-ostream-class.md#put)(*elementu*('\0')). Zwraca *Ostr*.

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

*Element*  
Typ elementu.

*OSTR*  
Obiekt typu **basic_ostream —**.

*TR*  
Cechy znaków.

### <a name="return-value"></a>Wartość zwracana

Obiekt typu **basic_ostream —**.

### <a name="remarks"></a>Uwagi

Wywołania manipulatora *Ostr*.[ Flush](../standard-library/basic-ostream-class.md#flush). Zwraca *Ostr*.

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

Zamienia wartości dwu **basic_ostream —** obiektów.

```cpp
template <class Elem, class Tr>
void swap(
   basic_ostream<Elem, Tr>& left,
   basic_ostream<Elem, Tr>& right);
```

### <a name="parameters"></a>Parametry

*Element*  
Typ elementu.

*TR*  
Cechy znaków.

*po lewej*  
Odwołania do wartości do **basic_ostream —** obiektu.

*prawo*  
Odwołania do wartości do **basic_ostream —** obiektu.

### <a name="remarks"></a>Uwagi

Funkcja szablonu **wymiany** wykonuje `left.swap(right)`.

## <a name="see-also"></a>Zobacz także

[\<ostream >](../standard-library/ostream.md)  
