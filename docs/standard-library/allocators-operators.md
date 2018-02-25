---
title: "&lt;allocators —&gt; operatory | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
dev_langs:
- C++
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: e84f3c66adaf4d4d0cd5af68ee51841025bd89b2
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ltallocatorsgt-operators"></a>&lt;allocators —&gt; operatory

Są to globalne szablonu funkcji operatora zdefiniowanych w &lt;allocators —&gt;. Funkcje operatorów elementu członkowskiego klasy znajduje się w dokumentacji klasy.

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

##  <a name="op_neq"></a>  operator! =

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

##  <a name="op_eq_eq"></a>  operator ==

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

[\<allocators>](../standard-library/allocators-header.md)  
