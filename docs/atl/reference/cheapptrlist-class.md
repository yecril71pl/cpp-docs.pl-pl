---
title: Klasa CHeapPtrList
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList::CHeapPtrList
helpviewer_keywords:
- CHeapPtrList class
ms.assetid: cc70e585-362a-4007-81db-c705eb181226
ms.openlocfilehash: 0500ab8f76049aeaf1c89355ea5450a93243b734
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326857"
---
# <a name="cheapptrlist-class"></a>Klasa CHeapPtrList

Ta klasa zawiera metody przydatne podczas konstruowania listy wskaźników sterty.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template<typename E, class Allocator = ATL::CCRTAllocator>
class CHeapPtrList
   : public CAtlList<ATL::CHeapPtr<E, Allocator>,
                     CHeapPtrElementTraits<E, Allocator>>
```

#### <a name="parameters"></a>Parametry

*E*<br/>
Typ obiektu, który ma być przechowywany w klasie kolekcji.

*Programu przydzielania*<br/>
Klasa alokacji pamięci do użycia. Wartość domyślna to [CCRTAllocator](../../atl/reference/ccrtallocator-class.md).

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Lista CHeapPtr::CHeapPtrList](#cheapptrlist)|Konstruktor.|

## <a name="remarks"></a>Uwagi

Ta klasa udostępnia konstruktora i wyprowadza metody z [CAtlList](../../atl/reference/catllist-class.md) i [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md) do tworzenia właściwości klasy kolekcji przechowywania wskaźników sterty.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Lista CAtl](../../atl/reference/catllist-class.md)

`CHeapPtrList`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="cheapptrlistcheapptrlist"></a><a name="cheapptrlist"></a>Lista CHeapPtr::CHeapPtrList

Konstruktor.

```
CHeapPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize (Rozmiar)*<br/>
Rozmiar bloku.

### <a name="remarks"></a>Uwagi

Rozmiar bloku jest miarą ilości pamięci przydzielonej, gdy wymagany jest nowy element. Większe rozmiary bloków zmniejszają liczbę wywołań procedur alokacji pamięci, ale zużywają więcej zasobów.

## <a name="see-also"></a>Zobacz też

[Klasa CAtlList](../../atl/reference/catllist-class.md)<br/>
[Klasa CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Klasa CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
