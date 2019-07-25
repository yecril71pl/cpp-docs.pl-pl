---
title: is_error_code_enum — Klasa
ms.date: 11/04/2016
f1_keywords:
- system_error/std::is_error_code_enum
helpviewer_keywords:
- is_error_code_enum class
ms.assetid: cee5be2d-7c20-4cec-a352-1ab8b7d32601
ms.openlocfilehash: 4080c62034b224a9553eca2787aa1c2f2cf69ab8
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454631"
---
# <a name="iserrorcodeenum-class"></a>is_error_code_enum — Klasa

Reprezentuje predykat typu, który testuje Wyliczenie [error_code](../standard-library/error-code-class.md) .

## <a name="syntax"></a>Składnia

```cpp
template <_Enum>
    class is_error_code_enum;
```

## <a name="remarks"></a>Uwagi

Wystąpienie tego predykatu [typu](../standard-library/type-traits.md) ma wartość true, jeśli typ `_Enum` jest wartością wyliczenia odpowiednią do przechowywania w obiekcie typu. `error_code`

Dozwolone jest dodanie specjalizacji do tego typu dla typów zdefiniowanych przez użytkownika.

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
