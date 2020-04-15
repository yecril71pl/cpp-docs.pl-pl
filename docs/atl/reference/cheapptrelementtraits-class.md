---
title: Klasa CHeapPtrElementTraits
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CHeapPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CHeapPtrElementTraits class
ms.assetid: 910e0e06-3c8b-4242-bf00-b57eb74fbc77
ms.openlocfilehash: f09da968b264463eba759372e4e0756397e9978e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326873"
---
# <a name="cheapptrelementtraits-class"></a>Klasa CHeapPtrElementTraits

Ta klasa zawiera metody, funkcje statyczne i typedefs przydatne podczas tworzenia kolekcji wskaźników sterty.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template<typename T, class Allocator = ATL::CCRTAllocator>
class CHeapPtrElementTraits :
   public CDefaultElementTraits<ATL::CHeapPtr<T, Allocator>>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ obiektu, który ma być przechowywany w klasie kolekcji.

*Programu przydzielania*<br/>
Klasa alokacji pamięci do użycia. Wartość domyślna to [CCRTAllocator](../../atl/reference/ccrtallocator-class.md).

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|[CHeapPtrElementTraits::INARGTYPE](#inargtype)|Typ danych do dodania elementów do obiektu klasy kolekcji.|
|[CHeapPtrElementTraits::OUTARGTYPE](#outargtype)|Typ danych do użycia do pobierania elementów z obiektu klasy kolekcji.|

## <a name="remarks"></a>Uwagi

Ta klasa zawiera metody, funkcje statyczne i typedefs do wspomagania tworzenia obiektów klasy kolekcji zawierających wskaźniki sterty. Klasa `CHeapPtrList` wywodzi się od `CHeapPtrElementTraits`.

Aby uzyskać więcej informacji, zobacz [ATL Collection Classes](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits (Niem.](../../atl/reference/cdefaulthashtraits-class.md)

[Baza CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits (3.](../../atl/reference/cdefaultelementtraits-class.md)

`CHeapPtrElementTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="cheapptrelementtraitsinargtype"></a><a name="inargtype"></a>CHeapPtrElementTraits::INARGTYPE

Typ danych do dodania elementów do obiektu klasy kolekcji.

```
typedef CHeapPtr<T, Allocator>& INARGTYPE;
```

## <a name="cheapptrelementtraitsoutargtype"></a><a name="outargtype"></a>CHeapPtrElementTraits::OUTARGTYPE

Typ danych do użycia do pobierania elementów z obiektu klasy kolekcji.

```
typedef T *& OUTARGTYPE;
```

## <a name="see-also"></a>Zobacz też

[Klasa CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Klasa CComHeapPtr](../../atl/reference/ccomheapptr-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
