---
title: Klasa ISupportErrorInfoImpl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl::InterfaceSupportsErrorInfo
dev_langs: C++
helpviewer_keywords:
- ISupportErrorInfo ATL implementation
- ISupportErrorInfoImpl class
- error information, ATL
ms.assetid: e33a4b11-a123-41cf-bcea-7b19743902af
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d57302ecd7f0e116e79e3c1fbcd263f5ff500a0c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="isupporterrorinfoimpl-class"></a>Klasa ISupportErrorInfoImpl
Ta klasa udostępnia domyślną implementację [interfejsu ISupportErrorInfo](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32) i mogą być używane, gdy tylko jeden interfejs generuje błędy w obiekcie.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<const IID* piid>  
class ATL_NO_VTABLE ISupportErrorInfoImpl 
   : public ISupportErrorInfo
```  
  
#### <a name="parameters"></a>Parametry  
 `piid`  
 Wskaźnik do identyfikatora IID interfejsu, który obsługuje [IErrorInfo](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447).  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|Wskazuje, czy interfejs identyfikowane przez `riid` obsługuje [IErrorInfo](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447) interfejsu.|  
  
## <a name="remarks"></a>Uwagi  
 [Interfejsu ISupportErrorInfo](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32) gwarantuje, że informacje o błędzie może być zwracany do klienta. Obiekty używające **IErrorInfo** musi implementować **ISupportErrorInfo**.  
  
 Klasa `ISupportErrorInfoImpl` udostępnia domyślną implementację elementu **ISupportErrorInfo** i mogą być używane, gdy tylko jeden interfejs generuje błędy w obiekcie. Na przykład:  
  
 [!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ISupportErrorInfo`  
  
 `ISupportErrorInfoImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="interfacesupportserrorinfo"></a>ISupportErrorInfoImpl::InterfaceSupportsErrorInfo  
 Wskazuje, czy interfejs identyfikowane przez `riid` obsługuje [IErrorInfo](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447) interfejsu.  
  
```
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [ISupportErrorInfo::InterfaceSupportsErrorInfo](http://msdn.microsoft.com/en-us/a54ef18d-ee3f-4483-ac4a-99d758f0960a) w systemie Windows SDK.  
  
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
 [!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_2.cpp)]  
  
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
 [Przegląd klas](../../atl/atl-class-overview.md)
