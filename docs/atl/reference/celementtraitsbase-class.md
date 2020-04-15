---
title: Klasa CElementTraitsBase
ms.date: 11/04/2016
f1_keywords:
- CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase::INARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::OUTARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::CopyElements
- ATLCOLL/ATL::CElementTraitsBase::RelocateElements
helpviewer_keywords:
- CElementTraitsBase class
ms.assetid: 75284caf-347e-4355-a7d8-efc708dd514a
ms.openlocfilehash: 5a29e8778cf2f3400df25b55574950a005bad995
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327005"
---
# <a name="celementtraitsbase-class"></a>Klasa CElementTraitsBase

Ta klasa zawiera domyślne metody kopiowania i przenoszenia dla klasy kolekcji.

## <a name="syntax"></a>Składnia

```
template<typename T>
class CElementTraitsBase
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych, które mają być przechowywane w kolekcji.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|[CElementTraitsBase::INARGTYPE](#inargtype)|Typ danych do dodania elementów do obiektu klasy kolekcji.|
|[CElementTraitsBase::OUTARGTYPE](#outargtype)|Typ danych do użycia do pobierania elementów z obiektu klasy kolekcji.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CElementTraitsBase::CopyElements](#copyelements)|Wywołanie tej metody, aby skopiować elementy przechowywane w obiekcie klasy kolekcji.|
|[CElementTraitsBase::RelocateElements](#relocateelements)|Wywołanie tej metody, aby przenieść elementy przechowywane w obiekcie klasy kolekcji.|

## <a name="remarks"></a>Uwagi

Ta klasa podstawowa definiuje metody kopiowania i przenoszenia elementów w klasie kolekcji. Jest on używany przez klasy [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md), [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)i [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md).

Aby uzyskać więcej informacji, zobacz [ATL Collection Classes](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="celementtraitsbasecopyelements"></a><a name="copyelements"></a>CElementTraitsBase::CopyElements

Wywołanie tej metody, aby skopiować elementy przechowywane w obiekcie klasy kolekcji.

```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Parametry

*pDest (właśc.*<br/>
Wskaźnik do pierwszego elementu, który otrzyma skopiowane dane.

*Psrc*<br/>
Wskaźnik do pierwszego elementu do skopiowania.

*nElementy*<br/>
Liczba elementów do skopiowania.

### <a name="remarks"></a>Uwagi

Elementy źródłowe i docelowe nie powinny nakładać się na siebie.

## <a name="celementtraitsbaseinargtype"></a><a name="inargtype"></a>CElementTraitsBase::INARGTYPE

Typ danych do użycia do dodawania elementów do kolekcji.

```
typedef const T& INARGTYPE;
```

## <a name="celementtraitsbaseoutargtype"></a><a name="outargtype"></a>CElementTraitsBase::OUTARGTYPE

Typ danych do użycia do pobierania elementów z kolekcji.

```
typedef T& OUTARGTYPE;
```

## <a name="celementtraitsbaserelocateelements"></a><a name="relocateelements"></a>CElementTraitsBase::RelocateElements

Wywołanie tej metody, aby przenieść elementy przechowywane w obiekcie klasy kolekcji.

```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Parametry

*pDest (właśc.*<br/>
Wskaźnik do pierwszego elementu, który otrzyma przeniesione dane.

*Psrc*<br/>
Wskaźnik do pierwszego elementu do przeniesienia.

*nElementy*<br/>
Liczba elementów do przeniesienia.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [memmove](../../c-runtime-library/reference/memmove-wmemmove.md), co jest wystarczające dla większości typów danych. Jeśli obiekty są przenoszone zawierają wskaźniki do własnych elementów członkowskich, ta metoda będzie musiała zostać zastąpiona.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
