---
title: Klasa CGlobalHeap | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CGlobalHeap
- ATLMEM/ATL::CGlobalHeap
- ATLMEM/ATL::CGlobalHeap::Allocate
- ATLMEM/ATL::CGlobalHeap::Free
- ATLMEM/ATL::CGlobalHeap::GetSize
- ATLMEM/ATL::CGlobalHeap::Reallocate
dev_langs: C++
helpviewer_keywords: CGlobalHeap class
ms.assetid: e348d838-3aa7-4bee-a1b3-cd000c99f834
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 693a0ce139c35b804325e9ef5dcb7beb1e4da6a1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cglobalheap-class"></a>Klasa CGlobalHeap
Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji globalnych sterty Win32.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CGlobalHeap : public IAtlMemMgr
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CGlobalHeap::Allocate](#allocate)|Wywołanie tej metody można przydzielić bloku pamięci.|  
|[CGlobalHeap::Free](#free)|Wywołanie tej metody, aby zwolnić blok pamięci przydzielonej przez ten Menedżer pamięci.|  
|[CGlobalHeap::GetSize](#getsize)|Wywołaj tę metodę, aby pobrać przydzielony rozmiar bloku pamięci przydzielonej przez ten Menedżer pamięci.|  
|[CGlobalHeap::Reallocate](#reallocate)|Wywołaj tę metodę, aby ponownie przydzielić pamięci przydzielonej przez ten Menedżer pamięci.|  
  
## <a name="remarks"></a>Uwagi  
 `CGlobalHeap`implementuje funkcje alokacji pamięci przy użyciu funkcji globalnych sterty Win32.  
  
> [!NOTE]
>  Funkcje globalne stosu wolniej niż inne funkcje zarządzania pamięcią i nie zapewnia tylu funkcji. W związku z tym nowe aplikacje powinny używać [stercie funkcji](http://msdn.microsoft.com/library/windows/desktop/aa366711). Są one dostępne w [CWin32Heap](../../atl/reference/cwin32heap-class.md) klasy. Globalne funkcje są nadal używane przez DDE i funkcji Schowka.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IAtlMemMgr`  
  
 `CGlobalHeap`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlmem.h  
  
##  <a name="allocate"></a>CGlobalHeap::Allocate  
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
 Wywołanie [CGlobalHeap::Free](#free) lub [CGlobalHeap::Reallocate](#reallocate) zwolnienia pamięci przydzielonej przez tę metodę.  
  
 Implementowane za pomocą [działanie funkcji GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) z parametrem flagi **GMEM_FIXED**.  
  
##  <a name="free"></a>CGlobalHeap::Free  
 Wywołanie tej metody, aby zwolnić blok pamięci przydzielonej przez ten Menedżer pamięci.  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Wskaźnik do pamięci przydzielonej wcześniej przez tego menedżera pamięci. Wartość NULL jest nieprawidłowa i nie działają.  
  
### <a name="remarks"></a>Uwagi  
 Implementowane za pomocą [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579).  
  
##  <a name="getsize"></a>CGlobalHeap::GetSize  
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
 Implementowane za pomocą [Funkcja GlobalSize](http://msdn.microsoft.com/library/windows/desktop/aa366593).  
  
##  <a name="reallocate"></a>CGlobalHeap::Reallocate  
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
 Wywołanie [CGlobalHeap::Free](#free) zwolnienia pamięci przydzielonej przez tę metodę.  
  
 Implementowane za pomocą [GlobalReAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366590).  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Klasa CComHeap](../../atl/reference/ccomheap-class.md)   
 [Klasa CWin32Heap](../../atl/reference/cwin32heap-class.md)   
 [Klasa CLocalHeap](../../atl/reference/clocalheap-class.md)   
 [Klasa CCRTHeap](../../atl/reference/ccrtheap-class.md)   
 [Klasa IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
