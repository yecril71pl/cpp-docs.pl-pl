---
title: '&lt;&gt;Operatory przytwórców'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: 7d22e550c7054c2197163f2edf829ec17a85a145
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87204563"
---
# <a name="ltallocatorsgt-operators"></a>&lt;&gt;Operatory przytwórców

Są to funkcje operatora szablonu globalnego zdefiniowane w przystawce &lt; &gt; . Aby uzyskać funkcje operatora składowej klasy, zobacz dokumentację klasy.

|||
|-|-|
|[operator! =](#op_neq)|[operator = =](#op_eq_eq)|

## <a name="operator"></a><a name="op_neq"></a>operator! =

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
|*lewym*|Jeden z obiektów alokatora, który ma być testowany pod kątem nierówności.|
|*Kliknij*|Jeden z obiektów alokatora, który ma być testowany pod kątem nierówności.|

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli obiekty programu przydzielania nie są równe; **`false`** Jeśli obiekty alokatora są równe.

### <a name="remarks"></a>Uwagi

Operator szablonu zwraca wartość `!(left == right)` .

## <a name="operator"></a><a name="op_eq_eq"></a>operator = =

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
|*lewym*|Jeden z obiektów alokatora, który ma być testowany pod kątem równości.|
|*Kliknij*|Jeden z obiektów alokatora, który ma być testowany pod kątem równości.|

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli obiekty alokatora są równe; **`false`** Jeśli obiekty alokatora nie są równe.

### <a name="remarks"></a>Uwagi

Ten operator szablonu zwraca wartość `left.equals(right)` .

## <a name="see-also"></a>Zobacz także

[\<allocators>](allocators-header.md)
