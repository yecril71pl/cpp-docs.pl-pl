---
title: Klasa is_move_assignable
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_move_assignable
helpviewer_keywords:
- is_move_assignable
ms.assetid: f33137f2-0639-4912-8745-bc0f9fd18d28
ms.openlocfilehash: 8563db51eeb1988697b3e07a1a8673a777783e38
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456120"
---
# <a name="ismoveassignable-class"></a>Klasa is_move_assignable

Testuje, czy można przenieść typ.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>Parametry

*&* \
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Typ jest przesuwany do przypisania, jeśli odwołanie rvalue do typu może zostać przypisane do odwołania do typu. Predykat typu jest równoważny z `is_assignable<T&, T&&>`. Przenieś typy z możliwością przypisania zawierają typy skalarne i typy klas, które mają zdefiniowane przez użytkownika operatory przypisania przenoszenia.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
