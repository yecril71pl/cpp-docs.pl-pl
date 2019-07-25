---
title: Klasa is_nothrow_constructible
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_constructible
helpviewer_keywords:
- is_nothrow_constructible
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
ms.openlocfilehash: 7ec4fc3ef5d9a799d5d77124870fbb337061c94c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455989"
---
# <a name="isnothrowconstructible-class"></a>Klasa is_nothrow_constructible

Testuje, czy typ jest konstrukcyjną i nie jest zgłaszany, gdy są używane określone typy argumentów.

## <a name="syntax"></a>Składnia

```cpp
template <class T, class... Args>
struct is_nothrow_constructible;
```

### <a name="parameters"></a>Parametry

*&* \
Typ do zapytania.

*Argumentów*\
Typy argumentów do dopasowania w konstruktorze *T*.

## <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *T* jest konstrukcyjną przy użyciu typów argumentów w *args*, a Konstruktor jest znany przez kompilator, aby nie zgłaszać; w przeciwnym razie zawiera wartość false. Typ *T* jest konstrukcyjną, jeśli definicja `T t(std::declval<Args>()...);` zmiennej jest poprawnie sformułowana. Zarówno *T* , jak i wszystkie typy w *args* muszą być pełnymi typami, **void**lub tablicami nieznanego powiązania.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
