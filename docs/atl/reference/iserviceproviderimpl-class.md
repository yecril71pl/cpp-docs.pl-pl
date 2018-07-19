---
title: Klasa IServiceProviderImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl::QueryService
dev_langs:
- C++
helpviewer_keywords:
- IServiceProviderImpl class
- IServiceProvider interface, ATL implementation
ms.assetid: 251254d3-c4ce-40d7-aee0-3d676d1d72f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2e298f8398041b7b83a581b95f95c4ff9521cd4b
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883609"
---
# <a name="iserviceproviderimpl-class"></a>Klasa IServiceProviderImpl
Ta klasa udostępnia domyślną implementację elementu `IServiceProvider` interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>  
class ATL_NO_VTABLE IServiceProviderImpl : public IServiceProvider
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Z klasą pochodną `IServiceProviderImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IServiceProviderImpl::QueryService](#queryservice)|Tworzy lub uzyskuje dostęp do określonej usługi i zwraca wskaźnik interfejsu do określonego interfejsu usługi.|  
  
## <a name="remarks"></a>Uwagi  
 `IServiceProvider` Interfejsu lokalizuje określony przez jego identyfikator GUID usługi i zwraca wskaźnik interfejsu dla żądanego interfejsu usługi. Klasa `IServiceProviderImpl` udostępnia domyślną implementację tego interfejsu.  
  
 `IServiceProviderImpl` Określa jedną z metod: [QueryService](#queryservice), który tworzy i uzyskuje dostęp do określonej usługi i zwraca wskaźnik interfejsu do określonego interfejsu usługi.  
  
 `IServiceProviderImpl` rozwiązania service map, począwszy od [BEGIN_SERVICE_MAP](service-map-macros.md#begin_service_map) i kończąc [END_SERVICE_MAP](service-map-macros.md#end_service_map).  
  
 Mapa usługi zawiera dwie pozycje: [SERVICE_ENTRY](service-map-macros.md#service_entry), który wskazuje identyfikator określonej usługi (SID), obsługiwane przez obiekt, i [SERVICE_ENTRY_CHAIN](service-map-macros.md#service_entry_chain), która wywołuje metodę `QueryService` do tworzenia łańcucha na inny obiekt.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IServiceProvider`  
  
 `IServiceProviderImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="queryservice"></a>  IServiceProviderImpl::QueryService  
 Tworzy lub uzyskuje dostęp do określonej usługi i zwraca wskaźnik interfejsu do określonego interfejsu usługi.  
  
```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 [IN] *guidService*  
 Wskaźnik do identyfikator usług (SID).  
  
 [IN] *riid*  
 Identyfikator interfejsu, do którego ma dostęp obiekt wywołujący.  
  
 [OUT] *ppvObj*  
 Pośredni wskaźnik do żądanego interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwrócona wartość HRESULT jest jedną z następujących czynności:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|S_OK|Usługa została pomyślnie utworzone lub pobrać.|  
|E_INVALIDARG|Co najmniej jeden z argumentów jest nieprawidłowa.|  
|E_OUTOFMEMORY|Pamięć jest za mała, aby utworzyć usługę.|  
|WARTOŚĆ E_UNEXPECTED|Wystąpił nieznany błąd.|  
|E_NOINTERFACE|Żądany interfejs nie jest częścią tej usługi lub usługa jest nieznany.|  
  
### <a name="remarks"></a>Uwagi  
 `QueryService` Zwraca wartość pośredni wskaźnik do żądanego interfejsu w określonej usługi. Obiekt wywołujący jest odpowiedzialny za zwalniając tego wskaźnika, gdy nie jest już wymagany.  
  
 Gdy wywołujesz `QueryService`, należy przekazać identyfikatorem usługi (*guidService*) i identyfikator interfejsu (*riid*). *GuidService* Określa usługę, do którego mają dostęp, i *riid* identyfikuje interfejs, który jest częścią usługi. W zamian otrzymasz pośredni wskaźnik do interfejsu.  
  
 Obiekt, który implementuje interfejs może także implementować interfejsy, które należą do innych usług. Rozważ następujące opcje:  
  
-   Niektóre z tych interfejsów, może być opcjonalny. Nie wszystkie interfejsy, zdefiniowane w opisie usługi są zawsze obecne w każdej implementacji usługi lub dla każdego zwróconego obiektu.  
  
-   W przeciwieństwie do wywołania `QueryInterface`, przekazując identyfikator innej usługi nie musi oznaczać zwróceniem innego obiektu Component Object Model (COM).  
  
-   Zwrócony obiekt może mieć dodatkowe interfejsy, które nie są częścią definicji usługi.  
  
 Dwa różne usługi, takie jak SID_SMyService i SID_SYourService, zarówno określić korzystanie z tego samego interfejsu, mimo że implementacja interfejsu może być nic wspólnego między obiema usługami. To działa, ponieważ wywołanie `QueryService` (SID_SMyService, IID_IDispatch) może zwrócić obiekt inny niż `QueryService` (SID_SYourService, IID_IDispatch). Tożsamość obiektu nie zakłada, że podczas określania identyfikatora innej usługi.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
