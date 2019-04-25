---
title: CSimpleMapEqualHelper Class
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
ms.openlocfilehash: c614cbb11376c5ae338762c0feaa54c8f1bb3e27
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62277934"
---
# <a name="csimplemapequalhelper-class"></a>CSimpleMapEqualHelper Class

Ta klasa jest pomocnika dla [CSimpleMap](../../atl/reference/csimplemap-class.md) klasy.

## <a name="syntax"></a>Składnia

```
template <class TKey, class TVal>
class CSimpleMapEqualHelper
```

#### <a name="parameters"></a>Parametry

*TKey*<br/>
Kluczowym elementem.

*TVal*<br/>
Element wartości.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleMapEqualHelper::IsEqualKey](#isequalkey)|(Statyczny) Testuje dwa klucze pod kątem równości.|
|[CSimpleMapEqualHelper::IsEqualValue](#isequalvalue)|(Statyczny) Sprawdza dwie wartości dla równości.|

## <a name="remarks"></a>Uwagi

Ta klasa cech jest uzupełnieniem `CSimpleMap` klasy. Zapewnia metody do porównywania dwóch `CSimpleMap` obiektu elementów (w szczególności składniki klucza i wartości) pod kątem równości. Domyślnie klucze i wartości są porównywane za pomocą **operator==()**, ale jeśli mapa zawiera złożone typy danych, które nie mają własne operator równości, ta klasa może zostać zastąpiona w celu zapewnienia dodatkowych wymaganych funkcji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpcoll.h

##  <a name="isequalkey"></a>  CSimpleMapEqualHelper::IsEqualKey

Testuje dwa klucze pod kątem równości.

```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```

### <a name="parameters"></a>Parametry

*k1*<br/>
Pierwszy klucz.

*k2*<br/>
Drugi klucz.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli klucze są takie same, wartość false w przeciwnym razie.

##  <a name="isequalvalue"></a>  CSimpleMapEqualHelper::IsEqualValue

Sprawdza dwie wartości dla równości.

```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```

### <a name="parameters"></a>Parametry

*v1*<br/>
Pierwsza wartość.

*v2*<br/>
Druga wartość.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli wartości są równe, wartość false w przeciwnym razie.

## <a name="see-also"></a>Zobacz także

[Klasa CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
