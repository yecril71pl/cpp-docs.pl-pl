---
title: Klasa Win32ThreadTraits | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c61ba91fe29610f4b313cf31c65f514ef8e46f96
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883677"
---
# <a name="win32threadtraits-class"></a>Klasa Win32ThreadTraits
Ta klasa udostępnia funkcję tworzenia wątku Windows. Jeśli wątek nie użyje funkcji CRT, należy użyć tej klasy.  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class Win32ThreadTraits
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Win32ThreadTraits::CreateThread](#createthread)|(Statyczny) Wywołaj tę funkcję, aby utworzyć wątek, który nie należy używać funkcji CRT.|  
  
## <a name="remarks"></a>Uwagi  
 Klasy, które zapewniają funkcję tworzenia dla określonego typu wątku z nich są cechami wątku. Funkcja tworzenia ma ten sam podpis i semantyka jako Windows [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) funkcji.  
  
 Cechy wątku są używane przez następujące klasy:  
  
- [CThreadPool](../../atl/reference/cthreadpool-class.md)  
  
- [CWorkerThread](../../atl/reference/cworkerthread-class.md)  
  
 Jeśli wątek będzie używać funkcji CRT, użyj [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) zamiast tego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="createthread"></a>  Win32ThreadTraits::CreateThread  
 Wywołaj tę funkcję, aby utworzyć wątek, który nie należy używać funkcji CRT.  
  
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
 *lpsa*  
 Atrybuty zabezpieczeń dla nowego wątku.  
  
 *dwStackSize*  
 Rozmiar stosu dla nowego wątku.  
  
 *pfnThreadProc*  
 Procedura wątku nowego wątku.  
  
 *pvParam*  
 Parametr, który zostanie przekazany do procedury wątku.  
  
 *dwCreationFlags*  
 Tworzenie flagi (0 lub CREATE_SUSPENDED).  
  
 *pdwThreadId*  
 [out] Adres zmiennej typu DWORD, że w przypadku powodzenia odbiera identyfikator wątku dla nowo utworzonego wątku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca uchwyt do nowo utworzonego wątku lub wartość NULL w przypadku niepowodzenia. Wywołaj [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) Aby uzyskać rozszerzone informacje o błędzie.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) więcej informacji na temat parametrów dotyczących wyłącznie tej funkcji.  
  
 Ta funkcja wywołuje `CreateThread` można utworzyć wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
