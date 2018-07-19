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
ms.openlocfilehash: 5433c9ff76b8b6f218cfff5e5fd39a0ad7166613
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963618"
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

*T* typ do modyfikacji.

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
