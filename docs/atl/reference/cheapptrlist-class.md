---
title: Klasa CHeapPtrList | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList::CHeapPtrList
dev_langs: C++
helpviewer_keywords: CHeapPtrList class
ms.assetid: cc70e585-362a-4007-81db-c705eb181226
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 18d4847c53e7926abecba43dd55f44acd22ed2f0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cheapptrlist-class"></a>Klasa CHeapPtrList
Ta klasa dostarcza metody przydatne podczas konstruowania listy wskaźniki stosu.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<typename E, class Allocator = ATL::CCRTAllocator>  
class CHeapPtrList 
   : public CAtlList<ATL::CHeapPtr<E, Allocator>,
                     CHeapPtrElementTraits<E, Allocator>>
```  
  
#### <a name="parameters"></a>Parametry  
 `E`  
 Typ obiektu do zapisania w klasie kolekcji.  
  
 `Allocator`  
 Klasa alokacji pamięci do użycia. Wartość domyślna to [CCRTAllocator](../../atl/reference/ccrtallocator-class.md).  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHeapPtrList::CHeapPtrList](#cheapptrlist)|Konstruktor.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa zawiera konstruktora i pochodzi z metody [CAtlList](../../atl/reference/catllist-class.md) i [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md) ułatwiających tworzenie obiektu klasy zbierania, przechowywania wskaźniki stosu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CHeapPtrList`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcoll.h  
  
##  <a name="cheapptrlist"></a>CHeapPtrList::CHeapPtrList  
 Konstruktor.  
  
```
CHeapPtrList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBlockSize`  
 Rozmiar bloku.  
  
### <a name="remarks"></a>Uwagi  
 Rozmiar bloku jest miarą ilość pamięci przydzielonej, gdy nowy element jest wymagany. Większe rozmiary bloków zmniejszyć wywołania procedury alokacji pamięci, ale użyj więcej zasobów.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CAtlList](../../atl/reference/catllist-class.md)   
 [Klasa CHeapPtr](../../atl/reference/cheapptr-class.md)   
 [Klasa CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
