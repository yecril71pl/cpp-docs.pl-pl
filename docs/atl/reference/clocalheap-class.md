---
title: Klasa CLocalHeap | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CLocalHeap
- ATLMEM/ATL::CLocalHeap
- ATLMEM/ATL::CLocalHeap::Allocate
- ATLMEM/ATL::CLocalHeap::Free
- ATLMEM/ATL::CLocalHeap::GetSize
- ATLMEM/ATL::CLocalHeap::Reallocate
dev_langs: C++
helpviewer_keywords: CLocalHeap class
ms.assetid: 1ffa87a5-5fc8-4f8d-8809-58e87e963bd2
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5307e0e6e8925bcbbfa7a03d0140c3a5a08baff9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="clocalheap-class"></a>Klasa CLocalHeap
Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji lokalnego stosu Win32.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CLocalHeap : public IAtlMemMgr
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CLocalHeap::Allocate](#allocate)|Wywołanie tej metody można przydzielić bloku pamięci.|  
|[CLocalHeap::Free](#free)|Wywołanie tej metody, aby zwolnić blok pamięci przydzielonej przez ten Menedżer pamięci.|  
|[CLocalHeap::GetSize](#getsize)|Wywołaj tę metodę, aby pobrać przydzielony rozmiar bloku pamięci przydzielonej przez ten Menedżer pamięci.|  
|[CLocalHeap::Reallocate](#reallocate)|Wywołaj tę metodę, aby ponownie przydzielić pamięci przydzielonej przez ten Menedżer pamięci.|  
  
## <a name="remarks"></a>Uwagi  
 `CLocalHeap`implementuje funkcje alokacji pamięci przy użyciu funkcji lokalnego stosu Win32.  
  
> [!NOTE]
>  Funkcje sterty lokalnego wolniej niż inne funkcje zarządzania pamięcią i nie zapewnia tylu funkcji. W związku z tym nowe aplikacje powinny używać [stercie funkcji](http://msdn.microsoft.com/library/windows/desktop/aa366711). Są one dostępne w [CWin32Heap](../../atl/reference/cwin32heap-class.md) klasy.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IAtlMemMgr`  
  
 `CLocalHeap`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlmem.h  
  
##  <a name="allocate"></a>CLocalHeap::Allocate  
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
 Wywołanie [CLocalHeap::Free](#free) lub [CLocalHeap::Reallocate](#reallocate) zwolnienia pamięci przydzielonej przez tę metodę.  
  
 Implementowane za pomocą [Funkcja LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723) z parametrem flagi **LMEM_FIXED**.  
  
##  <a name="free"></a>CLocalHeap::Free  
 Wywołanie tej metody, aby zwolnić blok pamięci przydzielonej przez ten Menedżer pamięci.  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Wskaźnik do pamięci przydzielonej wcześniej przez tego menedżera pamięci. Wartość NULL jest nieprawidłowa i nie działają.  
  
### <a name="remarks"></a>Uwagi  
 Implementowane za pomocą [LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730).  
  
##  <a name="getsize"></a>CLocalHeap::GetSize  
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
 Implementowane za pomocą [LocalSize](http://msdn.microsoft.com/library/windows/desktop/aa366745).  
  
##  <a name="reallocate"></a>CLocalHeap::Reallocate  
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
 Wywołanie [CLocalHeap::Free](#free) zwolnienia pamięci przydzielonej przez tę metodę.  
  
 Implementowane za pomocą [LocalReAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366742).  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Klasa CComHeap](../../atl/reference/ccomheap-class.md)   
 [Klasa CWin32Heap](../../atl/reference/cwin32heap-class.md)   
 [Klasa CGlobalHeap](../../atl/reference/cglobalheap-class.md)   
 [Klasa CCRTHeap](../../atl/reference/ccrtheap-class.md)   
 [Klasa IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
