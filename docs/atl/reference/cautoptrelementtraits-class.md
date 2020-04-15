---
title: Klasa CAutoPtrElementTraits
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CAutoPtrElementTraits class
ms.assetid: 777c1b14-6ab7-491f-b9a5-be149e71d4a2
ms.openlocfilehash: ac29116dc9beedf587c42cc0e52f8c9dbaf3d782
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318875"
---
# <a name="cautoptrelementtraits-class"></a>Klasa CAutoPtrElementTraits

Ta klasa zawiera metody, funkcje statyczne i typedefs przydatne podczas tworzenia kolekcji inteligentnych wskaźników.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template<typename T>
class CAutoPtrElementTraits
    : public CDefaultElementTraits<ATL::CAutoPtr<T>>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ wskaźnika.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|[CAutoPtrElementTraits::INARGTYPE](#inargtype)|Typ danych do dodania elementów do obiektu klasy kolekcji.|
|[CAutoPtrElementTraits::OUTARGTYPE](#outargtype)|Typ danych do użycia do pobierania elementów z obiektu klasy kolekcji.|

## <a name="remarks"></a>Uwagi

Ta klasa zawiera metody, funkcje statyczne i typedefs do wspomagania tworzenia obiektów klasy kolekcji zawierających inteligentne wskaźniki. Klasy [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) i [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) `CAutoPtrElementTraits`pochodzą od . Jeśli tworzenie kolekcji inteligentnych wskaźników, które wymaga operatorów wektora new i delete, należy użyć [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) zamiast.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits (Niem.](../../atl/reference/cdefaulthashtraits-class.md)

[Baza CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits (3.](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoPtrElementTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="cautoptrelementtraitsinargtype"></a><a name="inargtype"></a>CAutoPtrElementTraits::INARGTYPE

Typ danych do dodania elementów do obiektu klasy kolekcji.

```
typedef CAutoPtr<T>& INARGTYPE;
```

## <a name="cautoptrelementtraitsoutargtype"></a><a name="outargtype"></a>CAutoPtrElementTraits::OUTARGTYPE

Typ danych do użycia do pobierania elementów z obiektu klasy kolekcji.

```
typedef T *& OUTARGTYPE;
```

## <a name="see-also"></a>Zobacz też

[Klasa CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
