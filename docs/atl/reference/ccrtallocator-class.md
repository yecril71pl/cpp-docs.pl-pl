---
title: Klasa CCRTAllocator | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCRTAllocator
- ATLCORE/ATL::CCRTAllocator
- ATLCORE/ATL::CCRTAllocator::Allocate
- ATLCORE/ATL::CCRTAllocator::Free
- ATLCORE/ATL::CCRTAllocator::Reallocate
dev_langs: C++
helpviewer_keywords: CCRTAllocator class
ms.assetid: 3e1b8cb0-859a-41ab-8e93-6f0b5ceca49d
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 35d71154ccbfc5f2d3147c55aaedff8cf85a06de
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccrtallocator-class"></a>Klasa CCRTAllocator
Ta klasa dostarcza metody do zarządzania przy użyciu procedury pamięci CRT pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```
class ATL::CCRTAllocator
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCRTAllocator::Allocate](#allocate)|(Statyczny) Wywołanie tej metody można przydzielić pamięci.|  
|[CCRTAllocator::Free](#free)|(Statyczny) Wywołaj tę metodę, aby zwolnić pamięć.|  
|[CCRTAllocator::Reallocate](#reallocate)|(Statyczny) Wywołaj tę metodę, aby ponownie przydzielić pamięci.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa jest używana przez [CHeapPtr](../../atl/reference/cheapptr-class.md) do dostarczenia pamięci CRT procedury alokacji. Klasa odpowiednikiem [CComAllocator](../../atl/reference/ccomallocator-class.md), zapewnia te same metody, przy użyciu procedury COM.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcore.h  
  
##  <a name="allocate"></a>CCRTAllocator::Allocate  
 Wywołanie tej statycznych funkcji można przydzielić pamięci.  
  
```
static __declspec(allocator) void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBytes`  
 Liczba bajtów do przydzielenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca typ void wskaźnik do przydzielone miejsce, lub wartość NULL, jeśli dostępnych jest za mało pamięci.  
  
### <a name="remarks"></a>Uwagi  
 Przydziela pamięć. Zobacz [— funkcja malloc](../../c-runtime-library/reference/malloc.md) więcej szczegółów.  
  
##  <a name="free"></a>CCRTAllocator::Free  
 Wywołanie tej funkcji statycznych, aby zwolnić pamięć.  
  
```
static void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Wskaźnik do alokacji pamięci.  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia alokacji pamięci. Zobacz [wolnego](../../c-runtime-library/reference/free.md) więcej szczegółów.  
  
##  <a name="reallocate"></a>CCRTAllocator::Reallocate  
 Wywołanie tej funkcji statycznych ponownie przydzielić pamięci.  
  
```
static __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Wskaźnik do alokacji pamięci.  
  
 `nBytes`  
 Liczba bajtów ponownie przydzielić.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik void przydzielone miejsce, lub wartość NULL, jeśli jest za mało pamięci.  
  
### <a name="remarks"></a>Uwagi  
 Zmienia rozmiar ilość alokacji pamięci. Zobacz [realloc](../../c-runtime-library/reference/realloc.md) więcej szczegółów.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CHeapPtr](../../atl/reference/cheapptr-class.md)   
 [Klasa CComAllocator](../../atl/reference/ccomallocator-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
