---
title: decay — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::decay
helpviewer_keywords:
- decay class
ms.assetid: 96baa2fd-c8e0-49af-be91-ba375ba7f9dc
ms.openlocfilehash: 73b9e2d8ef9a14830c13ee3f6566137bb51e939d
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450641"
---
# <a name="decay-class"></a>decay — Klasa

Tworzy typ jako przekazaną przez wartość. Sprawia, że typ nie jest odwołaniem, niestałym, nietrwałym lub tworzy wskaźnik do typu z funkcji lub typu tablicy.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct decay;

template <class T>
using decay_t = typename decay<T>::type;
```

### <a name="parameters"></a>Parametry

*&* \
Typ do modyfikacji.

## <a name="remarks"></a>Uwagi

Użyj szablonu pozostałej w celu utworzenia typu wynikowego, tak jakby typ został przekazano przez wartość jako argument. Składowa klasy szablonu typedef `type` zawiera zmodyfikowany typ, który jest zdefiniowany w następujących etapach:

- Typ `U` jest zdefiniowany jako `remove_reference<T>::type`.

- Jeśli `is_array<U>::value` ma wartość true, modyfikowany `type` jest `remove_extent<U>::type *`typ.

- W przeciwnym razie `is_function<U>::value` , jeśli ma wartość true, `type` zmodyfikowany `add_pointer<U>::type`typ to.

- W przeciwnym razie zmodyfikowany typ `type` to `remove_cv<U>::type`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
