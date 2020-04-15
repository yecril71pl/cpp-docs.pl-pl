---
title: Klasa CSimpleMapEqualHelperFalse
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelperFalse class
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
ms.openlocfilehash: b6bf1d4e3be849004e13e593fb5f4b5cb87f8123
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330739"
---
# <a name="csimplemapequalhelperfalse-class"></a>Klasa CSimpleMapEqualHelperFalse

Ta klasa jest pomocnikiem dla [CSimpleMap](../../atl/reference/csimplemap-class.md) klasy.

## <a name="syntax"></a>Składnia

```
template <class TKey, class TVal>
class CSimpleMapEqualHelperFalse
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleMapEqualHelperFalse::IsEqualKey](#isequalkey)|(Statyczne) Testy dwa klucze równości.|
|[CSimpleMapEqualHelperFalse::IsEqualValue](#isequalvalue)|(Statyczne) Zwraca wartość false.|

## <a name="remarks"></a>Uwagi

Ta klasa cech jest uzupełnieniem `CSimpleMap` klasy. Zapewnia metodę porównywania dwóch elementów zawartych w `CSimpleMap` obiekcie, w szczególności dwa elementy wartości lub dwa kluczowe elementy.

Porównanie wartości zawsze zwróci false, a ponadto `ATLASSERT` wywoła argument false, jeśli kiedykolwiek odwołuje się. W sytuacjach, gdy test równości nie jest wystarczająco zdefiniowany, ta klasa umożliwia poprawne działanie mapy zawierającej pary klucz/wartość dla większości metod, ale nie działa w sposób dobrze zdefiniowany dla metod, które zależą od porównań, takich jak [CSimpleMap::FindVal](../../atl/reference/csimplemap-class.md#findval).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpcoll.h

## <a name="csimplemapequalhelperfalseisequalkey"></a><a name="isequalkey"></a>CSimpleMapEqualHelperFalse::IsEqualKey

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

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md).

## <a name="csimplemapequalhelperfalseisequalvalue"></a><a name="isequalvalue"></a>CSimpleMapEqualHelperFalse::IsEqualValue

Zwraca wartość false.

```
static bool IsEqualValue(const TVal&, const TVal&);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość false.

### <a name="remarks"></a>Uwagi

Ta metoda zawsze zwraca false `ATLASSERT` i wywoła argument false, jeśli kiedykolwiek odwołuje się. Celem jest `CSimpleMapEqualHelperFalse::IsEqualValue` wymuszenie użycia porównań w sposób dobrze zdefiniowany, gdy testy równości nie zostały odpowiednio zdefiniowane.

## <a name="see-also"></a>Zobacz też

[Klasa CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
