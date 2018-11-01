---
title: '&lt;IStream&gt; funkcji'
ms.date: 11/04/2016
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
ms.openlocfilehash: b590559b01bb8f5db21fca9f78d220d8bad5c27e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537647"
---
# <a name="ltistreamgt-functions"></a>&lt;IStream&gt; funkcji

|||
|-|-|
|[swap](#istream_swap)|[ws](#ws)|

## <a name="istream_swap"></a>  swap

Zamienia elementy z dwóch obiektów strumienia.

```cpp
template <class Elem, class Tr>
void swap(
    basic_istream<Elem, Tr>& left,
    basic_istream<Elem, Tr>& right);

template <class Elem, class Tr>
void swap(
    basic_iostream<Elem, Tr>& left,
    basic_iostream<Elem, Tr>& right);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Strumień.

*right*<br/>
Strumień.

## <a name="ws"></a>  ws

Pomija biały znak w strumieniu.

```cpp
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```

### <a name="parameters"></a>Parametry

*_Istr*<br/>
Strumień.

### <a name="return-value"></a>Wartość zwracana

Strumień.

### <a name="remarks"></a>Uwagi

Manipulator wyodrębnia i odrzuca wszelkie elementy `ch` dla którego [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype** \< **Elem**>> ( [getloc —](../standard-library/ios-base-class.md#getloc)). **jest**( **ctype** \< **Elem**>:: **miejsca**, **ch**) ma wartość true.

Wywołania funkcji [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**) w przypadku wykrycia koniec pliku podczas wyodrębniania elementów. Zwraca *_Istr*.

### <a name="example"></a>Przykład

Zobacz [operator >>](../standard-library/istream-operators.md#op_gt_gt) na przykład za pomocą `ws`.

## <a name="see-also"></a>Zobacz także

[\<istream>](../standard-library/istream.md)<br/>
