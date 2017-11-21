---
title: Klasa CStringElementTraitsI | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI::INARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::OUTARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::CompareElements
- ATLCOLL/ATL::CStringElementTraitsI::CompareElementsOrdered
- ATLCOLL/ATL::CStringElementTraitsI::Hash
dev_langs: C++
helpviewer_keywords: CStringElementTraitsI class
ms.assetid: c23f92b1-91e5-400f-96ed-258b02622b7a
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f2a2cbe93826ed2cad5d33d50df119d0ff5cb298
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cstringelementtraitsi-class"></a>Klasa CStringElementTraitsI
Ta klasa udostępnia statyczne funkcje związane z przechowywane w obiektach klasy kolekcji ciągów. Jest on podobny do [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md), ale wykonuje porównania bez uwzględniania wielkości liter.  
  
## <a name="syntax"></a>Składnia  
  
```
template <typename T, class CharTraits = CDefaultCharTraits<T ::XCHAR>>  
class CStringElementTraitsI : public CElementTraitsBase<T>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych ma być przechowywany w kolekcji.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CStringElementTraitsI::INARGTYPE](#inargtype)|Typ danych służących do dodawania elementów do obiektu klasy kolekcji.|  
|[CStringElementTraitsI::OUTARGTYPE](#outargtype)|Typ danych używany do pobierania elementów z kolekcji klasy obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CStringElementTraitsI::CompareElements](#compareelements)|Wywołanie tej funkcji statycznych, można porównać dwóch elementów ciąg pod kątem równości, ignorowanie różnice w przypadku.|  
|[CStringElementTraitsI::CompareElementsOrdered](#compareelementsordered)|Wywołanie tej funkcji statyczny do porównania dwóch elementów ciągu, ignorowanie różnice w przypadku.|  
|[CStringElementTraitsI::Hash](#hash)|Wywołanie tej funkcji statycznych, aby obliczyć wartość skrótu dla elementu dany ciąg znaków.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa udostępnia statyczne funkcje dotyczące porównywanie ciągów i tworzenia wartość skrótu. Funkcje te są przydatne do przechowywania danych na podstawie ciągu przy użyciu klasy kolekcji. Użyj [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) kiedy mają z traktowany jako odwołania do obiektów typu string.  
  
 Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 `CStringElementTraitsI`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcoll.h  
  
##  <a name="compareelements"></a>CStringElementTraitsI::CompareElements  
 Wywołanie tej funkcji statycznych, można porównać dwóch elementów ciąg pod kątem równości, ignorowanie różnice w przypadku.  
  
```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 Pierwszy ciąg elementu.  
  
 `str2`  
 Drugi ciąg elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli elementy są takie same, wartość false w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Bez uwzględniania wielkości liter podczas porównywania.  
  
##  <a name="compareelementsordered"></a>CStringElementTraitsI::CompareElementsOrdered  
 Wywołanie tej funkcji statyczny do porównania dwóch elementów ciągu, ignorowanie różnice w przypadku.  
  
```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 Pierwszy ciąg elementu.  
  
 `str2`  
 Drugi ciąg elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli ciągi są identyczne, < 0 Jeśli `str1` jest mniejsza niż `str2`, lub > 0 Jeśli `str1` jest większa niż `str2`. [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) metoda jest używana do wykonania porównania.  

  
### <a name="remarks"></a>Uwagi  
 Bez uwzględniania wielkości liter podczas porównywania.  
  
##  <a name="hash"></a>CStringElementTraitsI::Hash  
 Wywołanie tej funkcji statycznych, aby obliczyć wartość skrótu dla elementu dany ciąg znaków.  
  
```
static ULONG Hash(INARGTYPE str) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `str`  
 String element.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość skrótu obliczane przy użyciu zawartości ciągu.  
  
##  <a name="inargtype"></a>CStringElementTraitsI::INARGTYPE  
 Typ danych służących do dodawania elementów do obiektu klasy kolekcji.  
  
```
typedef T::PCXSTR INARGTYPE;
```  
  
##  <a name="outargtype"></a>CStringElementTraitsI::OUTARGTYPE  
 Typ danych używany do pobierania elementów z kolekcji klasy obiektu.  
  
```
typedef T& OUTARGTYPE;
```  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Klasa CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)
