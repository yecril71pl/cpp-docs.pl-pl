---
title: is_nothrow_copy_assignable — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_copy_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_copy_assignable
ms.assetid: baa8abd6-4f53-489f-abba-8d5d5c53bbbc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6c5c5bdc1e944483071f0f1dcd53c3bc93eb6ed3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="isnothrowcopyassignable-class"></a>is_nothrow_copy_assignable — klasa

Sprawdza, czy typ ma operatora przypisania kopii, znany do kompilatora nie throw.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_nothrow_copy_assignable;
```

### <a name="parameters"></a>Parametry

`T` Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu jest spełniony dla typu referenceable `T` gdzie `is_nothrow_assignable<T&, const T&>` ma wartość PRAWDA; w przeciwnym razie posiada wartość false.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_nothrow_assignable, klasa](../standard-library/is-nothrow-assignable-class.md)<br/>
