---
title: "Funkcje globalne punkt połączenia z | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlAdvise
- atlbase/ATL::AtlUnadvise
- atlbase/ATL::AtlAdviseSinkMap
dev_langs: C++
helpviewer_keywords: connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ce7f6fc3d2a0b51f88952dd720955367b1dfe9d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="connection-point-global-functions"></a>Globalne funkcje punktu połączenia
Funkcje te zapewniają obsługę punkty połączenia i sink mapy.  
  
> [!IMPORTANT]
>  Funkcje wymienione w poniższej tabeli nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
|||  
|-|-|  
|[AtlAdvise](#atladvise)|Tworzy połączenie między punktem połączenia obiektu a zbiornikiem klienta.|  
|[AtlUnadvise](#atlunadvise)|Przerywa połączenie nawiązane za pośrednictwem `AtlAdvise`.|  
|[AtlAdviseSinkMap](#atladvisesinkmap)|Zaleceniem lub unadvises wpisów w mapie obiekt sink zdarzenia.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
   
##  <a name="atladvise"></a>AtlAdvise  
 Tworzy połączenie między punktem połączenia obiektu a zbiornikiem klienta.  
  
> [!IMPORTANT]
>  Nie można użyć tej funkcji w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```  
  
### <a name="parameters"></a>Parametry  
 `pUnkCP`  
 [in] Wskaźnik do **IUnknown** obiektu chce nawiązać połączenie z klienta.  
  
 *pUnk*  
 [in] Wskaźnik do klienta **IUnknown**.  
  
 `iid`  
 [in] Identyfikator GUID punktu połączenia. Zazwyczaj jest to ten sam interfejs wychodzących, zarządzane przez punkt połączenia.  
  
 `pdw`  
 [out] Wskaźnik do pliku cookie, który unikatowo identyfikuje połączenie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa wartość HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt sink implementuje interfejs wychodzących obsługiwanych przez punkt połączenia. Klient używa `pdw` pliku cookie do usunięcia tego połączenia, przekazując go do [AtlUnadvise](#atlunadvise).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]  
  
##  <a name="atlunadvise"></a>AtlUnadvise  
 Przerywa połączenie nawiązane za pośrednictwem [AtlAdvise](#atladvise).  
  
> [!IMPORTANT]
>  Nie można użyć tej funkcji w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```  
  
### <a name="parameters"></a>Parametry  
 `pUnkCP`  
 [in] Wskaźnik do **IUnknown** obiektu, który klient jest połączony z.  
  
 `iid`  
 [in] Identyfikator GUID punktu połączenia. Zazwyczaj jest to ten sam interfejs wychodzących, zarządzane przez punkt połączenia.  
  
 `dw`  
 [in] Plik cookie, który unikatowo identyfikuje połączenie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa wartość HRESULT.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]  
  
##  <a name="atladvisesinkmap"></a>AtlAdviseSinkMap  
 Wywołaj tę funkcję, aby przeprowadzić operację advise lub unadvise na wszystkich wpisach w mapie zdarzeń zbiornika obiektu.  
  
> [!IMPORTANT]
>  Nie można użyć tej funkcji w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```  
  
### <a name="parameters"></a>Parametry  
 *pT*  
 [in] Wskaźnik do obiektu zawierającego mapy ujścia.  
  
 `bAdvise`  
 [in] **true** wszystkie wpisy zbiornika mają zaleceniem; **false** wszystkie wpisy zbiornika mają być unadvised.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa wartość HRESULT.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../atl/reference/atl-functions.md)   
 [Makra punktów połączenia](../../atl/reference/connection-point-macros.md)
