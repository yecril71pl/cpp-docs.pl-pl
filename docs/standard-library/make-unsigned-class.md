---
title: make_unsigned — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::make_unsigned
helpviewer_keywords:
- make_unsigned class
- make_unsigned
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
ms.openlocfilehash: 4c0224bd5fd7dc8c6589ae474bb9acb9a8f09cf6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456321"
---
# <a name="makeunsigned-class"></a>make_unsigned — Klasa

Ustawia typ lub najmniejszy typ bez znaku, który jest większy niż lub równy rozmiarowi do typu.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct make_unsigned;

template <class T>
using make_unsigned_t = typename make_unsigned<T>::type;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*T*|Typ do modyfikacji.|

## <a name="remarks"></a>Uwagi

Wystąpienie modyfikatora typu zawiera zmodyfikowany typ, `is_unsigned<T>` *który ma wartość* true. W przeciwnym razie jest to najmniejszy podpisany `ST` typ, `sizeof (T) <= sizeof (ST)`dla którego.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
