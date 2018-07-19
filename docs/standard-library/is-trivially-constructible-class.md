---
title: is_trivially_constructible, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_constructible
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f73559503ad427c9b7eb513d4164d3348c652948
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954750"
---
# <a name="istriviallyconstructible-class"></a>is_trivially_constructible, klasa

Sprawdza, czy typ jest przypadku konstrukcyjną, gdy są używane określone typy argumentów.

## <a name="syntax"></a>Składnia

```cpp
template <class T, class... Args>
struct is_trivially_constructible;
```

### <a name="parameters"></a>Parametry

*T* typ do zapytania.

*Argumenty* typy argumentów, aby dopasować w Konstruktorze z *T*.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *T* jest przypadku konstrukcyjną, korzystając z typami argumentów w elemencie *Args*, w przeciwnym razie przechowuje wartość false. Typ *T* jest przypadku konstrukcyjną Jeśli definicja zmiennej `T t(std::declval<Args>()...);` jest poprawnie sformułowany, wiadomo, że do wywoływania nie nietrywialnymi operacji. Zarówno *T* i wszystkie typy w *Args* muszą być typami pełnymi **void**, lub tablic nieznany powiązane z.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
