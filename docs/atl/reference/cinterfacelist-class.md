---
title: CInterfaceList Klasa
ms.date: 11/04/2016
f1_keywords:
- CInterfaceList
- ATLCOLL/ATL::CInterfaceList
- ATLCOLL/ATL::CInterfaceList::CInterfaceList
helpviewer_keywords:
- CInterfaceList class
ms.assetid: 2077764d-25e5-4b3d-96c8-08a287bbcd25
ms.openlocfilehash: 0a7fd781c63e4ea084cf078e49fc9efb9cfa2d85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326778"
---
# <a name="cinterfacelist-class"></a>CInterfaceList Klasa

Ta klasa zawiera metody przydatne podczas konstruowania listy wskaźników interfejsu COM.

## <a name="syntax"></a>Składnia

```
template<class I, const IID* piid =& __uuidof(I)>
class CInterfaceList
   : public CAtlList<ATL::CComQIPtr<I, piid>,
                     CComQIPtrElementTraits<I, piid>>
```

#### <a name="parameters"></a>Parametry

*I*<br/>
Interfejs COM określający typ wskaźnika do przechowywania.

*piid*<br/>
Wskaźnik do identyfikatora *I*.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInterfaceList::CInterfaceList](#cinterfacelist)|Konstruktor listy interfejsów.|

## <a name="remarks"></a>Uwagi

Ta klasa zawiera konstruktora i metody pochodne do tworzenia listy wskaźników interfejsu COM. Użyj [CInterfaceArray,](../../atl/reference/cinterfacearray-class.md) gdy wymagana jest tablica.

Aby uzyskać więcej informacji, zobacz [ATL Collection Classes](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Lista CAtl](../../atl/reference/catllist-class.md)

`CInterfaceList`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="cinterfacelistcinterfacelist"></a><a name="cinterfacelist"></a>CInterfaceList::CInterfaceList

Konstruktor listy interfejsów.

```
CInterfaceList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize (Rozmiar)*<br/>
Rozmiar bloku z domyślnym 10.

### <a name="remarks"></a>Uwagi

Rozmiar bloku jest miarą ilości pamięci przydzielonej, gdy wymagany jest nowy element. Większe rozmiary bloków zmniejszają liczbę wywołań procedur alokacji pamięci, ale zużywają więcej zasobów.

## <a name="see-also"></a>Zobacz też

[Klasa CAtlList](../../atl/reference/catllist-class.md)<br/>
[Klasa CComQIPtr](../../atl/reference/ccomqiptr-class.md)<br/>
[Klasa CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
