---
title: Klasa is_constructible
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_constructible
helpviewer_keywords:
- is_constructible
ms.assetid: 7cdec5ff-73cf-4f78-a9db-ced2e9c0fd7f
ms.openlocfilehash: a968efa5a867a3fd0e60594784cdb11122a974b2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222410"
---
# <a name="is_constructible-class"></a>Klasa is_constructible

Testuje, czy typ jest konstrukcyjną, gdy są używane określone typy argumentów.

## <a name="syntax"></a>Składnia

```cpp
template <class T, class... Args>
struct is_constructible;
```

### <a name="parameters"></a>Parametry

*&*\
Typ do zapytania.

*Argumentów*\
Typy argumentów do dopasowania w konstruktorze *T*.

## <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *T* jest konstrukcyjną przy użyciu typów argumentów w *args*, w przeciwnym razie ma wartość false. Typ *T* jest konstrukcyjną, jeśli definicja zmiennej `T t(std::declval<Args>()...);` jest poprawnie sformułowana. Zarówno *T* , jak i wszystkie typy w *args* muszą być pełnymi typami **`void`** lub tablicami nieznanego powiązania.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<type_traits>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
