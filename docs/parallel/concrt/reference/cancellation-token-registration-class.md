---
title: cancellation_token_registration — Klasa
ms.date: 11/04/2016
f1_keywords:
- cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration::cancellation_token_registration
helpviewer_keywords:
- cancellation_token_registration class
ms.assetid: 823d63f4-7233-4d65-8976-6152ccf12d0e
ms.openlocfilehash: 9342841e207c93b66521c2fc742c1b1114682f78
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142235"
---
# <a name="cancellation_token_registration-class"></a>cancellation_token_registration — Klasa

Klasa `cancellation_token_registration` reprezentuje powiadomienie wywołania zwrotnego z `cancellation_token`. Gdy metoda `register` na `cancellation_token` jest używana do otrzymywania powiadomień o wystąpieniu anulowania, obiekt `cancellation_token_registration` jest zwracany jako dojście do wywołania zwrotnego, dzięki czemu obiekt wywołujący może zażądać określonego wywołania zwrotnego za pomocą metody `deregister`.

## <a name="syntax"></a>Składnia

```cpp
class cancellation_token_registration;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[cancellation_token_registration](#ctor)||
|[~ cancellation_token_registration destruktor](#dtor)||

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[operator!=](#operator_neq)||
|[operator =](#operator_eq)||
|[operator = =](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`cancellation_token_registration`

## <a name="requirements"></a>Wymagania

**Nagłówek:** pplcancellation_token. h

**Przestrzeń nazw:** współbieżność

## <a name="dtor"></a>~ cancellation_token_registration

```cpp
~cancellation_token_registration();
```

## <a name="ctor"></a>cancellation_token_registration

```cpp
cancellation_token_registration();

cancellation_token_registration(const cancellation_token_registration& _Src);

cancellation_token_registration(cancellation_token_registration&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
`cancellation_token_registration` do kopiowania lub przenoszenia.

## <a name="operator_neq"></a>operator! =

```cpp
bool operator!= (const cancellation_token_registration& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
`cancellation_token_registration` do porównania.

### <a name="return-value"></a>Wartość zwrócona

## <a name="operator_eq"></a>operator =

```cpp
cancellation_token_registration& operator= (const cancellation_token_registration& _Src);

cancellation_token_registration& operator= (cancellation_token_registration&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
`cancellation_token_registration` do przypisania.

### <a name="return-value"></a>Wartość zwrócona

## <a name="operator_eq_eq"></a>operator = =

```cpp
bool operator== (const cancellation_token_registration& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
`cancellation_token_registration` do porównania.

### <a name="return-value"></a>Wartość zwrócona

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
