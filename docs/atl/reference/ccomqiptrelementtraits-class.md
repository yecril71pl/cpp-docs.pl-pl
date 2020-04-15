---
title: Klasa CComQIPtrElementTraits
ms.date: 11/04/2016
f1_keywords:
- CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits::INARGTYPE
helpviewer_keywords:
- CComQIPtrElementTraits class
ms.assetid: 9df9250a-5413-4362-b133-332932a597c4
ms.openlocfilehash: 19f2669c157310be02f746672b22f6c0ed005075
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327411"
---
# <a name="ccomqiptrelementtraits-class"></a>Klasa CComQIPtrElementTraits

Ta klasa zawiera metody, funkcje statyczne i typedefs przydatne podczas tworzenia kolekcji wskaźników interfejsu COM.

## <a name="syntax"></a>Składnia

```
template<typename I, const IID* piid=& __uuidof(I)>
class CComQIPtrElementTraits :
   public CDefaultElementTraits<ATL::CComQIPtr<I, piid>>
```

#### <a name="parameters"></a>Parametry

*I*<br/>
Interfejs COM określający typ wskaźnika do przechowywania.

*piid*<br/>
Wskaźnik do identyfikatora *I*.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|[CComQIPtrElementTraits::INARGTYPE](#inargtype)|Typ danych do dodania elementów do obiektu klasy kolekcji.|

## <a name="remarks"></a>Uwagi

Ta klasa wyprowadza metody i zapewnia typedef przydatne podczas tworzenia klasy kolekcji [CComQIPtr](../../atl/reference/ccomqiptr-class.md) COM obiektów wskaźnika interfejsu. Ta klasa jest wykorzystywana przez [klasy CInterfaceArray](../../atl/reference/cinterfacearray-class.md) i [CInterfaceList.](../../atl/reference/cinterfacelist-class.md)

Aby uzyskać więcej informacji, zobacz [ATL Collection Classes](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits (Niem.](../../atl/reference/cdefaulthashtraits-class.md)

[Baza CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits (3.](../../atl/reference/cdefaultelementtraits-class.md)

`CComQIPtrElementTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="ccomqiptrelementtraitsinargtype"></a><a name="inargtype"></a>CComQIPtrElementTraits::INARGTYPE

Typ danych do dodania elementów do obiektu klasy kolekcji.

```
typedef I* INARGTYPE;
```

## <a name="see-also"></a>Zobacz też

[Klasa CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
