---
title: '&lt;&gt;Operatory przytwórców'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: 969c9f8e05a9fafad4d3a1102060e2b3d4d0eb2e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844785"
---
# <a name="ltallocatorsgt-operators"></a>&lt;&gt;Operatory przytwórców

Są to funkcje operatora szablonu globalnego zdefiniowane w przystawce &lt; &gt; . Aby uzyskać funkcje operatora składowej klasy, zobacz dokumentację klasy.

[operator! =](#op_neq)\
[operator = =](#op_eq_eq)

## <a name="operator"></a><a name="op_neq"></a> operator! =

Testuje pod kątem nierówności pomiędzy obiektami alokatora określonej klasy.

```cpp
template <class Type, class Sync>
bool operator!=(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Jeden z obiektów alokatora, który ma być testowany pod kątem nierówności.

*Kliknij*\
Jeden z obiektów alokatora, który ma być testowany pod kątem nierówności.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli obiekty programu przydzielania nie są równe; **`false`** Jeśli obiekty alokatora są równe.

### <a name="remarks"></a>Uwagi

Operator szablonu zwraca wartość `!(left == right)` .

## <a name="operator"></a><a name="op_eq_eq"></a> operator = =

Testuje pod kątem równości pomiędzy obiektami alokatora określonej klasy.

```cpp
template <class Type, class Sync>
bool operator==(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Jeden z obiektów alokatora, który ma być testowany pod kątem równości.

*Kliknij*\
Jeden z obiektów alokatora, który ma być testowany pod kątem równości.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli obiekty alokatora są równe; **`false`** Jeśli obiekty alokatora nie są równe.

### <a name="remarks"></a>Uwagi

Ten operator szablonu zwraca wartość `left.equals(right)` .

## <a name="see-also"></a>Zobacz też

[\<allocators>](allocators-header.md)
