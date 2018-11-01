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
ms.openlocfilehash: ca664d78f80a0c335a8669454b1345955aaefcb2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644668"
---
# <a name="cancellationtokenregistration-class"></a>cancellation_token_registration — Klasa

`cancellation_token_registration` Klasa reprezentuje powiadomienie o wywołaniu zwrotnym od `cancellation_token`. Gdy `register` metody `cancellation_token` umożliwia otrzymywanie powiadomień o czasie wystąpienia anulowania `cancellation_token_registration` obiekt jest zwracany jako uchwyt do funkcji zwrotnej tak, aby obiekt wywołujący może żądać konkretne wywołanie zwrotne nie jest już dokonywane przy użyciu `deregister` metody.

## <a name="syntax"></a>Składnia

```
class cancellation_token_registration;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[cancellation_token_registration](#ctor)||
|[~cancellation_token_registration Destructor](#dtor)||

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator!=](#operator_neq)||
|[operator=](#operator_eq)||
|[operator==](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`cancellation_token_registration`

## <a name="requirements"></a>Wymagania

**Nagłówek:** pplcancellation_token.h

**Namespace:** współbieżności

##  <a name="dtor"></a> ~cancellation_token_registration

```
~cancellation_token_registration();
```

##  <a name="ctor"></a> cancellation_token_registration —

```
cancellation_token_registration();

cancellation_token_registration(const cancellation_token_registration& _Src);

cancellation_token_registration(cancellation_token_registration&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
`cancellation_token_registration` Aby skopiować lub przenieść.

##  <a name="operator_neq"></a> operator! =

```
bool operator!= (const cancellation_token_registration& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
`cancellation_token_registration` Do porównania.

### <a name="return-value"></a>Wartość zwracana

##  <a name="operator_eq"></a> operator =

```
cancellation_token_registration& operator= (const cancellation_token_registration& _Src);

cancellation_token_registration& operator= (cancellation_token_registration&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
`cancellation_token_registration` Do przypisania.

### <a name="return-value"></a>Wartość zwracana

##  <a name="operator_eq_eq"></a> operator ==

```
bool operator== (const cancellation_token_registration& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
`cancellation_token_registration` Do porównania.

### <a name="return-value"></a>Wartość zwracana

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
