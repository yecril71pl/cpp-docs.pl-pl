---
title: '&lt;operatory alokatorów&gt;'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: 7bc37e98ed85582cac8fc7ae21e54a6d5da9e06f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364962"
---
# <a name="ltallocatorsgt-operators"></a>&lt;operatory alokatorów&gt;

Są to funkcje operatora &lt;szablonu globalnego&gt;zdefiniowane w alokatorach . W przypadku funkcji operatora elementu członkowskiego klasy zobacz dokumentację klasy.

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

## <a name="operator"></a><a name="op_neq"></a>operator!=

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
|*Lewej*|Jeden z obiektów alokatora, które mają być testowane pod kątem nierówności.|
|*Prawo*|Jeden z obiektów alokatora, które mają być testowane pod kątem nierówności.|

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli obiekty alokatora nie są równe; **false,** jeśli obiekty alokatora są równe.

### <a name="remarks"></a>Uwagi

Operator szablonu `!(left == right)`zwraca plik .

## <a name="operator"></a><a name="op_eq_eq"></a>operator==

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
|*Lewej*|Jeden z obiektów alokatora, które mają być testowane pod kątem równości.|
|*Prawo*|Jeden z obiektów alokatora, które mają być testowane pod kątem równości.|

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli obiekty alokatora są równe; **false,** jeśli obiekty alokatora nie są równe.

### <a name="remarks"></a>Uwagi

Ten operator `left.equals(right)`szablonu zwraca plik .

## <a name="see-also"></a>Zobacz też

[\<>alokatorów](../standard-library/allocators-header.md)
