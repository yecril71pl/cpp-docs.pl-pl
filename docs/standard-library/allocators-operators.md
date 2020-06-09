---
title: '&lt;&gt;Operatory przytwórców'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: a21708ca090b0db561391308f347d90b77c62645
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623573"
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

**prawda** , jeśli obiekty alokatora nie są równe; **Fałsz** , jeśli obiekty alokatora są równe.

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

**ma wartość true** , jeśli obiekty alokatora są równe; **Fałsz** , jeśli obiekty alokatora nie są równe.

### <a name="remarks"></a>Uwagi

Ten operator szablonu zwraca wartość `left.equals(right)` .

## <a name="see-also"></a>Zobacz też

[\<allocators>](allocators-header.md)
