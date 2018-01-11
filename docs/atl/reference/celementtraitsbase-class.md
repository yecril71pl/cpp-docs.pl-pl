---
title: Klasa CElementTraitsBase | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase::INARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::OUTARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::CopyElements
- ATLCOLL/ATL::CElementTraitsBase::RelocateElements
dev_langs: C++
helpviewer_keywords: CElementTraitsBase class
ms.assetid: 75284caf-347e-4355-a7d8-efc708dd514a
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c9bbea69d2265563a0da4fda8b45cc09234a7789
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="celementtraitsbase-class"></a>Klasa CElementTraitsBase
Ta klasa udostępnia domyślna kopia i przenoszenie metody do klasy kolekcji.  
  
## <a name="syntax"></a>Składnia  
  
```
template<typename T>  
class CElementTraitsBase
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych ma być przechowywany w kolekcji.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CElementTraitsBase::INARGTYPE](#inargtype)|Typ danych służących do dodawania elementów do obiektu klasy kolekcji.|  
|[CElementTraitsBase::OUTARGTYPE](#outargtype)|Typ danych używany do pobierania elementów z kolekcji klasy obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CElementTraitsBase::CopyElements](#copyelements)|Wywołaj tę metodę, aby skopiować elementy przechowywane w obiekcie klasy kolekcji.|  
|[CElementTraitsBase::RelocateElements](#relocateelements)|Wywołanie tej metody może przenosić elementy przechowywane w obiekcie klasy kolekcji.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa podstawowa definiuje metody kopiowanie i przenoszenie elementów w klasie kolekcji. Jest wykorzystywany przez klasy [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md), [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md), i [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md).  
  
 Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcoll.h  
  
##  <a name="copyelements"></a>CElementTraitsBase::CopyElements  
 Wywołaj tę metodę, aby skopiować elementy przechowywane w obiekcie klasy kolekcji.  
  
```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>Parametry  
 `pDest`  
 Wskaźnik do pierwszego elementu, który będzie otrzymywał skopiowanych danych.  
  
 `pSrc`  
 Wskaźnik pierwszy element do skopiowania.  
  
 `nElements`  
 Liczba elementów do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Elementy źródłowe i docelowe nie powinny się nakładać.  
  
##  <a name="inargtype"></a>CElementTraitsBase::INARGTYPE  
 Typ danych służących do dodawania elementów do kolekcji.  
  
```
typedef const T& INARGTYPE;
```  
  
##  <a name="outargtype"></a>CElementTraitsBase::OUTARGTYPE  
 Typ danych używany do pobierania elementów z kolekcji.  
  
```
typedef T& OUTARGTYPE;
```  
  
##  <a name="relocateelements"></a>CElementTraitsBase::RelocateElements  
 Wywołanie tej metody może przenosić elementy przechowywane w obiekcie klasy kolekcji.  
  
```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>Parametry  
 `pDest`  
 Wskaźnik do pierwszego elementu, który otrzyma przeniesiono danych.  
  
 `pSrc`  
 Wskaźnik do pierwszego elementu do przeniesienia.  
  
 `nElements`  
 Liczba elementów do przeniesienia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wywołuje [memmove —](../../c-runtime-library/reference/memmove-wmemmove.md), która jest wystarczające dla większości typów danych. Jeśli obiekty przenoszony zawierają wskaźniki do ich własnych elementów członkowskich, ta metoda musi zostać zastąpiona.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
