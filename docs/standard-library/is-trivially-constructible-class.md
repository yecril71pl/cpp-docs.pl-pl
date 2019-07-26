---
title: Klasa is_trivially_constructible
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_constructible
helpviewer_keywords:
- is_trivially_constructible
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
ms.openlocfilehash: 6f177463b985d3e7b2f7ab7783f9c3db0dcd5722
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448012"
---
# <a name="istriviallyconstructible-class"></a>Klasa is_trivially_constructible

Testuje, czy typ jest bardzo konstrukcyjną, gdy są używane określone typy argumentów.

## <a name="syntax"></a>Składnia

```cpp
template <class T, class... Args>
struct is_trivially_constructible;
```

### <a name="parameters"></a>Parametry

*&* \
Typ do zapytania.

*Argumentów*\
Typy argumentów do dopasowania w konstruktorze *T*.

## <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *T* jest niekonstrukcyjnąy przy użyciu typów *argumentów w*argumentach, w przeciwnym razie ma wartość false. Typ *T* jest niekonstrukcyjnąy, jeśli definicja `T t(std::declval<Args>()...);` zmiennej jest poprawnie sformułowana i jest znana do wywołania braku prostych operacji. Zarówno *T* , jak i wszystkie typy w *args* muszą być pełnymi typami, **void**lub tablicami nieznanego powiązania.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
