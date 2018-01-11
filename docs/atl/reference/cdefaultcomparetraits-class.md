---
title: Klasa CDefaultCompareTraits | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElements
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElementsOrdered
dev_langs: C++
helpviewer_keywords: CDefaultCompareTraits class
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 13c8bfd8ac02979f82e205ec86269b7ac40c8b08
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cdefaultcomparetraits-class"></a>Klasa CDefaultCompareTraits
Ta klasa udostępnia domyślny element porównanie funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```
template<typename T>  
class CDefaultCompareTraits
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych ma być przechowywany w kolekcji.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDefaultCompareTraits::CompareElements](#compareelements)|(Statyczny) Wywołanie tej funkcji można porównać dwóch elementów pod kątem równości.|  
|[CDefaultCompareTraits::CompareElementsOrdered](#compareelementsordered)|(Statyczny) Wywołanie tej funkcji można określić elementu większa i mniejsza.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa zawiera dwie funkcje statyczne porównywania elementy przechowywane w obiekcie klasy kolekcji. Ta klasa jest wykorzystywany przez [CDefaultElementTraits klasy](../../atl/reference/cdefaultelementtraits-class.md).  
  
 Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcoll.h  
  
##  <a name="compareelements"></a>CDefaultCompareTraits::CompareElements  
 Wywołanie tej funkcji można porównać dwóch elementów pod kątem równości.  
  
```
static bool CompareElements(const T& element1, const T& element2);
```  
  
### <a name="parameters"></a>Parametry  
 `element1`  
 Pierwszy element.  
  
 `element2`  
 Drugi element.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli elementy są takie same, wartość false w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja tej funkcji jest równości ( `==`) operatora. Obiekty inne niż proste typy danych ta funkcja może być konieczne do zastąpienia.  
  
##  <a name="compareelementsordered"></a>CDefaultCompareTraits::CompareElementsOrdered  
 Wywołanie tej funkcji można określić elementu większa i mniejsza.  
  
```
static int CompareElementsOrdered(const T& element1, const T& element2);
```  
  
### <a name="parameters"></a>Parametry  
 `element1`  
 Pierwszy element.  
  
 `element2`  
 Drugi element.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę całkowitą na podstawie poniższej tabeli:  
  
|Warunek|Wartość zwracana|  
|---------------|------------------|  
|`element1` < `element2`|<0|  
|`element1` == `element2`|0|  
|`element1` > `element2`|>0|  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja tej funkcji używa `==`,  **\<** , i  **>**  operatorów. Obiekty inne niż proste typy danych ta funkcja może być konieczne do zastąpienia.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
