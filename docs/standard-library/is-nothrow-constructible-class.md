---
title: Klasa is_nothrow_constructible
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_constructible
helpviewer_keywords:
- is_nothrow_constructible
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
ms.openlocfilehash: e52b16965d849f992731c4ff4254fd218b944269
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217756"
---
# <a name="is_nothrow_constructible-class"></a>Klasa is_nothrow_constructible

Testuje, czy typ jest konstrukcyjną i nie jest zgłaszany, gdy są używane określone typy argumentów.

## <a name="syntax"></a>Składnia

```cpp
template <class T, class... Args>
struct is_nothrow_constructible;
```

### <a name="parameters"></a>Parametry

*&*\
Typ do zapytania.

*Argumentów*\
Typy argumentów do dopasowania w konstruktorze *T*.

## <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *T* jest konstrukcyjną przy użyciu typów argumentów w *args*, a Konstruktor jest znany przez kompilator, aby nie zgłaszać; w przeciwnym razie zawiera wartość false. Typ *T* jest konstrukcyjną, jeśli definicja zmiennej `T t(std::declval<Args>()...);` jest poprawnie sformułowana. Zarówno *T* , jak i wszystkie typy w *args* muszą być pełnymi typami **`void`** lub tablicami nieznanego powiązania.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<type_traits>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
