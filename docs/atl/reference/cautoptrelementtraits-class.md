---
title: Klasa CAutoPtrElementTraits | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoPtrElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtrElementTraits class
ms.assetid: 777c1b14-6ab7-491f-b9a5-be149e71d4a2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ffbec269e7bbf750cc3b877aa7a93d1cde74756b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cautoptrelementtraits-class"></a>Klasa CAutoPtrElementTraits
Ta klasa udostępnia metody statyczne funkcje i definicje typów przydatne podczas tworzenia kolekcji wskaźniki inteligentne.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<typename T>  
class CAutoPtrElementTraits 
    : public CDefaultElementTraits<ATL::CAutoPtr<T>>
```    
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ wskaźnika.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAutoPtrElementTraits::INARGTYPE](#inargtype)|Typ danych służących do dodawania elementów do obiektu klasy kolekcji.|  
|[CAutoPtrElementTraits::OUTARGTYPE](#outargtype)|Typ danych używany do pobierania elementów z kolekcji klasy obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa udostępnia metody statyczne funkcje i definicje typów dla nawiąże tworzenie kolekcji obiektów klasy zawierające wskaźniki inteligentne. Klasy [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) i [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) pochodzi od `CAutoPtrElementTraits`. Jeśli tworzenie kolekcji wskaźniki inteligentne, które wymaga nowy wektor i usuwanie operatorów, należy użyć [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) zamiast tego.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CAutoPtrElementTraits`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcoll.h  
  
##  <a name="inargtype"></a>CAutoPtrElementTraits::INARGTYPE  
 Typ danych służących do dodawania elementów do obiektu klasy kolekcji.  
  
```
typedef CAutoPtr<T>& INARGTYPE;
```  
  
##  <a name="outargtype"></a>CAutoPtrElementTraits::OUTARGTYPE  
 Typ danych używany do pobierania elementów z kolekcji klasy obiektu.  
  
```
typedef T *& OUTARGTYPE;
```  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
