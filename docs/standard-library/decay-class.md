---
title: decay — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::decay
helpviewer_keywords:
- decay class
ms.assetid: 96baa2fd-c8e0-49af-be91-ba375ba7f9dc
ms.openlocfilehash: 3b22dfecb1162ce67a0d648197465115acb044ba
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688115"
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

*T* \
Typ do modyfikacji.

## <a name="remarks"></a>Uwagi

Użyj szablonu pozostałej w celu utworzenia typu wynikowego, tak jakby typ został przekazano przez wartość jako argument. Element typedef elementu członkowskiego szablonu klasy `type` przechowuje zmodyfikowany typ, który jest zdefiniowany w następujących etapach:

- Typ `U` jest zdefiniowany jako `remove_reference<T>::type`.

- Jeśli `is_array<U>::value` ma wartość true, modyfikowany typ `type` jest `remove_extent<U>::type *`.

- W przeciwnym razie, jeśli `is_function<U>::value` ma wartość true, modyfikowany typ `type` jest `add_pointer<U>::type`.

- W przeciwnym razie zmodyfikowano typ `type` jest `remove_cv<U>::type`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
