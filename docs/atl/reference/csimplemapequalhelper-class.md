---
title: Klasa CSimpleMapEqualHelper
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
ms.openlocfilehash: d137a35a517ea93139f036f6e9a7a8de06d518a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330752"
---
# <a name="csimplemapequalhelper-class"></a>Klasa CSimpleMapEqualHelper

Ta klasa jest pomocnikiem dla [CSimpleMap](../../atl/reference/csimplemap-class.md) klasy.

## <a name="syntax"></a>Składnia

```
template <class TKey, class TVal>
class CSimpleMapEqualHelper
```

#### <a name="parameters"></a>Parametry

*Tkey*<br/>
Kluczowym elementem.

*TVal (własn.*<br/>
Element wartości.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleMapEqualHelper::IsEqualKey](#isequalkey)|(Statyczne) Testy dwa klucze równości.|
|[CSimpleMapEqualHelper::IsEqualValue](#isequalvalue)|(Statyczne) Testy dwie wartości równości.|

## <a name="remarks"></a>Uwagi

Ta klasa cech jest uzupełnieniem `CSimpleMap` klasy. Zapewnia metody porównywania `CSimpleMap` dwóch elementów obiektu (w szczególności składników klucza i wartości) dla równości. Domyślnie klucze i wartości są porównywane przy użyciu **operator==(),** ale jeśli mapa zawiera złożone typy danych, które nie mają własnego operatora równości, ta klasa może zostać zastąpiona w celu zapewnienia dodatkowych wymaganych funkcji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpcoll.h

## <a name="csimplemapequalhelperisequalkey"></a><a name="isequalkey"></a>CSimpleMapEqualHelper::IsEqualKey

Testy dwa klucze równości.

```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```

### <a name="parameters"></a>Parametry

*k1*<br/>
Pierwszy klucz.

*k2*<br/>
Drugi klawisz.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli klucze są równe, false w przeciwnym razie.

## <a name="csimplemapequalhelperisequalvalue"></a><a name="isequalvalue"></a>CSimpleMapEqualHelper::IsEqualValue

Testy dwie wartości równości.

```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```

### <a name="parameters"></a>Parametry

*w wersji 1*<br/>
Pierwsza wartość.

*v2*<br/>
Druga wartość.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli wartości są równe, false w przeciwnym razie.

## <a name="see-also"></a>Zobacz też

[Klasa CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
