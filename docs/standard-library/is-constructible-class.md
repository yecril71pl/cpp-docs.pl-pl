---
title: is_constructible, klasa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: f94390b96770a84b35de67f4d3a38644132d8ce8
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107445"
---
# <a name="isconstructible-class"></a>is_constructible, klasa

Sprawdza, czy typ jest konstrukcyjną, gdy są używane określone typy argumentów.

## <a name="syntax"></a>Składnia

```cpp
template <class T, class... Args>
struct is_constructible;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ do zapytania.

*Args*<br/>
Typy argumentów, aby dopasować w Konstruktorze z *T*.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *T* jest konstrukcyjną, korzystając z typami argumentów w elemencie *Args*, w przeciwnym razie przechowuje wartość false. Typ *T* jest konstrukcyjną Jeśli definicja zmiennej `T t(std::declval<Args>()...);` jest poprawnie sformułowany. Zarówno *T* i wszystkie typy w *Args* muszą być typami pełnymi **void**, lub tablic nieznany powiązane z.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
