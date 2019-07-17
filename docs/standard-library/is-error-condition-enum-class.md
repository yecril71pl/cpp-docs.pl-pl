---
title: is_error_condition_enum — Klasa
ms.date: 11/04/2016
f1_keywords:
- system_error/std::is_error_condition_enum
helpviewer_keywords:
- is_error_condition_enum class
ms.assetid: 752bb87a-c61c-4304-9254-5aaf228b59c0
ms.openlocfilehash: 213970d6260eaf55ac1bd678e6317cf2346ed9bc
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245179"
---
# <a name="iserrorconditionenum-class"></a>is_error_condition_enum — Klasa

Reprezentuje typu predykatu, który sprawdza, czy [error_condition](../standard-library/error-condition-class.md) wyliczenia.

## <a name="syntax"></a>Składnia

```cpp
template <_Enum>
    class is_error_condition_enum;
```

## <a name="remarks"></a>Uwagi

Wystąpienie tego elementu [predykatu typów](../standard-library/type-traits.md) ma wartość true, jeśli typ `_Enum` jest wartością wyliczenia odpowiedniego do przechowywania w obiekcie typu `error_condition`.

Jest dozwolone, aby dodać specjalizacje tego typu dla typów zdefiniowanych przez użytkownika.

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
