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
ms.openlocfilehash: 789839482e623e94172bbd55342d257c2b031614
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44109372"
---
# <a name="istriviallyconstructible-class"></a>is_trivially_constructible, klasa

Sprawdza, czy typ jest przypadku konstrukcyjną, gdy są używane określone typy argumentów.

## <a name="syntax"></a>Składnia

```cpp
template <class T, class... Args>
struct is_trivially_constructible;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ do zapytania.

*Args*<br/>
Typy argumentów, aby dopasować w Konstruktorze z *T*.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *T* jest przypadku konstrukcyjną, korzystając z typami argumentów w elemencie *Args*, w przeciwnym razie przechowuje wartość false. Typ *T* jest przypadku konstrukcyjną Jeśli definicja zmiennej `T t(std::declval<Args>()...);` jest poprawnie sformułowany, wiadomo, że do wywoływania nie nietrywialnymi operacji. Zarówno *T* i wszystkie typy w *Args* muszą być typami pełnymi **void**, lub tablic nieznany powiązane z.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
