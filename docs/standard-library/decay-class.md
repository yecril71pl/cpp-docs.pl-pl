---
title: decay — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::decay
dev_langs:
- C++
helpviewer_keywords:
- decay class
ms.assetid: 96baa2fd-c8e0-49af-be91-ba375ba7f9dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e0451b8565a4d021181d79d15437637e1b2f3b27
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="decay-class"></a>decay — Klasa

Tworzy typ jako przekazany przez wartość. Sprawia, że typem referencyjnym, wartością stałą, trwałej lub sprawia, że wskaźnik do typu z funkcją lub typem tablicy.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct decay;

template <class T>
using decay_t = typename decay<T>::type;
```

### <a name="parameters"></a>Parametry

`T` Typ do zmodyfikowania.

## <a name="remarks"></a>Uwagi

Szablon zanikania wygenerowało wynikowy typ tak, jakby typ został przekazany przez wartość jako argument. Typedef elementu członkowskiego szablonu klasy `type` zawiera typ zmodyfikowane, który jest zdefiniowany w następujących etapach:

- Typ `U` jest zdefiniowany jako `remove_reference<T>::type`.

- Jeśli `is_array<U>::value` ma wartość true, zmodyfikowany typ `type` jest `remove_extent<U>::type *`.

- W przeciwnym razie, jeśli `is_function<U>::value` ma wartość true, zmodyfikowany typ `type` jest `add_pointer<U>::type`.

- W przeciwnym razie zmodyfikowany typ `type` jest `remove_cv<U>::type`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
