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
ms.openlocfilehash: 84b4241dcad8d54321aea37c7055c6669ff3ca87
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245650"
---
# <a name="cheapptrlist-class"></a>Klasa CHeapPtrList

Ta klasa dostarcza metody przydatne podczas tworzenia listy wskaźników sterty.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

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

*Allocator*<br/>
Klasa alokacji pamięci do użycia. Wartość domyślna to [CCRTAllocator](../../atl/reference/ccrtallocator-class.md).

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHeapPtrList::CHeapPtrList](#cheapptrlist)|Konstruktor.|

## <a name="remarks"></a>Uwagi

Ta klasa zawiera konstruktora i pochodzi z metody z [CAtlList](../../atl/reference/catllist-class.md) i [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md) ułatwiające tworzenie obiektu klasy kolekcji przechowywania wskaźniki stosu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CAtlList](../../atl/reference/catllist-class.md)

`CHeapPtrList`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

##  <a name="cheapptrlist"></a>  CHeapPtrList::CHeapPtrList

Konstruktor.

```
CHeapPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Rozmiar bloku.

### <a name="remarks"></a>Uwagi

Rozmiar bloku jest miarą ilość pamięci przydzielonej, gdy nowy element jest wymagany. Większe rozmiary bloków zmniejszają liczbę interwencji do procedur alokacji pamięci, ale używa więcej zasobów.

## <a name="see-also"></a>Zobacz także

[Klasa CAtlList](../../atl/reference/catllist-class.md)<br/>
[Klasa CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Klasa CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
