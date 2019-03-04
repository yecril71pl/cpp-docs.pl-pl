---
title: CAutoPtrList Class
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList::CAutoPtrList
helpviewer_keywords:
- CAutoPtrList class
ms.assetid: 11de4aca-28b0-4ff2-a74a-cb602312ffbd
ms.openlocfilehash: 2558c522f7903e8d59363cd77d1a86027f6a7511
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285415"
---
# <a name="cautoptrlist-class"></a>CAutoPtrList Class

Ta klasa dostarcza metody przydatne podczas tworzenia listy inteligentne wskaźniki.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

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
|[CAutoPtrList::CAutoPtrList](#cautoptrlist)|Konstruktor.|

## <a name="remarks"></a>Uwagi

Ta klasa zawiera konstruktora i pochodzi z metody z [CAtlList](../../atl/reference/catllist-class.md) i [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) ułatwiające tworzenie obiekt listy przechowywania inteligentnych wskaźników. Klasa [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) udostępnia podobną funkcję do tablicy obiektów.

Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CAtlList](../../atl/reference/catllist-class.md)

`CAutoPtrList`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

##  <a name="cautoptrlist"></a>  CAutoPtrList::CAutoPtrList

Konstruktor.

```
CAutoPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Rozmiar bloku z domyślną 10.

### <a name="remarks"></a>Uwagi

Rozmiar bloku jest miarą ilość pamięci przydzielonej, gdy nowy element jest wymagany. Większe rozmiary bloków zmniejszają liczbę interwencji do procedur alokacji pamięci, ale używa więcej zasobów.

## <a name="see-also"></a>Zobacz także

[Klasa CAtlList](../../atl/reference/catllist-class.md)<br/>
[Klasa CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
