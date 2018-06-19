---
title: Klasa CCRTHeap | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CCRTHeap
- ATLMEM/ATL::CCRTHeap
- ATLMEM/ATL::CCRTHeap::Allocate
- ATLMEM/ATL::CCRTHeap::Free
- ATLMEM/ATL::CCRTHeap::GetSize
- ATLMEM/ATL::CCRTHeap::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CCRTHeap class
ms.assetid: 321bd6c5-1856-4ff7-8590-95044a1209f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 83655bddfb56bdd0e532b520b2389278e3fbd762
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363849"
---
# <a name="ccrtheap-class"></a>Klasa CCRTHeap
Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji CRT stosu.  
  
## <a name="syntax"></a>Składnia  
  
```
class CCRTHeap : public IAtlMemMgr
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCRTHeap::Allocate](#allocate)|Wywołanie tej metody można przydzielić bloku pamięci.|  
|[CCRTHeap::Free](#free)|Wywołanie tej metody, aby zwolnić blok pamięci przydzielonej przez ten Menedżer pamięci.|  
|[CCRTHeap::GetSize](#getsize)|Wywołaj tę metodę, aby pobrać przydzielony rozmiar bloku pamięci przydzielonej przez ten Menedżer pamięci.|  
|[CCRTHeap::Reallocate](#reallocate)|Wywołaj tę metodę, aby ponownie przydzielić pamięci przydzielonej przez ten Menedżer pamięci.|  
  
## <a name="remarks"></a>Uwagi  
 `CCRTHeap` implementuje pamięci funkcji alokacji przy użyciu CRT stercie funkcji, w tym [— funkcja malloc](../../c-runtime-library/reference/malloc.md), [wolnego](../../c-runtime-library/reference/free.md), [realloc](../../c-runtime-library/reference/realloc.md), i [_msize —](../../c-runtime-library/reference/msize.md).  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IAtlMemMgr`  
  
 `CCRTHeap`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlmem.h  
  
##  <a name="allocate"></a>  CCRTHeap::Allocate  
 Wywołanie tej metody można przydzielić bloku pamięci.  
  
```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBytes`  
 Żądana liczba bajtów w nowego bloku pamięci.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do rozpoczęcia bloku nowo alokacji pamięci.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie [CCRTHeap::Free](#free) lub [CCRTHeap::Reallocate](#reallocate) zwolnienia pamięci przydzielonej przez tę metodę.  
  
 Implementowane za pomocą [— funkcja malloc](../../c-runtime-library/reference/malloc.md).  
  
##  <a name="free"></a>  CCRTHeap::Free  
 Wywołanie tej metody, aby zwolnić blok pamięci przydzielonej przez ten Menedżer pamięci.  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Wskaźnik do pamięci przydzielonej wcześniej przez tego menedżera pamięci. Wartość NULL jest nieprawidłowa i nie działają.  
  
### <a name="remarks"></a>Uwagi  
 Implementowane za pomocą [wolnego](../../c-runtime-library/reference/free.md).  
  
##  <a name="getsize"></a>  CCRTHeap::GetSize  
 Wywołaj tę metodę, aby pobrać przydzielony rozmiar bloku pamięci przydzielonej przez ten Menedżer pamięci.  
  
```
virtual size_t GetSize(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Wskaźnik do pamięci przydzielonej wcześniej przez tego menedżera pamięci.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca blok pamięci przydzielony rozmiar w bajtach.  
  
### <a name="remarks"></a>Uwagi  
 Implementowane za pomocą [_msize —](../../c-runtime-library/reference/msize.md).  
  
##  <a name="reallocate"></a>  CCRTHeap::Reallocate  
 Wywołaj tę metodę, aby ponownie przydzielić pamięci przydzielonej przez ten Menedżer pamięci.  
  
```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Wskaźnik do pamięci przydzielonej wcześniej przez tego menedżera pamięci.  
  
 `nBytes`  
 Żądana liczba bajtów w nowego bloku pamięci.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do rozpoczęcia bloku nowo alokacji pamięci.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie [CCRTHeap::Free](#free) zwolnienia pamięci przydzielonej przez tę metodę. Implementowane za pomocą [realloc](../../c-runtime-library/reference/realloc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Klasa CComHeap](../../atl/reference/ccomheap-class.md)   
 [Klasa CWin32Heap](../../atl/reference/cwin32heap-class.md)   
 [Klasa CLocalHeap](../../atl/reference/clocalheap-class.md)   
 [Klasa CGlobalHeap](../../atl/reference/cglobalheap-class.md)   
 [Klasa IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
