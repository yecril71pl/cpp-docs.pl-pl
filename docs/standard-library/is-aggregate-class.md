---
title: is_aggregate klasy
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_aggregate
helpviewer_keywords:
- is_aggregate
ms.openlocfilehash: 7d979d4e4019ada12b72fb563c0b969fffe2c12d
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268049"
---
# <a name="isaggregate-class"></a>is_aggregate klasy

Sprawdza, czy typ jest typem klasy oznaczone `aggregate`.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_aggregate;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *T* typu klasy jest oznaczony `aggregate`, w przeciwnym razie przechowuje wartość false. Jeśli *T* jest typem klasy musi być typem kompletnym.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
