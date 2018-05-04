---
title: Makra mapy usługi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_SERVICE_MAP
- atlcom/ATL::END_SERVICE_MAP
- atlcom/ATL::SERVICE_ENTRY
- atlcom/ATL::SERVICE_ENTRY_CHAIN
dev_langs:
- C++
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d2d2fa313c574951a8f8ba7c85d5b405707ec220
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="service-map-macros"></a>Makra mapy usługi
Te makra zdefiniuj mapy usług i zapisów.  
  
|||  
|-|-|  
|[BEGIN_SERVICE_MAP](#begin_service_map)|Oznacza początek ATL mapy usługi.|  
|[END_SERVICE_MAP](#end_service_map)|Oznacza koniec ATL mapy usługi.|  
|[SERVICE_ENTRY](#service_entry)|Oznacza, że obiekt obsługuje identyfikatora dla określonej usługi.|  
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|Powoduje, że [IServiceProviderImpl::QueryService](#queryservice) do tworzenia łańcucha określony obiekt.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
   
##  <a name="begin_service_map"></a>  BEGIN_SERVICE_MAP  
 Oznacza początek mapy usługi.  
  
```
BEGIN_SERVICE_MAP(theClass)
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 [in] Określa klasę zawierającą mapy usługi.  
  
### <a name="remarks"></a>Uwagi  
 Do implementowania dostawcy usługi na obiekt COM, użyj mapy usługi. Po pierwsze, musi pochodzić z klasy [IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md). Istnieją dwa typy wpisów:  
  
- [SERVICE_ENTRY](#service_entry) wskazuje pomocy technicznej usługi określony identyfikator.  
  
- [SERVICE_ENTRY_CHAIN](#service_entry_chain) nakazuje [IServiceProviderImpl::QueryService](#queryservice) łańcucha do innego, określonego obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#57](../../atl/codesnippet/cpp/service-map-macros_1.h)]  
  
##  <a name="end_service_map"></a>  END_SERVICE_MAP  
 Oznacza koniec mapy usługi.  
  
```
END_SERVICE_MAP()
```  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [BEGIN_SERVICE_MAP](#begin_service_map).  
  
##  <a name="service_entry"></a>  SERVICE_ENTRY  
 Oznacza, że obiekt obsługuje podany identyfikator usługi przez *SID*.  
  
```
SERVICE_ENTRY( SID )
```  
  
### <a name="parameters"></a>Parametry  
 *IDENTYFIKATOR SID*  
 Identyfikator usługi.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [BEGIN_SERVICE_MAP](#begin_service_map).  
  
##  <a name="service_entry_chain"></a>  SERVICE_ENTRY_CHAIN  
 Powoduje, że [IServiceProviderImpl::QueryService](#queryservice) do tworzenia łańcucha obiekt określony przez `punk`.  
  
```
SERVICE_ENTRY_CHAIN( punk )
```  
  
### <a name="parameters"></a>Parametry  
 `punk`  
 Wskaźnik do **IUnknown** interfejsu, do którego łańcucha.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [BEGIN_SERVICE_MAP](#begin_service_map).  
  
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
 [Makra](../../atl/reference/atl-macros.md)
