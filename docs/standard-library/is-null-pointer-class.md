---
title: is_null_pointer, klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_null_pointer
helpviewer_keywords:
- is_null_pointer
ms.assetid: f3b3601b-f162-4803-a6e9-dabf5c3876cc
ms.openlocfilehash: 10979e790cb1f3e1ae3eace4f88a0328cb9a7f01
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480395"
---
# <a name="isnullpointer-class"></a>is_null_pointer, klasa

Sprawdza, czy typ jest std::nullptr_t.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_null_pointer;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *T* jest `std::nullptr_t`, w przeciwnym razie przechowuje wartość false.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
