---
title: Klasa Win32ThreadTraits | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits::CreateThread
dev_langs:
- C++
helpviewer_keywords:
- threading [ATL], Windows threads
- threading [ATL], creation functions
- Win32ThreadTraits class
ms.assetid: 50279c38-eae1-4301-9ea6-97ccea580f3e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bf4fd3ffaf2fc4a035fdecf679ab507ebb557f38
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="win32threadtraits-class"></a>Klasa Win32ThreadTraits
Ta klasa udostępnia funkcję tworzenia dla wątku systemu Windows. Użyj tej klasy, jeśli wątek nie będzie używać funkcji CRT.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class Win32ThreadTraits
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Win32ThreadTraits::CreateThread](#createthread)|(Statyczny) Wywołanie tej funkcji można utworzyć wątku, który nie należy używać funkcji CRT.|  
  
## <a name="remarks"></a>Uwagi  
 Wątek cechy są klasy, które zapewniają funkcję tworzenia dla określonego typu wątku. Funkcja tworzenia ma taką samą sygnaturę i semantyki jako systemu Windows [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) funkcji.  
  
 Wątek cechy są używane przez następujące klasy:  
  
- [CThreadPool](../../atl/reference/cthreadpool-class.md)  
  
- [CWorkerThread](../../atl/reference/cworkerthread-class.md)  
  
 Jeśli wątek będziesz używać funkcji CRT, użyj [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) zamiast tego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="createthread"></a>Win32ThreadTraits::CreateThread  
 Wywołanie tej funkcji można utworzyć wątku, który nie należy używać funkcji CRT.  
  
```
static HANDLE CreateThread(
    LPSECURITY_ATTRIBUTES lpsa,
    DWORD dwStackSize,
    LPTHREAD_START_ROUTINE pfnThreadProc,
    void* pvParam,
    DWORD dwCreationFlags,
    DWORD* pdwThreadId) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpsa`  
 Atrybuty zabezpieczeń dla nowego wątku.  
  
 `dwStackSize`  
 Rozmiar stosu dla nowego wątku.  
  
 `pfnThreadProc`  
 Procedury wątku nowego wątku.  
  
 `pvParam`  
 Parametr do przekazania do procedury wątku.  
  
 `dwCreationFlags`  
 Tworzenie flagi (0 lub CREATE_SUSPENDED).  
  
 `pdwThreadId`  
 [out] Adres zmiennej DWORD odbierająca, w przypadku powodzenia, identyfikator wątku nowo utworzony wątku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca dojście do nowo utworzonej wątku lub wartość NULL w przypadku awarii. Wywołanie [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) do pobrania rozszerzone informacje o błędzie.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) Aby uzyskać więcej informacji o parametrach tej funkcji.  
  
 Ta funkcja wymaga `CreateThread` można utworzyć wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
