---
title: is_error_code_enum — Klasa
ms.date: 11/04/2016
f1_keywords:
- system_error/std::is_error_code_enum
helpviewer_keywords:
- is_error_code_enum class
ms.assetid: cee5be2d-7c20-4cec-a352-1ab8b7d32601
ms.openlocfilehash: d890eb6a1b7c93f9ae5b87018c3bf1d6eeae8abb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607015"
---
# <a name="iserrorcodeenum-class"></a>is_error_code_enum — Klasa

Reprezentuje typu predykatu, który sprawdza, czy [error_code](../standard-library/error-code-class.md) wyliczenia.

## <a name="syntax"></a>Składnia

```cpp
template <_Enum>
class is_error_code_enum;
```

## <a name="remarks"></a>Uwagi

Wystąpienie tego elementu [predykatu typów](../standard-library/type-traits.md) ma wartość true, jeśli typ `_Enum` jest wartością wyliczenia odpowiedniego do przechowywania w obiekcie typu `error_code`.

Jest dozwolone, aby dodać specjalizacje tego typu dla typów zdefiniowanych przez użytkownika.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<system_error >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[<system_error>](../standard-library/system-error.md)<br/>
