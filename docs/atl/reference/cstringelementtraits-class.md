---
title: Klasa CStringElementTraits | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits::INARGTYPE
- CSTRINGT/ATL::CStringElementTraits::OUTARGTYPE
- CSTRINGT/ATL::CStringElementTraits::CompareElements
- CSTRINGT/ATL::CStringElementTraits::CompareElementsOrdered
- CSTRINGT/ATL::CStringElementTraits::CopyElements
- CSTRINGT/ATL::CStringElementTraits::Hash
- CSTRINGT/ATL::CStringElementTraits::RelocateElements
dev_langs:
- C++
helpviewer_keywords:
- CStringElementTraits class
ms.assetid: 74d7134b-099d-4455-bf91-3e68ccbf95bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ddce07ed7f79c167d4cf819b85de1484346bba93
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="cstringelementtraits-class"></a>Klasa CStringElementTraits
Ta klasa udostępnia funkcje statyczne używane przez klasy kolekcji przechowywania `CString` obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```
template <typename T>  
class CStringElementTraits
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych ma być przechowywany w kolekcji.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CStringElementTraits::INARGTYPE](#inargtype)|Typ danych służących do dodawania elementów do obiektu klasy kolekcji.|  
|[CStringElementTraits::OUTARGTYPE](#outargtype)|Typ danych używany do pobierania elementów z kolekcji klasy obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CStringElementTraits::CompareElements](#compareelements)|(Statyczny) Wywołanie tej funkcji można porównać dwóch elementów ciąg pod kątem równości.|  
|[CStringElementTraits::CompareElementsOrdered](#compareelementsordered)|(Statyczny) Wywołanie tej funkcji można porównać dwóch elementów ciągu.|  
|[CStringElementTraits::CopyElements](#copyelements)|(Statyczny) Wywołanie tej funkcji, aby skopiować `CString` elementy przechowywane w obiekcie klasy kolekcji.|  
|[CStringElementTraits::Hash](#hash)|(Statyczny) Wywołanie tej funkcji, aby obliczyć wartość skrótu dla elementu dany ciąg znaków.|  
|[CStringElementTraits::RelocateElements](#relocateelements)|(Statyczny) Wywołanie tej funkcji może przenosić `CString` elementy przechowywane w obiekcie klasy kolekcji.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa udostępnia statyczne funkcje kopiowania, przenoszenie i porównywanie ciągów i tworzenia wartość skrótu. Funkcje te są przydatne do przechowywania danych na podstawie ciągu przy użyciu klasy kolekcji. Użyj [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md) podczas porównania bez uwzględniania wielkości liter są wymagane. Użyj [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) kiedy mają będzie traktowane jako odwołania do obiektów typu string.  
  
 Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cstringt.h  
  
##  <a name="compareelements"></a>  CStringElementTraits::CompareElements  
 Wywołanie tej funkcji statycznych, można porównać dwóch elementów ciąg pod kątem równości.  
  
```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2);
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 Pierwszy ciąg elementu.  
  
 `str2`  
 Drugi ciąg elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli elementy są takie same, wartość false w przeciwnym razie wartość.  
  
##  <a name="compareelementsordered"></a>  CStringElementTraits::CompareElementsOrdered  
 Wywołanie tej funkcji statycznych, aby porównać dwa elementy ciągu.  
  
```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2);
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 Pierwszy ciąg elementu.  
  
 `str2`  
 Drugi ciąg elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli ciągi są identyczne, < 0 Jeśli `str1` jest mniejsza niż `str2`, lub > 0 Jeśli `str1` jest większa niż `str2`. [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) metoda jest używana do wykonania porównania.  

  
##  <a name="copyelements"></a>  CStringElementTraits::CopyElements  
 Wywołanie tej funkcji statycznych, aby skopiować `CString` elementy przechowywane w obiekcie klasy kolekcji.  
  
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
  
##  <a name="hash"></a>  CStringElementTraits::Hash  
 Wywołanie tej funkcji statycznych, aby obliczyć wartość skrótu dla elementu dany ciąg znaków.  
  
```
static ULONG Hash(INARGTYPE str);
```  
  
### <a name="parameters"></a>Parametry  
 `str`  
 String element.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość skrótu obliczane przy użyciu zawartości ciągu.  
  
##  <a name="inargtype"></a>  CStringElementTraits::INARGTYPE  
 Typ danych służących do dodawania elementów do obiektu klasy kolekcji.  
  
```
typedef T::PCXSTR INARGTYPE;
```  
  
##  <a name="outargtype"></a>  CStringElementTraits::OUTARGTYPE  
 Typ danych używany do pobierania elementów z kolekcji klasy obiektu.  
  
```
typedef T& OUTARGTYPE;
```  
  
##  <a name="relocateelements"></a>  CStringElementTraits::RelocateElements  
 Wywołanie tej funkcji statycznych może przenosić `CString` elementy przechowywane w obiekcie klasy kolekcji.  
  
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
 Ta funkcja statyczna wywołuje [memmove —](../../c-runtime-library/reference/memmove-wmemmove.md), która jest wystarczające dla większości typów danych. Jeśli obiekty przenoszony zawierają wskaźniki do ich własnych elementów członkowskich, ta funkcja statyczna musi zostać zastąpiona.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)   
 [Klasa CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
