---
title: '&lt;funkcje&gt; strumienia'
ms.date: 11/04/2016
f1_keywords:
- sstream/std::swap
ms.assetid: bc9607e8-7c6b-44ef-949b-19e917b450ad
ms.openlocfilehash: 707d35123797b84b2b7cef1d1cfd9005e4becb1c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865924"
---
# <a name="ltsstreamgt-functions"></a>&lt;funkcje&gt; strumienia

||
|-|
|[wymiany](#sstream_swap)|

## <a name="sstream_swap"></a>wymiany

Wymienia wartości między dwoma obiektami `sstream`.

```cpp
template <class Elem, class Tr, class Alloc>
void swap(
    basic_stringbuf<Elem, Tr, Alloc>& left,
    basic_stringbuf<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>
void swap(
    basic_istringstream<Elem, Tr, Alloc>& left,
    basic_istringstream<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>
void swap(
    basic_ostringstream<Elem, Tr, Alloc>& left,
    basic_ostringstream<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>
void swap(
    basic_stringstream<Elem, Tr, Alloc>& left,
    basic_stringstream<Elem, Tr, Alloc>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*lewym*|Odwołanie do obiektu `sstream`.|
|*Kliknij*|Odwołanie do obiektu `sstream`.|

### <a name="remarks"></a>Uwagi

Funkcja Template wykonuje `left.swap(right)`.

## <a name="see-also"></a>Zobacz też

[\<strumienia >](../standard-library/sstream.md)
