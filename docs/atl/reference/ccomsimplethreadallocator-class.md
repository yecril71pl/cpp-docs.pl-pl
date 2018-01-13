---
title: Klasa CComSimpleThreadAllocator | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator::GetThread
dev_langs: C++
helpviewer_keywords:
- threading [ATL], selecting threads
- ATL threads
- CComSimpleThreadAllocator class
- ATL threads, allocating
ms.assetid: 66b2166a-8c50-49fd-b8e4-7f293470327d
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 244443692478d0391c2079e55995c1fef1e1655e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ccomsimplethreadallocator-class"></a>Klasa CComSimpleThreadAllocator
Ta klasa zarządza wyboru wątku dla klasy `CComAutoThreadModule`.  
  
## <a name="syntax"></a>Składnia  
  
```
class CComSimpleThreadAllocator
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComSimpleThreadAllocator::GetThread](#getthread)|Wybiera wątku.|  
  
## <a name="remarks"></a>Uwagi  
 `CComSimpleThreadAllocator`zarządza wyboru wątku do [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md). `CComSimpleThreadAllocator::GetThread`po prostu przełączanie po kolei każdy wątek i zwraca kolejnego w sekwencji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="getthread"></a>CComSimpleThreadAllocator::GetThread  
 Wybiera wątku, określając następnego wątku w sekwencji.  
  
```
int GetThread(CComApartment* /* pApt */, int nThreads);
```  
  
### <a name="parameters"></a>Parametry  
 `pApt`  
 Nie są używane w ATL w domyślnej implementacji.  
  
 `nThreads`  
 Maksymalna liczba wątków w EXE module.  
  
### <a name="return-value"></a>Wartość zwracana  
 Całkowitą z zakresu od zera i ( `nThreads` - 1). Identyfikuje jeden z wątków w EXE module.  
  
### <a name="remarks"></a>Uwagi  
 Można zastąpić `GetThread` Podaj inną metodę wyboru lub dokonanie użycie `pApt` parametru.  
  
 `GetThread`Metoda jest wywoływana przez [CComAutoThreadModule::CreateInstance](../../atl/reference/ccomautothreadmodule-class.md#createinstance).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComApartment](../../atl/reference/ccomapartment-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
