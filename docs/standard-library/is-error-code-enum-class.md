---
title: is_error_code_enum — Klasa
ms.date: 11/04/2016
f1_keywords:
- system_error/std::is_error_code_enum
helpviewer_keywords:
- is_error_code_enum class
ms.assetid: cee5be2d-7c20-4cec-a352-1ab8b7d32601
ms.openlocfilehash: bc4ed7cd2e058414448c9366011b9efab97ee3d5
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245189"
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

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
