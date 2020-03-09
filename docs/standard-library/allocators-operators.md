---
title: '&lt;przydzielania&gt; operatory'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: b7429e298cdf14d727fc481db6c4a3bf8574b5e7
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78875961"
---
# <a name="ltallocatorsgt-operators"></a>&lt;przydzielania&gt; operatory

Są to funkcje operatora szablonu globalnego zdefiniowane w &lt;przydzielania&gt;. Aby uzyskać funkcje operatora składowej klasy, zobacz dokumentację klasy.

|||
|-|-|
|[operator!=](#op_neq)|[operator = =](#op_eq_eq)|

## <a name="op_neq"></a>operator! =

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

Operator szablonu zwraca `!(left == right)`.

## <a name="op_eq_eq"></a>operator = =

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

Ten operator szablonu zwraca `left.equals(right)`.

## <a name="see-also"></a>Zobacz także

[\<przydzielania >](../standard-library/allocators-header.md)
