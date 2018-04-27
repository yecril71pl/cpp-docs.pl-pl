---
title: is_error_code_enum — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- system_error/std::is_error_code_enum
dev_langs:
- C++
helpviewer_keywords:
- is_error_code_enum class
ms.assetid: cee5be2d-7c20-4cec-a352-1ab8b7d32601
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c0d0eae64b7474ab9539cc7d4494483322f75ceb
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="iserrorcodeenum-class"></a>is_error_code_enum — Klasa

Reprezentuje predykat typów, które sprawdza, czy [error_code —](../standard-library/error-code-class.md) wyliczenia.

## <a name="syntax"></a>Składnia

```cpp
template <_Enum>
class is_error_code_enum;
```

## <a name="remarks"></a>Uwagi

Wystąpienie tego elementu [predykatu typów](../standard-library/type-traits.md) blokad wartość true, jeśli typ `_Enum` jest wartością wyliczenia odpowiedniego do przechowywania w obiekcie typu `error_code`.

Jest dozwolone, aby dodać specjalizacje do tego typu dla typów zdefiniowanych przez użytkownika.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<system_error — >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[<system_error>](../standard-library/system-error.md)<br/>
