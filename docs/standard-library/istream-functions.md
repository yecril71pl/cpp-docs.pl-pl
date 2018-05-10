---
title: '&lt;IStream&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6310281aa86c48ae0a8b0fb313e79994d0b9b538
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="ltistreamgt-functions"></a>&lt;IStream&gt; funkcji

|||
|-|-|
|[swap](#istream_swap)|[ws](#ws)|

## <a name="istream_swap"></a>  Swap

Zamienia elementy dwa obiekty stream.

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

`left` Strumień.

`right` Strumień.

## <a name="ws"></a>  ws

Pomija biały znak w strumieniu.

```cpp
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```

### <a name="parameters"></a>Parametry

`_Istr` Strumień.

### <a name="return-value"></a>Wartość zwracana

Strumień.

### <a name="remarks"></a>Uwagi

Manipulatora wyodrębnia i odrzuca wszystkie elementy `ch` dla którego [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype** \< **elementu**>> ( [getloc](../standard-library/ios-base-class.md#getloc)). **jest**( **ctype** \< **elementu**>:: **miejsca**, **ch**) ma wartość true.

Wywołania funkcji [metoda setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**) w przypadku wykrycia koniec pliku podczas wyodrębniania elementów. Zwraca `_Istr`.

### <a name="example"></a>Przykład

Zobacz [operator >>](../standard-library/istream-operators.md#op_gt_gt) przykład przy użyciu `ws`.

## <a name="see-also"></a>Zobacz także

[\<istream>](../standard-library/istream.md)<br/>
