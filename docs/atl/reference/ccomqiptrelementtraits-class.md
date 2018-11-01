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
ms.openlocfilehash: df1bbf5cb36e45b6b47acbd4263c34a7353fd6ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603739"
---
# <a name="ccomqiptrelementtraits-class"></a>Klasa CComQIPtrElementTraits

Ta klasa dostarcza metody, funkcje statyczne i definicje typów przydatne podczas tworzenia kolekcji wskaźniki interfejsu COM.

## <a name="syntax"></a>Składnia

```
template<typename I, const IID* piid=& __uuidof(I)>
class CComQIPtrElementTraits :
   public CDefaultElementTraits<ATL::CComQIPtr<I, piid>>
```

#### <a name="parameters"></a>Parametry

*I*<br/>
Interfejs COM, określając typ wskaźnika, które mają być przechowywane.

*piid*<br/>
Wskaźnik do identyfikatora IID z *I*.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[CComQIPtrElementTraits::INARGTYPE](#inargtype)|Typ danych na potrzeby dodawania elementów do obiektu klasy kolekcji.|

## <a name="remarks"></a>Uwagi

Ta klasa pochodzi z metody i zawiera element typedef, które są przydatne podczas tworzenia klasy kolekcji [CComQIPtr](../../atl/reference/ccomqiptr-class.md) obiektów wskaźnika interfejsu COM. Ta klasa jest używana przez obie [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) i [CInterfaceList](../../atl/reference/cinterfacelist-class.md) klasy.

Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CComQIPtrElementTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

##  <a name="inargtype"></a>  CComQIPtrElementTraits::INARGTYPE

Typ danych na potrzeby dodawania elementów do obiektu klasy kolekcji.

```
typedef I* INARGTYPE;
```

## <a name="see-also"></a>Zobacz też

[Klasa CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
