---
title: Safeintexception — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeIntException Class
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
dev_langs:
- C++
helpviewer_keywords:
- SafeIntException class
- SafeIntException, constructor
ms.assetid: 88bef958-1f48-4d55-ad4f-d1f9581a293a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2a1890bc20c0737007075656dcbefa20ad81a9bf
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50068063"
---
# <a name="safeintexception-class"></a>SafeIntException — Klasa

`SafeInt` Klasy używa `SafeIntException` celu ustaleniu, dlaczego nie można ukończyć operacji matematycznych.

> [!NOTE]
> Najnowszą wersję tej biblioteki znajduje się w [ https://github.com/dcleblanc/SafeInt ](https://github.com/dcleblanc/SafeInt).

## <a name="syntax"></a>Składnia

```cpp
class SafeIntException;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                    | Opis
------------------------------------------------------- | ------------------------------------
[SafeIntException::SafeIntException](#safeintexception) | Tworzy `SafeIntException` obiektu.

## <a name="remarks"></a>Uwagi

[Safeint — klasa](../windows/safeint-class.md) jest to jedyna klasa, która używa `SafeIntException` klasy.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SafeIntException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** safeint.h

**Namespace:** msl::utilities

## <a name="safeintexception"></a>SafeIntException::SafeIntException

Tworzy `SafeIntException` obiektu.

```cpp
SafeIntException();

SafeIntException(
   SafeIntError code
);
```

### <a name="parameters"></a>Parametry

*Kod*<br/>
[in] Wartość danych wyliczany, który opisuje błąd, który wystąpił.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *kodu* są zdefiniowane w pliku Safeint.h. Dla wygody możliwe wartości są również wymienione tutaj.

- `SafeIntNoError`
- `SafeIntArithmeticOverflow`
- `SafeIntDivideByZero`
