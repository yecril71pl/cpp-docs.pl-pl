---
title: Klasa CSimpleMapEqualHelper | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualValue
dev_langs:
- C++
helpviewer_keywords:
- CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1670ff7ed53d05b1dfc09e6953650892b0335f61
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761472"
---
# <a name="csimplemapequalhelper-class"></a>Klasa CSimpleMapEqualHelper

Ta klasa jest pomocnika dla [CSimpleMap](../../atl/reference/csimplemap-class.md) klasy.

## <a name="syntax"></a>Składnia

```
template <class TKey, class TVal>  
class CSimpleMapEqualHelper
```

#### <a name="parameters"></a>Parametry

*TKey*  
Kluczowym elementem.

*TVal*  
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

*K1*  
Pierwszy klucz.

*K2*  
Drugi klucz.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli klucze są takie same, wartość false w przeciwnym razie.

##  <a name="isequalvalue"></a>  CSimpleMapEqualHelper::IsEqualValue

Sprawdza dwie wartości dla równości.

```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```

### <a name="parameters"></a>Parametry

*w wersji 1*  
Pierwsza wartość.

*w wersji 2*  
Druga wartość.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli wartości są równe, wartość false w przeciwnym razie.

## <a name="see-also"></a>Zobacz też

[Klasa CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)   
[Klasa — Przegląd](../../atl/atl-class-overview.md)
