---
title: Klasa is_constructible | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_constructible
ms.assetid: 7cdec5ff-73cf-4f78-a9db-ced2e9c0fd7f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2461d7986e87bed846d09d6e3938a339237c8f8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="isconstructible-class"></a>is_constructible — klasa

Sprawdza, czy typ jest umożliwia konstrukcji, gdy określone typy argumentów są używane.

## <a name="syntax"></a>Składnia

```cpp
template <class T, class... Args>
struct is_constructible;
```

### <a name="parameters"></a>Parametry

`T` Typ do zapytania.

`Args` Typy argumentów do dopasowania w konstruktora `T`.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu posiada wartość true Jeśli typ `T` jest umożliwia konstrukcji, korzystając z typami argumentów w `Args`, w przeciwnym razie ma wartość false. Typ `T` umożliwia konstrukcji Jeśli definicja zmiennej `T t(std::declval<Args>()...);` jest poprawnie sformułowany. Zarówno `T` i wszystkie typy w `Args` musi być ukończone typy `void`, lub tablic z nieznanym powiązaniem.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
