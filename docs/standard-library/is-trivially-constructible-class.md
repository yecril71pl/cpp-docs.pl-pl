---
title: is_trivially_constructible, klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_constructible
helpviewer_keywords:
- is_trivially_constructible
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
ms.openlocfilehash: c83bea8be5c88876ffa25337464caa62b998ab45
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628842"
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
