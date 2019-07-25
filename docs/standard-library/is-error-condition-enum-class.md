---
title: is_error_condition_enum — Klasa
ms.date: 11/04/2016
f1_keywords:
- system_error/std::is_error_condition_enum
helpviewer_keywords:
- is_error_condition_enum class
ms.assetid: 752bb87a-c61c-4304-9254-5aaf228b59c0
ms.openlocfilehash: c40f8f6eb93a33098cfbcf8133f08c56285abb43
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452602"
---
# <a name="iserrorconditionenum-class"></a>is_error_condition_enum — Klasa

Reprezentuje predykat typu, który testuje Wyliczenie [error_condition](../standard-library/error-condition-class.md) .

## <a name="syntax"></a>Składnia

```cpp
template <_Enum>
    class is_error_condition_enum;
```

## <a name="remarks"></a>Uwagi

Wystąpienie tego predykatu [typu](../standard-library/type-traits.md) ma wartość true, jeśli typ `_Enum` jest wartością wyliczenia odpowiednią do przechowywania w obiekcie typu. `error_condition`

Dozwolone jest dodanie specjalizacji do tego typu dla typów zdefiniowanych przez użytkownika.

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
