---
title: '&lt;allocators —&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
dev_langs:
- C++
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
caps.latest.revision: 11
manager: ghogen
ms.openlocfilehash: d6d69d07c8b16d2749c7ac62eb290f180b1e1b09
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ltallocatorsgt-operators"></a>&lt;allocators —&gt; operatory

Są to globalne szablonu funkcji operatora zdefiniowanych w &lt;allocators —&gt;. Funkcje operatorów elementu członkowskiego klasy znajduje się w dokumentacji klasy.

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  operator! =

Testuje pod kątem nierówności pomiędzy obiektami alokatora określonej klasy.

```cpp
template <class Type, class Sync>
bool operator!=(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`left`|Jeden z obiektów alokatora pod kątem nierówności.|
|`right`|Jeden z obiektów alokatora pod kątem nierówności.|

### <a name="return-value"></a>Wartość zwracana

**wartość true,** alokatora obiekty nie są równe; **false** alokatora obiekty są równe.

### <a name="remarks"></a>Uwagi

Operator szablonu zwraca `!(left == right)`.

## <a name="op_eq_eq"></a>  operator ==

Testuje pod kątem równości pomiędzy obiektami alokatora określonej klasy.

```cpp
template <class Type, class Sync>
bool operator==(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`left`|Jeden z obiektów alokatora pod kątem równości.|
|`right`|Jeden z obiektów alokatora pod kątem równości.|

### <a name="return-value"></a>Wartość zwracana

**wartość true,** alokatora obiekty są równe; **false** alokatora obiekty nie są równe.

### <a name="remarks"></a>Uwagi

Ten operator szablonu zwraca `left.equals(right)`.

## <a name="see-also"></a>Zobacz także

[\<allocators — >](../standard-library/allocators-header.md)
