---
title: Klasa CAutoPtrList
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList::CAutoPtrList
helpviewer_keywords:
- CAutoPtrList class
ms.assetid: 11de4aca-28b0-4ff2-a74a-cb602312ffbd
ms.openlocfilehash: 48c7ad6fe13c5f5fbbe5829c25ce1c27896841be
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318801"
---
# <a name="cautoptrlist-class"></a>Klasa CAutoPtrList

Ta klasa zawiera metody przydatne podczas konstruowania listy inteligentnych wskaźników.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template<typename E>
class CAutoPtrList :
   public CAtlList<ATL::CAutoPtr<E>, CAutoPtrElementTraits<E>>
```

#### <a name="parameters"></a>Parametry

*E*<br/>
Typ wskaźnika.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Lista CAutoPtr::Lista CAutoPtr](#cautoptrlist)|Konstruktor.|

## <a name="remarks"></a>Uwagi

Ta klasa udostępnia konstruktora i wyprowadza metody z [CAtlList](../../atl/reference/catllist-class.md) i [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) do tworzenia obiektu listy przechowywania inteligentnych wskaźników. Klasa [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) zapewnia podobną funkcję dla obiektu tablicowego.

Aby uzyskać więcej informacji, zobacz [ATL Collection Classes](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Lista CAtl](../../atl/reference/catllist-class.md)

`CAutoPtrList`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="cautoptrlistcautoptrlist"></a><a name="cautoptrlist"></a>Lista CAutoPtr::Lista CAutoPtr

Konstruktor.

```
CAutoPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize (Rozmiar)*<br/>
Rozmiar bloku z domyślnym 10.

### <a name="remarks"></a>Uwagi

Rozmiar bloku jest miarą ilości pamięci przydzielonej, gdy wymagany jest nowy element. Większe rozmiary bloków zmniejszają liczbę wywołań procedur alokacji pamięci, ale zużywają więcej zasobów.

## <a name="see-also"></a>Zobacz też

[Klasa CAtlList](../../atl/reference/catllist-class.md)<br/>
[Klasa CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
