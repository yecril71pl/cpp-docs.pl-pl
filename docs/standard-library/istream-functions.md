---
title: '&lt;&gt;funkcje IStream'
ms.date: 11/04/2016
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
ms.openlocfilehash: 6d1fede2726d3d8f5dd678b95fd7a22a301ea95a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840976"
---
# <a name="ltistreamgt-functions"></a>&lt;&gt;funkcje IStream

[wymiany](#istream_swap)\
[ws](#ws)

## <a name="swap"></a><a name="istream_swap"></a> wymiany

Wymienia elementy dwóch obiektów strumienia.

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

*lewym*\
Strumień.

*Kliknij*\
Strumień.

## <a name="ws"></a><a name="ws"></a> WS

Pomija biały znak w strumieniu.

```cpp
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```

### <a name="parameters"></a>Parametry

*_Istr*\
Strumień.

### <a name="return-value"></a>Wartość zwracana

Strumień.

### <a name="remarks"></a>Uwagi

Manipulator wyodrębnia i odrzuca wszystkie elementy, `ch` dla których [use_facet](../standard-library/basic-filebuf-class.md#open) <  **CType** \< **Elem**> > ( [getloc](../standard-library/ios-base-class.md#getloc)). **is**( **CType** \< **Elem**> :: **Space**, **ch**) ma wartość true.

Funkcja wywołuje metodę [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**), jeśli napotka koniec pliku podczas wyodrębniania elementów. Zwraca *_Istr*.

### <a name="example"></a>Przykład

Zobacz [>>operatora ](../standard-library/istream-operators.md#op_gt_gt) , aby zapoznać się z przykładem użycia `ws` .

## <a name="see-also"></a>Zobacz też

[\<istream>](../standard-library/istream.md)
