---
title: decay — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::decay
helpviewer_keywords:
- decay class
ms.assetid: 96baa2fd-c8e0-49af-be91-ba375ba7f9dc
ms.openlocfilehash: 23c2cff37e67e78ba68c37468c110d7a3725b785
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394066"
---
# <a name="decay-class"></a>decay — Klasa

Tworzy typ, jak przekazać przez wartość. Tworzy typ niebędący odniesieniem, niestały, trwałej lub tworzy wskaźnik do typu z funkcją lub typem tablicowym.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct decay;

template <class T>
using decay_t = typename decay<T>::type;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ do modyfikacji.

## <a name="remarks"></a>Uwagi

Wybierz szablon zanikania i generuje wynikowy typ tak, jakby typ został przekazany przez wartość jako argument. Typedef składowej klasy szablonu `type` ma zmodyfikowany typ, który jest zdefiniowany w następujących etapach:

- Typ `U` jest zdefiniowany jako `remove_reference<T>::type`.

- Jeśli `is_array<U>::value` ma wartość true, zmodyfikowany typ `type` jest `remove_extent<U>::type *`.

- W przeciwnym razie, jeśli `is_function<U>::value` ma wartość true, zmodyfikowany typ `type` jest `add_pointer<U>::type`.

- W przeciwnym razie zmodyfikowany typ `type` jest `remove_cv<U>::type`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
