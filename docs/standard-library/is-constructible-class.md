---
title: is_constructible Class
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_constructible
helpviewer_keywords:
- is_constructible
ms.assetid: 7cdec5ff-73cf-4f78-a9db-ced2e9c0fd7f
ms.openlocfilehash: c921efd5b7e12873ce986952029ae39f118ad763
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62336858"
---
# <a name="isconstructible-class"></a>is_constructible Class

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
