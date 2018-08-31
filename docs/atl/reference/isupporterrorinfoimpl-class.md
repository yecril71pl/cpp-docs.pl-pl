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
ms.openlocfilehash: fa9ee25403464a13418081abc8e8e150c7e03500
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43217462"
---
# <a name="isupporterrorinfoimpl-class"></a>Klasa ISupportErrorInfoImpl
Ta klasa udostępnia domyślną implementację elementu [interfejsu Interfejs ISupportErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo) i mogą być używane, gdy tylko jeden interfejs generuje błędy na obiekcie.  
  
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
 Wskaźnik do identyfikatora IID interfejsu, który obsługuje [IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo).  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|Wskazuje, czy interfejsie zidentyfikowany przez `riid` obsługuje [IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) interfejsu.|  
  
## <a name="remarks"></a>Uwagi  
 [Interfejsu Interfejs ISupportErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo) gwarantuje, że informacje o błędzie mogą być zwrócone do klienta. Obiekty używające `IErrorInfo` musi implementować `ISupportErrorInfo`.  
  
 Klasa `ISupportErrorInfoImpl` udostępnia domyślną implementację elementu `ISupportErrorInfo` i mogą być używane, gdy tylko jeden interfejs generuje błędy na obiekcie. Na przykład:  
  
 [!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ISupportErrorInfo`  
  
 `ISupportErrorInfoImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="interfacesupportserrorinfo"></a>  ISupportErrorInfoImpl::InterfaceSupportsErrorInfo  
 Wskazuje, czy interfejsie zidentyfikowany przez `riid` obsługuje [IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) interfejsu.  
  
```
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [ISupportErrorInfo::InterfaceSupportsErrorInfo](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) w Windows SDK.  
  
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
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
