---
title: is_error_condition_enum — Klasa
ms.date: 11/04/2016
f1_keywords:
- system_error/std::is_error_condition_enum
helpviewer_keywords:
- is_error_condition_enum class
ms.assetid: 752bb87a-c61c-4304-9254-5aaf228b59c0
ms.openlocfilehash: 1b5b55431db806bb109a58199ad9d2d7c16f38ff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612722"
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

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<system_error >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[<system_error>](../standard-library/system-error.md)<br/>
