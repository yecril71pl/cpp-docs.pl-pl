---
title: Klasa CPrimitiveElementTraits
ms.date: 11/04/2016
f1_keywords:
- CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits::INARGTYPE
- ATLCOLL/ATL::CPrimitiveElementTraits::OUTARGTYPE
helpviewer_keywords:
- CPrimitiveElementTraits class
ms.assetid: 21c1cea8-2c5a-486c-b65c-85490f3ed4e6
ms.openlocfilehash: 6b45d93420d1832091cc451a3e6eb309f61d07a3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331438"
---
# <a name="cprimitiveelementtraits-class"></a>Klasa CPrimitiveElementTraits

Ta klasa zawiera domyślne metody i funkcje dla klasy kolekcji składającej się z typów danych pierwotnych.

## <a name="syntax"></a>Składnia

```
template <typename T>
class CPrimitiveElementTraits : public CDefaultElementTraits<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych, które mają być przechowywane w obiekcie klasy kolekcji.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|[CPrimitiveElementTraits::INARGTYPE](#inargtype)|Typ danych do dodania elementów do obiektu klasy kolekcji.|
|[CPrimitiveElementTraits::OUTARGTYPE](#outargtype)|Typ danych do użycia do pobierania elementów z obiektu klasy kolekcji.|

## <a name="remarks"></a>Uwagi

Ta klasa zawiera domyślne funkcje statyczne i metody przenoszenia, kopiowania, porównywania i mieszania podstawowych elementów typu danych przechowywanych w obiekcie klasy kolekcji.

Aby uzyskać więcej informacji, zobacz [ATL Collection Classes](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits (Niem.](../../atl/reference/cdefaulthashtraits-class.md)

[Baza CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits (3.](../../atl/reference/cdefaultelementtraits-class.md)

`CPrimitiveElementTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="cprimitiveelementtraitsinargtype"></a><a name="inargtype"></a>CPrimitiveElementTraits::INARGTYPE

Typ danych do dodania elementów do obiektu klasy kolekcji.

```
typedef T INARGTYPE;
```

## <a name="cprimitiveelementtraitsoutargtype"></a><a name="outargtype"></a>CPrimitiveElementTraits::OUTARGTYPE

Typ danych do użycia do pobierania elementów z obiektu klasy kolekcji.

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>Zobacz też

[Klasa CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
