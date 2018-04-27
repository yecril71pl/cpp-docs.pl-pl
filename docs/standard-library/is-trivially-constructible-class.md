---
title: Klasa is_trivially_constructible | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- type_traits/std::is_trivially_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_constructible
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f564ae5970f56690f493e26cbefebbdc34cfec61
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="istriviallyconstructible-class"></a>is_trivially_constructible — klasa

Sprawdza, czy typ jest trivially umożliwia konstrukcji, gdy określone typy argumentów są używane.

## <a name="syntax"></a>Składnia

```cpp
template <class T, class... Args>
struct is_trivially_constructible;
```

### <a name="parameters"></a>Parametry

`T` Typ do zapytania.

`Args` Typy argumentów do dopasowania w konstruktora `T`.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu posiada wartość true Jeśli typ `T` jest trivially umożliwia konstrukcji, korzystając z typami argumentów w `Args`, w przeciwnym razie ma wartość false. Typ `T` trivially umożliwia konstrukcji Jeśli definicja zmiennej `T t(std::declval<Args>()...);` jest poprawnie sformułowany i jest rozpoznawany do wywołania ma nieuproszczone operacji. Zarówno `T` i wszystkie typy w `Args` musi być ukończone typy `void`, lub tablic z nieznanym powiązaniem.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
