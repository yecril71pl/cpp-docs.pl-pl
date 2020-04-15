---
title: Operatory ATL
ms.date: 11/04/2016
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
ms.openlocfilehash: 8c15daa1d2b12c58323ef5ef75559a2ab911ad93
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319233"
---
# <a name="atl-operators"></a>Operatory ATL

Ta sekcja zawiera tematy referencyjne dla globalnych operatorów ATL.

|Operator|Opis|
|--------------|-----------------|
|[operator ==](#operator_eq_eq)|Porównuje dwa `CSid` obiekty `SID` lub struktury dla równości.|
|[operator !=](#operator_neq)|Porównuje dwa `CSid` obiekty `SID` lub struktury dla nierówności.|
|[<operatora](#operator_lt)|Sprawdza, `CSid` czy `SID` obiekt lub struktura po lewej stronie `CSid` operatora `SID` jest mniejsza niż obiekt lub struktura po prawej stronie (dla zgodności z biblioteką standardową języka C++).|
|[>operatora](#operator_gt)|Sprawdza, `CSid` czy `SID` obiekt lub struktura po lewej stronie `CSid` operatora `SID` jest większa niż obiekt lub struktura po prawej stronie (dla zgodności z biblioteką standardową języka C++).|
|[<operatora =](#operator_lt__eq)|Sprawdza, `CSid` czy `SID` obiekt lub struktura po lewej stronie operatora jest `CSid` mniejsza `SID` lub równa obiektowi lub strukturze po prawej stronie (dla zgodności biblioteki standardowej języka C++).|
|[>operatora =](#operator_gt__eq)|Sprawdza, `CSid` czy `SID` obiekt lub struktura po lewej stronie operatora jest `CSid` większa `SID` lub równa obiektowi lub strukturze po prawej stronie (dla zgodności biblioteki standardowej języka C++).|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h.

## <a name="operator-"></a><a name="operator_eq_eq"></a>operator ==

Porównuje `CSid` obiekty `SID` lub (identyfikator zabezpieczeń) struktury równości.

```
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
Pierwszy `CSid` obiekt `SID` lub struktura do porównania.

*Rhs*<br/>
Drugi `CSid` obiekt `SID` lub struktura do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli obiekty są równe, WARTOŚĆ FAŁSZ, jeśli nie są równe.

## <a name="operator-"></a><a name="operator_neq"></a>operator !=

Porównuje `CSid` obiekty `SID` lub struktury (identyfikator zabezpieczeń) dla nierówności.

```
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
Pierwszy `CSid` obiekt `SID` lub struktura do porównania.

*Rhs*<br/>
Drugi `CSid` obiekt `SID` lub struktura do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli obiekty nie są równe, wartość FAŁsz, jeśli są równe.

## <a name="operator-"></a><a name="operator_lt"></a>< operatora

Sprawdza, `CSid` czy `SID` obiekt lub struktura po lewej stronie `CSid` operatora `SID` jest mniejsza niż obiekt lub struktura po prawej stronie (dla zgodności z biblioteką standardową języka C++).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
Pierwszy `CSid` obiekt `SID` lub struktura do porównania.

*Rhs*<br/>
Drugi `CSid` obiekt `SID` lub struktura do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli adres obiektu *lhs* jest mniejszy niż adres obiektu *rhs,* w przeciwnym razie wartość FAŁSZ.

### <a name="remarks"></a>Uwagi

Ten operator działa na `CSid` adres `SID` obiektu lub struktury i jest implementowany w celu zapewnienia zgodności z klasami kolekcji biblioteki standardowej języka C++.

## <a name="operator-"></a><a name="operator_gt"></a>> operatora

Sprawdza, `CSid` czy `SID` obiekt lub struktura po lewej stronie `CSid` operatora `SID` jest większa niż obiekt lub struktura po prawej stronie (dla zgodności z biblioteką standardową języka C++).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
Pierwszy `CSid` obiekt `SID` lub struktura do porównania.

*Rhs*<br/>
Drugi `CSid` obiekt `SID` lub struktura do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli adres *lhs* jest większy niż adres *rhs*, FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Ten operator działa na `CSid` adres `SID` obiektu lub struktury i jest implementowany w celu zapewnienia zgodności z klasami kolekcji biblioteki standardowej języka C++.

## <a name="operator-"></a><a name="operator_lt__eq"></a><operatora =

Sprawdza, `CSid` czy `SID` obiekt lub struktura po lewej stronie operatora jest `CSid` mniejsza `SID` lub równa obiektowi lub strukturze po prawej stronie (dla zgodności biblioteki standardowej języka C++).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
Pierwszy `CSid` obiekt `SID` lub struktura do porównania.

*Rhs*<br/>
Drugi `CSid` obiekt `SID` lub struktura do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli adres *lhs* jest mniejszy lub równy adresowi *rhs*, FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Ten operator działa na `CSid` adres `SID` obiektu lub struktury i jest implementowany w celu zapewnienia zgodności z klasami kolekcji biblioteki standardowej języka C++.

## <a name="operator-"></a><a name="operator_gt__eq"></a>>operatora =

Sprawdza, `CSid` czy `SID` obiekt lub struktura po lewej stronie operatora jest `CSid` większa `SID` lub równa obiektowi lub strukturze po prawej stronie (dla zgodności biblioteki standardowej języka C++).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
Pierwszy `CSid` obiekt `SID` lub struktura do porównania.

*Rhs*<br/>
Drugi `CSid` obiekt `SID` lub struktura do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli adres *lhs* jest większy lub równy adresowi *rhs*, FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Ten operator działa na `CSid` adres `SID` obiektu lub struktury i jest implementowany w celu zapewnienia zgodności z klasami kolekcji biblioteki standardowej języka C++.
