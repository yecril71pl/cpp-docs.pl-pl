---
title: Klasa is_nothrow_constructible | Dokumentacja firmy Microsoft
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
- type_traits/std::is_nothrow_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_constructible
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 38c334524cc5965f187d5ec76f698e9ed275f8b0
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="isnothrowconstructible-class"></a>is_nothrow_constructible — klasa

Sprawdza, czy typem umożliwia konstrukcji, nie wiadomo throw, gdy określone typy argumentów są używane.

## <a name="syntax"></a>Składnia

```cpp
template <class T, class... Args>
struct is_nothrow_constructible;
```

### <a name="parameters"></a>Parametry

`T` Typ do zapytania.

`Args` Typy argumentów do dopasowania w konstruktora `T`.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu posiada wartość true Jeśli typ `T` jest umożliwia konstrukcji, korzystając z typami argumentów w `Args`i Konstruktor jest znana przez kompilator nie throw; w przeciwnym razie ma wartość false. Typ `T` umożliwia konstrukcji Jeśli definicja zmiennej `T t(std::declval<Args>()...);` jest poprawnie sformułowany. Zarówno `T` i wszystkie typy w `Args` musi być ukończone typy `void`, lub tablic z nieznanym powiązaniem.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
