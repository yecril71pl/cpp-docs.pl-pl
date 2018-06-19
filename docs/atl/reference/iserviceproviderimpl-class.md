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
ms.openlocfilehash: 1b1472fe5d952e93b45240128383db9fdec5b093
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363677"
---
# <a name="iserviceproviderimpl-class"></a>Klasa IServiceProviderImpl
Ta klasa udostępnia domyślną implementację `IServiceProvider` interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>  
class ATL_NO_VTABLE IServiceProviderImpl : public IServiceProvider
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IServiceProviderImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IServiceProviderImpl::QueryService](#queryservice)|Tworzy lub uzyskuje dostęp do określonej usługi i zwraca wskaźnika interfejsu do określonego interfejsu usługi.|  
  
## <a name="remarks"></a>Uwagi  
 `IServiceProvider` Interfejsu lokalizuje usługę określony przez jego identyfikator GUID i zwraca wskaźnik interfejsu dla żądanego interfejsu usługi. Klasa `IServiceProviderImpl` udostępnia domyślną implementację tego interfejsu.  
  
 **IServiceProviderImpl** Określa jedną metodę: [QueryService](#queryservice), która tworzy lub uzyskuje dostęp do określonej usługi i zwraca wskaźnika interfejsu do określonego interfejsu usługi.  
  
 `IServiceProviderImpl` używa mapy usługi, zaczynając od [BEGIN_SERVICE_MAP](service-map-macros.md#begin_service_map) i kończąc [END_SERVICE_MAP](service-map-macros.md#end_service_map).  
  
 Mapy usług zawiera dwie pozycje: [SERVICE_ENTRY](service-map-macros.md#service_entry), co oznacza identyfikator określonej usługi (SID), obsługiwane przez obiekt, i [SERVICE_ENTRY_CHAIN](service-map-macros.md#service_entry_chain), które wywołuje `QueryService` łańcucha do innego obiekt.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IServiceProvider`  
  
 `IServiceProviderImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="queryservice"></a>  IServiceProviderImpl::QueryService  
 Tworzy lub uzyskuje dostęp do określonej usługi i zwraca wskaźnika interfejsu do określonego interfejsu usługi.  
  
```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 [IN] `guidService`  
 Wskaźnik do identyfikatora usługi (SID).  
  
 [IN] `riid`  
 Identyfikator interfejsu, do którego ma dostęp obiekt wywołujący.  
  
 [OUT] `ppvObj`  
 Pośredni wskaźnik do żądanego interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwrócona `HRESULT` wartość to jeden z następujących czynności:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|S_OK|Usługa został pomyślnie utworzony lub pobrać.|  
|E_INVALIDARG|Co najmniej jeden z argumentów jest nieprawidłowa.|  
|E_OUTOFMEMORY|Ilość pamięci jest za mała, aby utworzyć usługę.|  
|E_UNEXPECTED|Wystąpił nieznany błąd.|  
|E_NOINTERFACE|Żądany interfejs nie jest częścią tej usługi lub usługa jest nieznany.|  
  
### <a name="remarks"></a>Uwagi  
 `QueryService` Zwraca pośredni wskaźnik do żądanego interfejsu w określonej usługi. Obiekt wywołujący jest odpowiedzialny za zwolnienie ten wskaźnik, gdy nie jest już wymagane.  
  
 Podczas wywoływania `QueryService`, Przekaż identyfikatorem usługi ( `guidService`) i identyfikator interfejsu ( `riid`). `guidService` Określa usługę, do którego ma dostęp, i `riid` identyfikuje interfejs, który jest częścią usługi. W zamian zostanie wyświetlony pośredni wskaźnik do interfejsu.  
  
 Obiekt, który implementuje interfejs może także implementować interfejsów, które należą do innych usług. Rozważ następujące opcje:  
  
-   Niektóre z tych interfejsów mogą być opcjonalne. Nie są musi występować w każdej implementacji usługi lub dla każdego zwróconego obiektu nie wszystkie interfejsy zdefiniowana w opisie usługi.  
  
-   W przeciwieństwie do wywołania `QueryInterface`, przekazywanie identyfikator innej usługi nie musi oznaczać, że inny obiekt składnika modelu COM (Object) jest zwracany.  
  
-   Zwrócony obiekt może mieć dodatkowe interfejsy, które nie są częścią definicji usługi.  
  
 Dwóch różnych usług, takich jak SID_SMyService i SID_SYourService, można jednocześnie określić korzystanie z tego samego interfejsu mimo, że implementacja interfejsu może mają one nic wspólnego między dwie usługi. Dzieje się tak, ponieważ wywołanie `QueryService` (SID_SMyService, IID_IDispatch) może zwracać obiektu innego niż `QueryService` (SID_SYourService, IID_IDispatch). Tożsamość obiektu nie zakłada, że po określeniu identyfikatora innej usługi.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
