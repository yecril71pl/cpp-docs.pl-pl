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
ms.openlocfilehash: d45a999f777a2d497542544c2d3c7f079b7a32b0
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881607"
---
# <a name="ccomheap-class"></a>Klasa CComHeap
Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji alokacji pamięci COM.  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CComHeap : public IAtlMemMgr
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComHeap::Allocate](#allocate)|Wywołaj tę metodę można przydzielić bloku pamięci.|  
|[CComHeap::Free](#free)|Wywołaj tę metodę w celu zwolnienia bloku pamięci przydzielonej przez tego menedżera pamięci.|  
|[CComHeap::GetSize](#getsize)|Wywołaj tę metodę, aby uzyskać przydzielony rozmiar bloku pamięci przydzielonej przez tego menedżera pamięci.|  
|[CComHeap::Reallocate](#reallocate)|Wywołaj tę metodę w celu ponownego przydzielenia pamięci przydzielonej przez tego menedżera pamięci.|  
  
## <a name="remarks"></a>Uwagi  
 `CComHeap` implementuje funkcje alokacji pamięci za pomocą funkcji alokacji COM, w tym [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727), [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722), [IMalloc::GetSize](http://msdn.microsoft.com/library/windows/desktop/ms691226)i [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280). Maksymalna ilość pamięci, która może być przydzielona jest równa bajtów INT_MAX (2147483647).  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IAtlMemMgr`  
  
 `CComHeap`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ATLComMem.h  
  
##  <a name="allocate"></a>  CComHeap::Allocate  
 Wywołaj tę metodę można przydzielić bloku pamięci.  
  
```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *nBytes*  
 Żądana liczba bajtów w nowy blok pamięci.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do początku bloku nowo alokacji pamięci.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj [CComHeap::Free](#free) lub [CComHeap::Reallocate](#reallocate) zwolnienie pamięci przydzielonej przez tę metodę.  
  
 Implementowany przy użyciu [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727).  
  
##  <a name="free"></a>  CComHeap::Free  
 Wywołaj tę metodę w celu zwolnienia bloku pamięci przydzielonej przez tego menedżera pamięci.  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *p*  
 Wskaźnik do pamięci uprzednio przydzielonej przez tego menedżera pamięci. Wartość NULL jest prawidłową wartością i nic nie robi.  
  
### <a name="remarks"></a>Uwagi  
 Implementowany przy użyciu [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722).  
  
##  <a name="getsize"></a>  CComHeap::GetSize  
 Wywołaj tę metodę, aby uzyskać przydzielony rozmiar bloku pamięci przydzielonej przez tego menedżera pamięci.  
  
```
virtual size_t GetSize(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *p*  
 Wskaźnik do pamięci uprzednio przydzielonej przez tego menedżera pamięci.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca rozmiar bloku ilość przydzielonej pamięci w bajtach.  
  
### <a name="remarks"></a>Uwagi  
 Implementowany przy użyciu [IMalloc::GetSize](http://msdn.microsoft.com/library/windows/desktop/ms691226).  
  
##  <a name="reallocate"></a>  CComHeap::Reallocate  
 Wywołaj tę metodę w celu ponownego przydzielenia pamięci przydzielonej przez tego menedżera pamięci.  
  
```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *p*  
 Wskaźnik do pamięci uprzednio przydzielonej przez tego menedżera pamięci.  
  
 *nBytes*  
 Żądana liczba bajtów w nowy blok pamięci.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do początku bloku nowo alokacji pamięci.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj [CComHeap::Free](#free) zwolnienie pamięci przydzielonej przez tę metodę.  
  
 Implementowany przy użyciu [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe DynamicConsumer](../../visual-cpp-samples.md)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)   
 [Klasa CWin32Heap](../../atl/reference/cwin32heap-class.md)   
 [Klasa CLocalHeap](../../atl/reference/clocalheap-class.md)   
 [Klasa CGlobalHeap](../../atl/reference/cglobalheap-class.md)   
 [Klasa CCRTHeap](../../atl/reference/ccrtheap-class.md)   
 [Klasa IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
