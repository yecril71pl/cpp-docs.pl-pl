---
title: SafeIntException::SafeIntException | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
dev_langs:
- C++
helpviewer_keywords:
- SafeIntException, constructor
ms.assetid: 8e5a0c24-a56b-4c80-9ee8-876604b1e7dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 24138db5ab772990f050fc8fcb6e5dad640a662d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396782"
---
# <a name="safeintexceptionsafeintexception"></a>SafeIntException::SafeIntException

Tworzy **safeintexception —** obiektu.

## <a name="syntax"></a>Składnia

```cpp
SafeIntException();

SafeIntException(
   SafeIntError code
);
```

### <a name="parameters"></a>Parametry

*Kod*<br/>
[in] Wartość danych wyliczany, który opisuje błąd, który wystąpił.

## <a name="remarks"></a>Uwagi

Możliwe wartości parametru *kodu* są zdefiniowane w pliku Safeint.h. Dla wygody możliwe wartości są również wymienione tutaj.

- `SafeIntNoError`

- `SafeIntArithmeticOverflow`

- `SafeIntDivideByZero`

## <a name="requirements"></a>Wymagania

**Nagłówek:** safeint.h

**Namespace:** msl::utilities

## <a name="see-also"></a>Zobacz też

[Biblioteka SafeInt](../windows/safeint-library.md)<br/>
[SafeIntException, klasa](../windows/safeintexception-class.md)<br/>
[SafeInt, klasa](../windows/safeint-class.md)