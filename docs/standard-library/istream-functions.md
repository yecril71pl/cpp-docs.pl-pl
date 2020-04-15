---
title: '&lt;funkcje&gt; istream'
ms.date: 11/04/2016
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
ms.openlocfilehash: 3d647c7b05a3868ec0359410cc0e703306b874ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363081"
---
# <a name="ltistreamgt-functions"></a>&lt;funkcje&gt; istream

|||
|-|-|
|[Wymiany](#istream_swap)|[ws](#ws)|

## <a name="swap"></a><a name="istream_swap"></a>Wymiany

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

*Lewej*\
Strumień.

*Prawo*\
Strumień.

## <a name="ws"></a><a name="ws"></a>Ws

Pomija odstęp w strumieniu.

```cpp
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```

### <a name="parameters"></a>Parametry

*_Istr*\
Strumień.

### <a name="return-value"></a>Wartość zwracana

Strumień.

### <a name="remarks"></a>Uwagi

Manipulator wyodrębnia i odrzuca `ch` wszelkie elementy, dla których [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype** \< **Elem**> >( [getloc](../standard-library/ios-base-class.md#getloc)). **jest**( **ctype** \< **Elem**>:: **space**, **ch**) jest prawdą.

Funkcja wywołuje [setstate](../standard-library/basic-ios-class.md#setstate) **(eofbit),** jeśli napotka koniec pliku podczas wyodrębniania elementów. Zwraca *_Istr*.

### <a name="example"></a>Przykład

Zobacz [>>operatora,](../standard-library/istream-operators.md#op_gt_gt) aby uzyskać `ws`przykład użycia pliku .

## <a name="see-also"></a>Zobacz też

[\<>istream](../standard-library/istream.md)
