---
title: Klasa CStringRefElementTraits | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits::CompareElements
- ATLCOLL/ATL::CStringRefElementTraits::CompareElementsOrdered
- ATLCOLL/ATL::CStringRefElementTraits::Hash
dev_langs:
- C++
helpviewer_keywords:
- CStringRefElementTraits class
ms.assetid: cc15062d-5627-46cc-ac2b-1744afdc2dbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e8746bf216be417fb569aae58421b272c983914b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360690"
---
# <a name="cstringrefelementtraits-class"></a>Klasa CStringRefElementTraits
Ta klasa udostępnia statyczne funkcje związane z przechowywane w obiektach klasy kolekcji ciągów. Obiekty ciągu są traktowane jako odwołania.  
  
## <a name="syntax"></a>Składnia  
  
```
template <typename T>  
class CStringRefElementTraits : public CElementTraitsBase<T>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych ma być przechowywany w kolekcji.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CStringRefElementTraits::CompareElements](#compareelements)|Wywołanie tej funkcji statycznych, można porównać dwóch elementów ciąg pod kątem równości.|  
|[CStringRefElementTraits::CompareElementsOrdered](#compareelementsordered)|Wywołanie tej funkcji statycznych, aby porównać dwa elementy ciągu.|  
|[CStringRefElementTraits::Hash](#hash)|Wywołanie tej funkcji statycznych, aby obliczyć wartość skrótu dla elementu dany ciąg znaków.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa udostępnia statyczne funkcje dotyczące porównywanie ciągów i tworzenia wartość skrótu. Funkcje te są przydatne do przechowywania danych na podstawie ciągu przy użyciu klasy kolekcji. W odróżnieniu od [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md) i [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md), `CStringRefElementTraits` powoduje, że `CString` argumenty do przekazania jako **const cstring — &** odwołania.  
  
 Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 `CStringRefElementTraits`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcoll.h  
  
##  <a name="compareelements"></a>  CStringRefElementTraits::CompareElements  
 Wywołanie tej funkcji statycznych, można porównać dwóch elementów ciąg pod kątem równości.  
  
```
static bool CompareElements(INARGTYPE element1, INARGTYPE element2) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `element1`  
 Pierwszy ciąg elementu.  
  
 `element2`  
 Drugi ciąg elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli elementy są takie same, wartość false w przeciwnym razie wartość.  
  
##  <a name="compareelementsordered"></a>  CStringRefElementTraits::CompareElementsOrdered  
 Wywołanie tej funkcji statycznych, aby porównać dwa elementy ciągu.  
  
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
  
##  <a name="hash"></a>  CStringRefElementTraits::Hash  
 Wywołanie tej funkcji statycznych, aby obliczyć wartość skrótu dla elementu dany ciąg znaków.  
  
```
static ULONG Hash(INARGTYPE str) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `str`  
 String element.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość skrótu obliczane przy użyciu zawartości ciągu.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
