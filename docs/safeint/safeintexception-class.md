---
title: SafeIntException — Klasa
ms.date: 10/22/2018
ms.topic: reference
f1_keywords:
- SafeIntException Class
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
helpviewer_keywords:
- SafeIntException class
- SafeIntException, constructor
ms.assetid: 88bef958-1f48-4d55-ad4f-d1f9581a293a
ms.openlocfilehash: 2998bbb83fd568d7ff627d6598c32fb5b17c1e40
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787507"
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

[Safeint — klasa](../safeint/safeint-class.md) jest to jedyna klasa, która używa `SafeIntException` klasy.

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