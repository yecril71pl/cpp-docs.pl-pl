---
title: '&lt;funkcje&gt; IStream'
ms.date: 11/04/2016
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
ms.openlocfilehash: fc512558969bc25d2b16afa2b93219e13d0b28ca
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874836"
---
# <a name="ltistreamgt-functions"></a>&lt;funkcje&gt; IStream

|||
|-|-|
|[wymiany](#istream_swap)|[WS](#ws)|

## <a name="istream_swap"></a>wymiany

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

\ *lewo*
Strumień.

*prawa*\
Strumień.

## <a name="ws"></a>WS

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

Manipulator wyodrębnia i odrzuca wszystkie elementy `ch`, dla których [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype**\< **elem**> > ( [getloc](../standard-library/ios-base-class.md#getloc)). **is**( **ctype**\< **elem**>:: **Space**, **ch**) ma wartość true.

Funkcja wywołuje metodę [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**), jeśli napotka koniec pliku podczas wyodrębniania elementów. Zwraca *_Istr*.

### <a name="example"></a>Przykład

Zobacz [> operatora >](../standard-library/istream-operators.md#op_gt_gt) , aby zapoznać się z przykładem użycia `ws`.

## <a name="see-also"></a>Zobacz też

[\<IStream >](../standard-library/istream.md)
