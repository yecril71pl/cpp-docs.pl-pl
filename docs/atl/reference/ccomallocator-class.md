---
title: Klasa CComAllocator | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComAllocator
- ATLBASE/ATL::CComAllocator
- ATLBASE/ATL::CComAllocator::Allocate
- ATLBASE/ATL::CComAllocator::Free
- ATLBASE/ATL::CComAllocator::Reallocate
dev_langs: C++
helpviewer_keywords: CComAllocator class
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b1ba2b12110e4c312b84b2a24831687e782cc339
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccomallocator-class"></a>Klasa CComAllocator
Ta klasa dostarcza metody do zarządzania przy użyciu procedury pamięci COM pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```
class CComAllocator
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComAllocator::Allocate](#allocate)|Wywołanie tej metody statycznej można przydzielić pamięci.|  
|[CComAllocator::Free](#free)|Wywołanie tej metody statycznej zwolnienia alokacji pamięci.|  
|[CComAllocator::Reallocate](#reallocate)|Wywołanie tej metody statycznej ponownie przydzielić pamięci.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa jest używana przez [CComHeapPtr](../../atl/reference/ccomheapptr-class.md) do dostarczenia pamięci COM procedury alokacji. Klasa odpowiednikiem [CCRTAllocator](../../atl/reference/ccrtallocator-class.md), zapewnia te same metody, przy użyciu procedury CRT.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="allocate"></a>CComAllocator::Allocate  
 Wywołanie tej statycznych funkcji można przydzielić pamięci.  
  
```
static void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBytes`  
 Liczba bajtów do przydzielenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca typ void wskaźnik do przydzielone miejsce, lub wartość NULL, jeśli dostępnych jest za mało pamięci.  
  
### <a name="remarks"></a>Uwagi  
 Przydziela pamięć. Zobacz [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727) więcej szczegółów.  
  
##  <a name="free"></a>CComAllocator::Free  
 Wywołanie tej funkcji statycznych, aby zwolnić alokacji pamięci.  
  
```
static void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Wskaźnik do alokacji pamięci.  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia alokacji pamięci. Zobacz [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722) więcej szczegółów.  
  
##  <a name="reallocate"></a>CComAllocator::Reallocate  
 Wywołanie tej funkcji statycznych ponownie przydzielić pamięci.  
  
```
static void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Wskaźnik do alokacji pamięci.  
  
 `nBytes`  
 Liczba bajtów ponownie przydzielić.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik void przydzielone miejsce, lub wartość NULL, jeśli jest za mało pamięci  
  
### <a name="remarks"></a>Uwagi  
 Zmienia rozmiar ilość alokacji pamięci. Zobacz [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280) więcej szczegółów.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComHeapPtr](../../atl/reference/ccomheapptr-class.md)   
 [Klasa CCRTAllocator](../../atl/reference/ccrtallocator-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
