---
title: Klasa CElementTraitsBase | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase::INARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::OUTARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::CopyElements
- ATLCOLL/ATL::CElementTraitsBase::RelocateElements
dev_langs:
- C++
helpviewer_keywords:
- CElementTraitsBase class
ms.assetid: 75284caf-347e-4355-a7d8-efc708dd514a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1173633cd720ed6ee0e4aacdf75a8b305fdbfe4d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043368"
---
# <a name="celementtraitsbase-class"></a>Klasa CElementTraitsBase

Ta klasa zawiera kopię domyślnego i przenoszenie metody do klasy kolekcji.

## <a name="syntax"></a>Składnia

```
template<typename T>
class CElementTraitsBase
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych, które mają być przechowywane w kolekcji.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[CElementTraitsBase::INARGTYPE](#inargtype)|Typ danych na potrzeby dodawania elementów do obiektu klasy kolekcji.|
|[CElementTraitsBase::OUTARGTYPE](#outargtype)|Typ danych używany do pobierania elementów z obiektu klasy kolekcji.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CElementTraitsBase::CopyElements](#copyelements)|Wywołaj tę metodę można skopiować elementów przechowywanych w obiekcie klasy kolekcji.|
|[CElementTraitsBase::RelocateElements](#relocateelements)|Wywołaj tę metodę, aby zmienić lokalizację elementów przechowywanych w obiekcie klasy kolekcji.|

## <a name="remarks"></a>Uwagi

Ta klasa bazowa definiuje metody kopiowanie i przenoszenie elementów w klasie kolekcji. Jest wykorzystywany przez klasy [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md), [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md), i [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md).

Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

##  <a name="copyelements"></a>  CElementTraitsBase::CopyElements

Wywołaj tę metodę można skopiować elementów przechowywanych w obiekcie klasy kolekcji.

```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Parametry

*pDest*<br/>
Wskaźnik do pierwszego elementu, który będzie otrzymywać dane skopiowane.

*pSrc*<br/>
Wskaźnik do pierwszego elementu, aby skopiować.

*nElements*<br/>
Liczba elementów do skopiowania.

### <a name="remarks"></a>Uwagi

Elementy źródłowe i docelowe nie powinny nakładać się na.

##  <a name="inargtype"></a>  CElementTraitsBase::INARGTYPE

Typ danych na potrzeby dodawania elementów do kolekcji.

```
typedef const T& INARGTYPE;
```

##  <a name="outargtype"></a>  CElementTraitsBase::OUTARGTYPE

Typ danych używany do pobierania elementów z kolekcji.

```
typedef T& OUTARGTYPE;
```

##  <a name="relocateelements"></a>  CElementTraitsBase::RelocateElements

Wywołaj tę metodę, aby zmienić lokalizację elementów przechowywanych w obiekcie klasy kolekcji.

```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Parametry

*pDest*<br/>
Wskaźnik do pierwszego elementu, który będzie otrzymywać dane przenoszone.

*pSrc*<br/>
Wskaźnik do pierwszego elementu przenosić.

*nElements*<br/>
Liczba elementów do przeniesienia.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [memmove](../../c-runtime-library/reference/memmove-wmemmove.md), który jest wystarczające dla większości typów danych. Jeśli obiektów jest przenoszony zawierają wskaźniki do ich własnych elementów członkowskich, ta metoda należy do zastąpienia.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../../atl/atl-class-overview.md)
