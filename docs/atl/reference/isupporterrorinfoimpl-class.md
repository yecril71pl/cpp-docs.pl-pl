---
title: Klasa ISupportErrorInfoImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl::InterfaceSupportsErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- ISupportErrorInfo ATL implementation
- ISupportErrorInfoImpl class
- error information, ATL
ms.assetid: e33a4b11-a123-41cf-bcea-7b19743902af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 849107cc9f0d0611eb3dc9259fc317f73a961407
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/13/2018
ms.locfileid: "39026176"
---
# <a name="isupporterrorinfoimpl-class"></a>Klasa ISupportErrorInfoImpl
Ta klasa udostępnia domyślną implementację elementu [interfejsu Interfejs ISupportErrorInfo](http://msdn.microsoft.com/42d33066-36b4-4a5b-aa5d-46682e560f32) i mogą być używane, gdy tylko jeden interfejs generuje błędy na obiekcie.  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<const IID* piid>  
class ATL_NO_VTABLE ISupportErrorInfoImpl 
   : public ISupportErrorInfo
```  
  
#### <a name="parameters"></a>Parametry  
 *piid*  
 Wskaźnik do identyfikatora IID interfejsu, który obsługuje [IErrorInfo](http://msdn.microsoft.com/4dda6909-2d9a-4727-ae0c-b5f90dcfa447).  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|Wskazuje, czy interfejsie zidentyfikowany przez `riid` obsługuje [IErrorInfo](http://msdn.microsoft.com/4dda6909-2d9a-4727-ae0c-b5f90dcfa447) interfejsu.|  
  
## <a name="remarks"></a>Uwagi  
 [Interfejsu Interfejs ISupportErrorInfo](http://msdn.microsoft.com/42d33066-36b4-4a5b-aa5d-46682e560f32) gwarantuje, że informacje o błędzie mogą być zwrócone do klienta. Obiekty używające `IErrorInfo` musi implementować `ISupportErrorInfo`.  
  
 Klasa `ISupportErrorInfoImpl` udostępnia domyślną implementację elementu `ISupportErrorInfo` i mogą być używane, gdy tylko jeden interfejs generuje błędy na obiekcie. Na przykład:  
  
 [!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ISupportErrorInfo`  
  
 `ISupportErrorInfoImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="interfacesupportserrorinfo"></a>  ISupportErrorInfoImpl::InterfaceSupportsErrorInfo  
 Wskazuje, czy interfejsie zidentyfikowany przez `riid` obsługuje [IErrorInfo](http://msdn.microsoft.com/4dda6909-2d9a-4727-ae0c-b5f90dcfa447) interfejsu.  
  
```
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [ISupportErrorInfo::InterfaceSupportsErrorInfo](http://msdn.microsoft.com/a54ef18d-ee3f-4483-ac4a-99d758f0960a) w Windows SDK.  
  
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
 [!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_2.cpp)]  
  
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
  
 Jeśli *nNumThreads* wynosi zero, [ATLS_DEFAULT_THREADSPERPROC](http://msdn.microsoft.com/library/e0dcf107-72a9-4122-abb4-83c63aa7d571) zostanie pomnożona przez liczbę procesorów w komputerze, aby uzyskać łączna liczba wątków.  
  
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
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
