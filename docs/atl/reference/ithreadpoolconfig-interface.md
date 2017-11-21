---
title: Interfejs IThreadPoolConfig | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IThreadPoolConfig
- ATLUTIL/ATL::IThreadPoolConfig
- ATLUTIL/ATL::GetSize
- ATLUTIL/ATL::GetTimeout
- ATLUTIL/ATL::SetSize
- ATLUTIL/ATL::SetTimeout
dev_langs: C++
helpviewer_keywords: IThreadPoolConfig interface
ms.assetid: 69e642bf-6925-46e6-9a37-cce52231b1cc
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9ae9aea7c6517e2369901ea7e435627eff180c69
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ithreadpoolconfig-interface"></a>Interfejs IThreadPoolConfig
Ten interfejs umożliwia stosowanie metod konfigurowania puli wątków.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
__interface
    __declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660")) IThreadPoolConfig : public IUnknown
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[GetSize](#getsize)|Wywołaj tę metodę, aby pobrać liczbę wątków w puli.|  
|[GetTimeout](#gettimeout)|Wywołanie tej metody, aby uzyskać maksymalny czas (w milisekundach) oczekiwania na wątek zamknięcia puli wątków.|  
|[SetSize](#setsize)|Wywołanie tej metody, aby ustawić liczbę wątków w puli.|  
|[SetTimeout](#settimeout)|Wywołaj tę metodę, aby ustawić maksymalny czas (w milisekundach) oczekiwania na wątek zamknięcia puli wątków.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest implementowany przez [CThreadPool](../../atl/reference/cthreadpool-class.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlutil.h  
  
##  <a name="getsize"></a>IThreadPoolConfig::GetSize  
 Wywołaj tę metodę, aby pobrać liczbę wątków w puli.  
  
```
STDMETHOD(GetSize)(int* pnNumThreads);
```  
  
### <a name="parameters"></a>Parametry  
 `pnNumThreads`  
 [out] Adres zmiennej, która w przypadku powodzenia otrzymuje to liczba wątków w puli.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]  
  
##  <a name="gettimeout"></a>IThreadPoolConfig::GetTimeout  
 Wywołanie tej metody, aby uzyskać maksymalny czas (w milisekundach) oczekiwania na wątek zamknięcia puli wątków.  
  
```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```  
  
### <a name="parameters"></a>Parametry  
 `pdwMaxWait`  
 [out] Adres zmiennej, która w przypadku powodzenia otrzymuje maksymalny czas (w milisekundach) oczekiwania na wątek zamknięcia puli wątków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="example"></a>Przykład  
 Zobacz [IThreadPoolConfig::GetSize](#getsize).  
  
##  <a name="setsize"></a>IThreadPoolConfig::SetSize  
 Wywołanie tej metody, aby ustawić liczbę wątków w puli.  
  
```
STDMETHOD(SetSize)int nNumThreads);
```  
  
### <a name="parameters"></a>Parametry  
 `nNumThreads`  
 Żądana liczba wątków w puli.  
  
 Jeśli `nNumThreads` jest ujemna, jego wartość bezwzględna zostanie pomnożona przez liczbę procesorów na maszynie, aby uzyskać łączna liczba wątków.  
  
 Jeśli `nNumThreads` wynosi zero, [ATLS_DEFAULT_THREADSPERPROC](http://msdn.microsoft.com/library/e0dcf107-72a9-4122-abb4-83c63aa7d571) zostanie pomnożona przez liczbę procesorów na maszynie, aby uzyskać łączna liczba wątków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="example"></a>Przykład  
 Zobacz [IThreadPoolConfig::GetSize](#getsize).  
  
##  <a name="settimeout"></a>IThreadPoolConfig::SetTimeout  
 Wywołaj tę metodę, aby ustawić maksymalny czas (w milisekundach) oczekiwania na wątek zamknięcia puli wątków.  
  
```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```  
  
### <a name="parameters"></a>Parametry  
 `dwMaxWait`  
 Żądana maksymalny czas (w milisekundach) oczekiwania na wątek zamknięcia puli wątków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="example"></a>Przykład  
 Zobacz [IThreadPoolConfig::GetSize](#getsize).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../atl/reference/atl-classes.md)   
 [Klasa CThreadPool](../../atl/reference/cthreadpool-class.md)
