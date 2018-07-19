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
ms.openlocfilehash: 967ae999811e829ae7a890d367a6cdc16fb28239
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880492"
---
# <a name="cstringrefelementtraits-class"></a>Klasa CStringRefElementTraits
Ta klasa dostarcza statyczne funkcje związane z przechowywanych w obiektach klasy kolekcji ciągów. Obiektów w postaci ciągów są traktowane jako odwołania.  
  
## <a name="syntax"></a>Składnia  
  
```
template <typename T>  
class CStringRefElementTraits : public CElementTraitsBase<T>
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Typ danych, które mają być przechowywane w kolekcji.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CStringRefElementTraits::CompareElements](#compareelements)|Wywołaj tę funkcję statycznej, aby porównać dwa elementy ciągu dla równości.|  
|[CStringRefElementTraits::CompareElementsOrdered](#compareelementsordered)|Wywołaj tę funkcję statycznej, aby porównać dwa elementy ciągu.|  
|[CStringRefElementTraits::Hash](#hash)|Wywołaj tę funkcję statycznej, aby obliczyć wartość skrótu dla elementu dany ciąg znaków.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa dostarcza statycznej funkcji porównywania ciągów i tworzenia wartość skrótu. Te funkcje są przydatne w przypadku korzystania z klasy kolekcji do przechowywania danych w ciągu. W odróżnieniu od [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md) i [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md), `CStringRefElementTraits` powoduje, że `CString` argumenty do przekazania jako **const** `CString&` odwołania.  
  
 Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 `CStringRefElementTraits`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcoll.h  
  
##  <a name="compareelements"></a>  CStringRefElementTraits::CompareElements  
 Wywołaj tę funkcję statycznej, aby porównać dwa elementy ciągu dla równości.  
  
```
static bool CompareElements(INARGTYPE element1, INARGTYPE element2) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *element1*  
 Pierwszy ciąg elementu.  
  
 *element2*  
 Drugi ciąg elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli elementy są równe, wartość false w przeciwnym razie.  
  
##  <a name="compareelementsordered"></a>  CStringRefElementTraits::CompareElementsOrdered  
 Wywołaj tę funkcję statycznej, aby porównać dwa elementy ciągu.  
  
```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *str1*  
 Pierwszy ciąg elementu.  
  
 *str2*  
 Drugi ciąg elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli ciągi są identyczne, < 0 Jeśli *str1* jest mniejsza niż *str2*, lub > 0 Jeśli *str1* jest większa niż *str2*. [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) metoda służy do przeprowadzania porównania.  
  
##  <a name="hash"></a>  CStringRefElementTraits::Hash  
 Wywołaj tę funkcję statycznej, aby obliczyć wartość skrótu dla elementu dany ciąg znaków.  
  
```
static ULONG Hash(INARGTYPE str) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *str*  
 Element ciągu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość skrótu obliczane przy użyciu zawartości ciągu.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
