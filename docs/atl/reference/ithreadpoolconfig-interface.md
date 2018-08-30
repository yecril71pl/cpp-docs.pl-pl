---
title: Interfejs IThreadPoolConfig | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IThreadPoolConfig
- ATLUTIL/ATL::IThreadPoolConfig
- ATLUTIL/ATL::GetSize
- ATLUTIL/ATL::GetTimeout
- ATLUTIL/ATL::SetSize
- ATLUTIL/ATL::SetTimeout
dev_langs:
- C++
helpviewer_keywords:
- IThreadPoolConfig interface
ms.assetid: 69e642bf-6925-46e6-9a37-cce52231b1cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b144e08e0f87165c284310afc86267f67b1c124
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222057"
---
# <a name="ithreadpoolconfig-interface"></a>Interfejs IThreadPoolConfig
Ten interfejs zapewnia metody konfigurowania puli wątków.  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
__interface
    __declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660")) IThreadPoolConfig : public IUnknown
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[GetSize](#getsize)|Wywołaj tę metodę, aby uzyskać liczbę wątków w puli.|  
|[GetTimeout](#gettimeout)|Wywołaj tę metodę, aby uzyskać maksymalny czas (w milisekundach) oczekiwania na wątek zamknąć puli wątków.|  
|[SetSize](#setsize)|Wywołaj tę metodę, aby ustawić liczbę wątków w puli.|  
|[SetTimeout —](#settimeout)|Wywołaj tę metodę, aby ustawić maksymalny czas (w milisekundach) oczekiwania na wątek zamknąć puli wątków.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest implementowany przez [CThreadPool](../../atl/reference/cthreadpool-class.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlutil.h  
  
##  <a name="getsize"></a>  IThreadPoolConfig::GetSize  
 Wywołaj tę metodę, aby uzyskać liczbę wątków w puli.  
  
```
STDMETHOD(GetSize)(int* pnNumThreads);
```  
  
### <a name="parameters"></a>Parametry  
 *pnNumThreads*  
 [out] Adres zmiennej, która w przypadku powodzenia, otrzyma liczbę wątków w puli.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]  
  
##  <a name="gettimeout"></a>  IThreadPoolConfig::GetTimeout  
 Wywołaj tę metodę, aby uzyskać maksymalny czas (w milisekundach) oczekiwania na wątek zamknąć puli wątków.  
  
```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```  
  
### <a name="parameters"></a>Parametry  
 *pdwMaxWait*  
 [out] Adres zmiennej, która w przypadku powodzenia odbiera maksymalny czas (w milisekundach) oczekiwania na wątek zamknąć puli wątków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="example"></a>Przykład  
 Zobacz [IThreadPoolConfig::GetSize](#getsize).  
  
##  <a name="setsize"></a>  IThreadPoolConfig::SetSize  
 Wywołaj tę metodę, aby ustawić liczbę wątków w puli.  
  
```
STDMETHOD(SetSize)int nNumThreads);
```  
  
### <a name="parameters"></a>Parametry  
 *nNumThreads*  
 Żądana liczba wątków w puli.  
  
 Jeśli *nNumThreads* jest ujemna, jego wartość bezwzględna będzie pomnożona przez liczbę procesorów w komputerze, aby uzyskać łączna liczba wątków.  
  
 Jeśli *nNumThreads* wynosi zero, [ATLS_DEFAULT_THREADSPERPROC](https://msdn.microsoft.com/library/e0dcf107-72a9-4122-abb4-83c63aa7d571) zostanie pomnożona przez liczbę procesorów w komputerze, aby uzyskać łączna liczba wątków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="example"></a>Przykład  
 Zobacz [IThreadPoolConfig::GetSize](#getsize).  
  
##  <a name="settimeout"></a>  IThreadPoolConfig::SetTimeout  
 Wywołaj tę metodę, aby ustawić maksymalny czas (w milisekundach) oczekiwania na wątek zamknąć puli wątków.  
  
```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```  
  
### <a name="parameters"></a>Parametry  
 *dwMaxWait*  
 Żądany maksymalny czas (w milisekundach) oczekiwania na wątek zamknąć puli wątków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="example"></a>Przykład  
 Zobacz [IThreadPoolConfig::GetSize](#getsize).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../atl/reference/atl-classes.md)   
 [Klasa CThreadPool](../../atl/reference/cthreadpool-class.md)
