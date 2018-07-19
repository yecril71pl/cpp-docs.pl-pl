---
title: Klasa CHeapPtrElementTraits | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CHeapPtrElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtrElementTraits class
ms.assetid: 910e0e06-3c8b-4242-bf00-b57eb74fbc77
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1aa3921f79e8c368fe4a42c3b56ede27f436e25
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884103"
---
# <a name="cheapptrelementtraits-class"></a>Klasa CHeapPtrElementTraits
Ta klasa dostarcza metody, funkcje statyczne i definicje typów przydatne podczas tworzenia kolekcji wskaźniki stosu.  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<typename T, class Allocator = ATL::CCRTAllocator>  
class CHeapPtrElementTraits : 
   public CDefaultElementTraits<ATL::CHeapPtr<T, Allocator>>
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Typ obiektu, który ma być przechowywany w klasie kolekcji.  
  
 *Allocator*  
 Klasa alokacji pamięci do użycia. Wartość domyślna to [CCRTAllocator](../../atl/reference/ccrtallocator-class.md).  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Publiczne definicje typów  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHeapPtrElementTraits::INARGTYPE](#inargtype)|Typ danych na potrzeby dodawania elementów do obiektu klasy kolekcji.|  
|[CHeapPtrElementTraits::OUTARGTYPE](#outargtype)|Typ danych używany do pobierania elementów z obiektu klasy kolekcji.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa dostarcza metody, funkcje statyczne i definicje typów dla łatwiejszemu tworzenia typów obiektów klas kolekcji zawierające wskaźniki stosu. Klasa `CHeapPtrList` pochodzi od klasy `CHeapPtrElementTraits`.  
  
 Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CHeapPtrElementTraits`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcoll.h  
  
##  <a name="inargtype"></a>  CHeapPtrElementTraits::INARGTYPE  
 Typ danych na potrzeby dodawania elementów do obiektu klasy kolekcji.  
  
```
typedef CHeapPtr<T, Allocator>& INARGTYPE;
```  
  
##  <a name="outargtype"></a>  CHeapPtrElementTraits::OUTARGTYPE  
 Typ danych używany do pobierania elementów z obiektu klasy kolekcji.  
  
```
typedef T *& OUTARGTYPE;
```  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)   
 [Klasa CComHeapPtr](../../atl/reference/ccomheapptr-class.md)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
