---
title: Operatory ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b651d73db043388e1dc7bf33c085f07d3aabed33
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767946"
---
# <a name="atl-operators"></a>Operatory ATL

Ta sekcja zawiera tematy referencyjne dla operatorów globalnych ATL.

|Operator|Opis|
|--------------|-----------------|
|[operator ==](#operator_eq_eq)|Porównuje dwa `CSid` obiektów lub `SID` struktury pod kątem równości.|
|[operator! =](#operator_neq)|Porównuje dwa `CSid` obiektów lub `SID` struktury pod kątem nierówności.|
|[Operator <](#operator_lt)|Sprawdza, czy `CSid` obiektu lub `SID` struktura po lewej stronie operatora jest mniejszy od `CSid` obiektu lub `SID` struktury z prawej strony (w przypadku zgodności standardowa biblioteka C++).|
|[operator >](#operator_gt)|Sprawdza, czy `CSid` obiektu lub `SID` struktury po lewej stronie operatora jest większy niż `CSid` obiektu lub `SID` struktury z prawej strony (w przypadku zgodności standardowa biblioteka C++).|
|[Operator < =](#operator_lt__eq)|Sprawdza, czy `CSid` obiektu lub `SID` struktury po lewej stronie operatora jest mniejszy niż lub równe `CSid` obiektu lub `SID` struktury z prawej strony (w przypadku zgodności standardowa biblioteka C++).|
|[operator > =](#operator_gt__eq)|Sprawdza, czy `CSid` obiektu lub `SID` struktury po lewej stronie operatora jest większy niż lub równa `CSid` obiektu lub `SID` struktury z prawej strony (w przypadku zgodności standardowa biblioteka C++).|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h.

##  <a name="operator_eq_eq"></a>  operator ==

Porównuje `CSid` obiektów lub `SID` struktur (identyfikator zabezpieczeń) pod kątem równości.

```   
bool operator==(const CSid& lhs, const CSid& rhs) throw(); 
```

### <a name="parameters"></a>Parametry

`lhs`  
Pierwszy `CSid` obiektu lub `SID` struktury do porównania.

`rhs`  
Drugi `CSid` obiektu lub `SID` struktury do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli obiekty są równe, wartość FALSE, jeśli nie są takie same.

##  <a name="operator_neq"></a>  operator! =

Porównuje `CSid` obiektów lub `SID` struktur (identyfikator zabezpieczeń) pod kątem nierówności.

```   
bool operator==(const CSid& lhs, const CSid& rhs) throw(); 
```

### <a name="parameters"></a>Parametry

*Lewa strona reguły przepisywania*  
Pierwszy `CSid` obiektu lub `SID` struktury do porównania.

*RHS*  
Drugi `CSid` obiektu lub `SID` struktury do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli obiekty nie są równe, wartość FALSE, jeśli są równe.

##  <a name="operator_lt"></a>  Operator <

Sprawdza, czy `CSid` obiektu lub `SID` struktura po lewej stronie operatora jest mniejszy od `CSid` obiektu lub `SID` struktury z prawej strony (w przypadku zgodności standardowa biblioteka C++).

```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```

### <a name="parameters"></a>Parametry

*Lewa strona reguły przepisywania*  
Pierwszy `CSid` obiektu lub `SID` struktury do porównania.

*RHS*  
Drugi `CSid` obiektu lub `SID` struktury do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli adres *lhs* obiekt jest mniejszy niż adres *rhs* obiekt, wartość FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Ten operator działa na adres `CSid` obiektu lub `SID` struktury i jest implementowane w celu zapewnienia zgodności z klas kolekcji standardowej biblioteki języka C++.

##  <a name="operator_gt"></a>  operator >

Sprawdza, czy `CSid` obiektu lub `SID` struktury po lewej stronie operatora jest większy niż `CSid` obiektu lub `SID` struktury z prawej strony (w przypadku zgodności standardowa biblioteka C++).

```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```

### <a name="parameters"></a>Parametry

*Lewa strona reguły przepisywania*  
Pierwszy `CSid` obiektu lub `SID` struktury do porównania.

*RHS*  
Drugi `CSid` obiektu lub `SID` struktury do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli adres *lhs* jest większy niż adres *rhs*, wartość FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Ten operator działa na adres `CSid` obiektu lub `SID` struktury i jest implementowane w celu zapewnienia zgodności z klas kolekcji standardowej biblioteki języka C++.

##  <a name="operator_lt__eq"></a>  Operator < =

Sprawdza, czy `CSid` obiektu lub `SID` struktury po lewej stronie operatora jest mniejszy niż lub równe `CSid` obiektu lub `SID` struktury z prawej strony (w przypadku zgodności standardowa biblioteka C++).

```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```

### <a name="parameters"></a>Parametry

*Lewa strona reguły przepisywania*  
Pierwszy `CSid` obiektu lub `SID` struktury do porównania.

*RHS*  
Drugi `CSid` obiektu lub `SID` struktury do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli adres *lhs* jest mniejszy niż adres *rhs*, wartość FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Ten operator działa na adres `CSid` obiektu lub `SID` struktury i jest implementowane w celu zapewnienia zgodności z klas kolekcji standardowej biblioteki języka C++.

##  <a name="operator_gt__eq"></a>  operator > =

Sprawdza, czy `CSid` obiektu lub `SID` struktury po lewej stronie operatora jest większy niż lub równa `CSid` obiektu lub `SID` struktury z prawej strony (w przypadku zgodności standardowa biblioteka C++).

```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```

### <a name="parameters"></a>Parametry

*Lewa strona reguły przepisywania*  
Pierwszy `CSid` obiektu lub `SID` struktury do porównania.

*RHS*  
Drugi `CSid` obiektu lub `SID` struktury do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli adres *lhs* jest większy lub równy adresowi *rhs*, wartość FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Ten operator działa na adres `CSid` obiektu lub `SID` struktury i jest implementowane w celu zapewnienia zgodności z klas kolekcji standardowej biblioteki języka C++.

