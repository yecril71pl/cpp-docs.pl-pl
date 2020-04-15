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
ms.openlocfilehash: e118d7e3cce47ebb93cef16319a8fc45aab1118b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349950"
---
# <a name="safeintexception-class"></a>SafeIntException — Klasa

Klasa `SafeInt` używa `SafeIntException` do określenia, dlaczego nie można ukończyć operacji matematycznej.

> [!NOTE]
> Najnowsza wersja tej biblioteki [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt)znajduje się pod adresem .

## <a name="syntax"></a>Składnia

```cpp
class SafeIntException;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                    | Opis
------------------------------------------------------- | ------------------------------------
[SafeIntException::SafeIntException](#safeintexception) | Tworzy obiekt `SafeIntException`.

## <a name="remarks"></a>Uwagi

[SafeInt Klasa](../safeint/safeint-class.md) jest jedyną klasą, `SafeIntException` która używa klasy.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SafeIntException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** safeint.h

**Obszar nazw:** msl::utilities

## <a name="safeintexceptionsafeintexception"></a><a name="safeintexception"></a>SafeIntException::SafeIntException

Tworzy obiekt `SafeIntException`.

```cpp
SafeIntException();

SafeIntException(
   SafeIntError code
);
```

### <a name="parameters"></a>Parametry

*Kod*<br/>
[w] Wyliczona wartość danych opisująca błąd, który wystąpił.

### <a name="remarks"></a>Uwagi

Możliwe wartości *kodu* są zdefiniowane w pliku Safeint.h. Dla wygody, możliwe wartości są również wymienione tutaj.

- `SafeIntNoError`
- `SafeIntArithmeticOverflow`
- `SafeIntDivideByZero`
