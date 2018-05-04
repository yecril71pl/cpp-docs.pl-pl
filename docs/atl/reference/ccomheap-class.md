---
title: Klasa CComHeap | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComHeap
- ATLCOMMEM/ATL::CComHeap
- ATLCOMMEM/ATL::CComHeap::Allocate
- ATLCOMMEM/ATL::CComHeap::Free
- ATLCOMMEM/ATL::CComHeap::GetSize
- ATLCOMMEM/ATL::CComHeap::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CComHeap class
ms.assetid: c74183ce-98ae-46fb-b186-93ea4cf0222b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75bd4ad2f182d2a9f62e82b78f9ee9d0db44fa00
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ccomheap-class"></a>Klasa CComHeap
Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji alokacji pamięci COM.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CComHeap : public IAtlMemMgr
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComHeap::Allocate](#allocate)|Wywołanie tej metody można przydzielić bloku pamięci.|  
|[CComHeap::Free](#free)|Wywołanie tej metody, aby zwolnić blok pamięci przydzielonej przez ten Menedżer pamięci.|  
|[CComHeap::GetSize](#getsize)|Wywołaj tę metodę, aby pobrać przydzielony rozmiar bloku pamięci przydzielonej przez ten Menedżer pamięci.|  
|[CComHeap::Reallocate](#reallocate)|Wywołaj tę metodę, aby ponownie przydzielić pamięci przydzielonej przez ten Menedżer pamięci.|  
  
## <a name="remarks"></a>Uwagi  
 `CComHeap` implementuje funkcje alokacji pamięci przy użyciu funkcji alokacji COM, w tym [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727), [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722), [IMalloc::GetSize](http://msdn.microsoft.com/library/windows/desktop/ms691226)i [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280). Maksymalna ilość pamięci, która może być przydzielona jest równa **int_max —** (2147483647) bajtów.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IAtlMemMgr`  
  
 `CComHeap`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ATLComMem.h  
  
##  <a name="allocate"></a>  CComHeap::Allocate  
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
 Wywołanie [CComHeap::Free](#free) lub [CComHeap::Reallocate](#reallocate) zwolnienia pamięci przydzielonej przez tę metodę.  
  
 Implementowane za pomocą [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727).  
  
##  <a name="free"></a>  CComHeap::Free  
 Wywołanie tej metody, aby zwolnić blok pamięci przydzielonej przez ten Menedżer pamięci.  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Wskaźnik do pamięci przydzielonej wcześniej przez tego menedżera pamięci. Wartość NULL jest nieprawidłowa i nie działają.  
  
### <a name="remarks"></a>Uwagi  
 Implementowane za pomocą [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722).  
  
##  <a name="getsize"></a>  CComHeap::GetSize  
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
 Implementowane za pomocą [IMalloc::GetSize](http://msdn.microsoft.com/library/windows/desktop/ms691226).  
  
##  <a name="reallocate"></a>  CComHeap::Reallocate  
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
 Wywołanie [CComHeap::Free](#free) zwolnienia pamięci przydzielonej przez tę metodę.  
  
 Implementowane za pomocą [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe DynamicConsumer](../../visual-cpp-samples.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Klasa CWin32Heap](../../atl/reference/cwin32heap-class.md)   
 [Klasa CLocalHeap](../../atl/reference/clocalheap-class.md)   
 [Klasa CGlobalHeap](../../atl/reference/cglobalheap-class.md)   
 [Klasa CCRTHeap](../../atl/reference/ccrtheap-class.md)   
 [Klasa IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
