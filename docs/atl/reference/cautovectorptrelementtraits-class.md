---
title: CAutoVectorPtrElementTraits Klasa
ms.date: 11/04/2016
f1_keywords:
- CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CAutoVectorPtrElementTraits class
ms.assetid: 16b81a56-55fb-46ca-b376-66a1884231a6
ms.openlocfilehash: 956fe39c4d3ba89bb9def2f996dca59905753edb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318754"
---
# <a name="cautovectorptrelementtraits-class"></a>CAutoVectorPtrElementTraits Klasa

Ta klasa zawiera metody, funkcje statyczne i typedefs przydatne podczas tworzenia kolekcji inteligentnych wskaźników przy użyciu operatorów wektorowych i delete.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <typename T>
class CAutoVectorPtrElementTraits :
   public CDefaultElementTraits<ATL::CAutoVectorPtr<T>>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ wskaźnika.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|[CAutoVectorPtrElementTraits::INARGTYPE](#inargtype)|Typ danych do dodania elementów do obiektu klasy kolekcji.|
|[CAutoVectorPtrElementTraits::OUTARGTYPE](#outargtype)|Typ danych do użycia do pobierania elementów z obiektu klasy kolekcji.|

## <a name="remarks"></a>Uwagi

Ta klasa zawiera metody, funkcje statyczne i typedefs do wspomagania tworzenia obiektów klasy kolekcji zawierających inteligentne wskaźniki. W przeciwieństwie do [CAutoPtrElementTraits,](../../atl/reference/cautoptrelementtraits-class.md)ta klasa używa operatorów wektorowych i delete.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits (Niem.](../../atl/reference/cdefaulthashtraits-class.md)

[Baza CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits (3.](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoVectorPtrElementTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="cautovectorptrelementtraitsinargtype"></a><a name="inargtype"></a>CAutoVectorPtrElementTraits::INARGTYPE

Typ danych do dodania elementów do obiektu klasy kolekcji.

```
typedef CAutoVectorPtr<T>& INARGTYPE;
```

## <a name="cautovectorptrelementtraitsoutargtype"></a><a name="outargtype"></a>CAutoVectorPtrElementTraits::OUTARGTYPE

Typ danych do użycia do pobierania elementów z obiektu klasy kolekcji.

```
typedef T*& OUTARGTYPE;
```

## <a name="see-also"></a>Zobacz też

[Klasa CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Klasa CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
