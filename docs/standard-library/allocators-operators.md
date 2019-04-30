---
title: '&lt;allocators —&gt; operatorów'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: b7429e298cdf14d727fc481db6c4a3bf8574b5e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377899"
---
# <a name="ltallocatorsgt-operators"></a>&lt;allocators —&gt; operatorów

Są to funkcje operatora szablon globalny, które są zdefiniowane w &lt;buforów&gt;. Funkcje operatorów składowych klasy znajduje się w dokumentacji klasy.

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
|*left*|Jeden z obiektami alokatora, który ma zostać przetestowana pod kątem nierówności.|
|*right*|Jeden z obiektami alokatora, który ma zostać przetestowana pod kątem nierówności.|

### <a name="return-value"></a>Wartość zwracana

**wartość true,** obiektami alokatora nie są równe; **false** alokatora obiekty są równe.

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
|*left*|Jeden z obiektami alokatora, który ma zostać przetestowana pod kątem równości.|
|*right*|Jeden z obiektami alokatora, który ma zostać przetestowana pod kątem równości.|

### <a name="return-value"></a>Wartość zwracana

**wartość true,** obiektami alokatora są równe; **false** obiektami alokatora nie są równe.

### <a name="remarks"></a>Uwagi

Ten szablon operator zwraca `left.equals(right)`.

## <a name="see-also"></a>Zobacz także

[\<allocators>](../standard-library/allocators-header.md)
