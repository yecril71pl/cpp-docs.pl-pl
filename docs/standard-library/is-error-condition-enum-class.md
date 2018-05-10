---
title: is_error_condition_enum — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- system_error/std::is_error_condition_enum
dev_langs:
- C++
helpviewer_keywords:
- is_error_condition_enum class
ms.assetid: 752bb87a-c61c-4304-9254-5aaf228b59c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01650db9c1aec141852f66a2f4e2f09f5d5e78ac
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="iserrorconditionenum-class"></a>is_error_condition_enum — Klasa

Reprezentuje predykat typów, które sprawdza, czy [error_condition —](../standard-library/error-condition-class.md) wyliczenia.

## <a name="syntax"></a>Składnia

```cpp
template <_Enum>
class is_error_condition_enum;
```

## <a name="remarks"></a>Uwagi

Wystąpienie tego elementu [predykatu typów](../standard-library/type-traits.md) blokad wartość true, jeśli typ `_Enum` jest wartością wyliczenia odpowiedniego do przechowywania w obiekcie typu `error_condition`.

Jest dozwolone, aby dodać specjalizacje do tego typu dla typów zdefiniowanych przez użytkownika.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<system_error — >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[<system_error>](../standard-library/system-error.md)<br/>
