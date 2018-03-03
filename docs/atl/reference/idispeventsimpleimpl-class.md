---
title: Klasa IDispEventSimpleImpl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl::Advise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventAdvise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventUnadvise
- ATLCOM/ATL::IDispEventSimpleImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventSimpleImpl::Invoke
- ATLCOM/ATL::IDispEventSimpleImpl::Unadvise
dev_langs:
- C++
helpviewer_keywords:
- IDispEventSimpleImpl class
ms.assetid: 971d82b7-a921-47fa-a4d8-909bed377ab0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f8a5b3098961af4f3f9262cdc4c99dbe80b4ac7c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="idispeventsimpleimpl-class"></a>Klasa IDispEventSimpleImpl
Ta klasa zawiera implementacje `IDispatch` metody bez uzyskiwania informacji o typie z biblioteki typów.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <UINT nID, class T, const IID* pdiid>  
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```    
  
#### <a name="parameters"></a>Parametry  
 `nID`  
 Unikatowy identyfikator dla obiekt źródłowy. Gdy `IDispEventSimpleImpl` jest klasą bazową dla formantu złożonego, należy użyć Identyfikatora zasobu żądanego formantu zawartych w niej dla tego parametru. W innych przypadkach należy użyć dowolną dodatnią liczbą całkowitą.  
  
 `T`  
 Klasa użytkownika, która jest pochodną `IDispEventSimpleImpl`.  
  
 `pdiid`  
 Wskaźnik do uzyskanie identyfikatora IID Interfejs rozdzielania zdarzeń implementowana przez tę klasę.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IDispEventSimpleImpl::Advise](#advise)|Ustanawia połączenie z domyślne źródło zdarzeń.|  
|[IDispEventSimpleImpl::DispEventAdvise](#dispeventadvise)|Ustanawia połączenie ze źródłem zdarzenia.|  
|[IDispEventSimpleImpl::DispEventUnadvise](#dispeventunadvise)|Przerywa połączenie ze źródłem zdarzenia.|  
|[IDispEventSimpleImpl::GetIDsOfNames](#getidsofnames)|Zwraca **E_NOTIMPL**.|  
|[IDispEventSimpleImpl::GetTypeInfo](#gettypeinfo)|Zwraca **E_NOTIMPL**.|  
|[IDispEventSimpleImpl::GetTypeInfoCount](#gettypeinfocount)|Zwraca **E_NOTIMPL**.|  
|[IDispEventSimpleImpl::Invoke](#invoke)|Wywołań obsługi zdarzeń na liście zdarzeń zbiornika mapy.|  
|[IDispEventSimpleImpl::Unadvise](#unadvise)|Przerywa połączenie z domyślne źródło zdarzeń.|  
  
## <a name="remarks"></a>Uwagi  
 `IDispEventSimpleImpl`zapewnia sposób wdrażania Interfejs rozdzielania zdarzeń, bez konieczności podać kod implementacji dla każdej metody lub zdarzenia w tym interfejsie. `IDispEventSimpleImpl`zawiera implementacje `IDispatch` metody. Należy dostarczyć implementacje wybrane w obsłudze zdarzeń.  
  
 `IDispEventSimpleImpl`działa w połączeniu z mapą obiekt sink zdarzenia w klasie zdarzeń trasy do funkcji obsługi odpowiednie. Aby użyć tej klasy:  
  
-   Dodaj [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) makro do mapy obiekt sink zdarzenia dla każdego zdarzenia dla każdego obiektu, który ma obsługiwać.  
  
-   Podaj informacje o typie dla każdego zdarzenia przez przekazanie wskaźnika do [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) struktury jako parametru dla każdego wpisu. Na x86 platformy, `_ATL_FUNC_INFO.cc` wartość musi być CC_CDECL za pomocą funkcji wywołania zwrotnego wywołanie metody __stdcall.  
  
-   Wywołanie [DispEventAdvise](#dispeventadvise) do nawiązywania połączenia między obiektu źródłowego i klasy podstawowej.  
  
-   Wywołanie [DispEventUnadvise](#dispeventunadvise) aby przerwać połączenie.  
  
 Musi pochodzić od `IDispEventSimpleImpl` (przy użyciu unikatową wartość `nID`) dla każdego obiektu, dla których potrzebujesz do obsługi zdarzeń. Można ponownie użyć klasy podstawowej przez unadvising względem obiektu jednego źródła, następnie udzielanie porad względem obiektu innego źródła, ale maksymalna liczba obiektów źródła, które są obsługiwane przez jeden obiekt w tym samym czasie jest ograniczona liczba `IDispEventSimpleImpl` klasy podstawowej.  
  
 **IDispEventSimplImpl** zapewnia te same funkcje co [IDispEventImpl](../../atl/reference/idispeventimpl-class.md), z wyjątkiem nie pobrać typu informacji na temat interfejsu z biblioteki typów. Kreatorów generowanie kodu opartego tylko na `IDispEventImpl`, ale można użyć `IDispEventSimpleImpl` przez ręczne dodanie kodu. Użyj `IDispEventSimpleImpl` gdy nie ma biblioteki typów dla interfejsu zdarzenia opisujące lub aby uniknąć obciążenia związanego z przy użyciu biblioteki typów.  
  
> [!NOTE]
> `IDispEventImpl`i `IDispEventSimpleImpl` podać własne implementacja **IUnknown::QueryInterface** każda Włączanie `IDispEventImpl` lub `IDispEventSimpleImpl` klasy do działania jako osobna tożsamość COM, umożliwiając bezpośredni dostęp do elementów członkowskich klasy podstawowej w głównym obiekcie COM.  
  
 Implementacja CE ATL ActiveX event sink tylko obsługuje zwracanych wartości typu HRESULT lub void z metody obsługi zdarzeń; inne wartości zwracanej jest nieobsługiwany i jego zachowanie jest niezdefiniowana.  
  
 Aby uzyskać więcej informacji, zobacz [Obsługa IDispEventImpl](../../atl/supporting-idispeventimpl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `_IDispEvent`  
  
 `_IDispEventLocator`  
  
 `IDispEventSimpleImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="advise"></a>IDispEventSimpleImpl::Advise  
 Wywołaj tę metodę w celu nawiązania połączenia ze źródłem zdarzenia reprezentowany przez *pUnk*.  
  
```
HRESULT Advise(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnk*  
 [in] Wskaźnik do **IUnknown** interfejsu zdarzeń obiektu źródłowego.  
  
### <a name="return-value"></a>Wartość zwracana  
 `S_OK`lub jakiekolwiek niepowodzenie `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Po nawiązaniu połączenia zdarzenia wywoływane z *pUnk* będą kierowane do obsługi w klasie i map obiekt sink zdarzenia.  
  
> [!NOTE]
>  Jeśli na klasę pochodną wielu `IDispEventSimpleImpl` klas, konieczne będzie odróżnienia wywołania tej metody przez zakresu wywołań z konkretnej klasy podstawowej planuje się.  
  
 `Advise`nawiązuje połączenie ze źródłem zdarzenia domyślne, pobiera uzyskanie identyfikatora IID domyślne źródło zdarzeń obiektu zgodnie z ustaleniami [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).  
  
##  <a name="dispeventadvise"></a>IDispEventSimpleImpl::DispEventAdvise  
 Wywołaj tę metodę w celu nawiązania połączenia ze źródłem zdarzenia reprezentowany przez *pUnk*.  
  
```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnk*  
 [in] Wskaźnik do **IUnknown** interfejsu zdarzeń obiektu źródłowego.  
  
 `piid`  
 Wskaźnik do identyfikatora IID obiektu źródła zdarzenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 `S_OK`lub jakiekolwiek niepowodzenie `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Następnie zdarzenia wywoływane z *pUnk* będą kierowane do obsługi w klasie i map obiekt sink zdarzenia.  
  
> [!NOTE]
>  Jeśli na klasę pochodną wielu `IDispEventSimpleImpl` klas, konieczne będzie odróżnienia wywołania tej metody przez zakresu wywołań z konkretnej klasy podstawowej planuje się.  
  
 `DispEventAdvise`nawiązuje połączenie ze źródłem zdarzeń określony w `pdiid`.  
  
##  <a name="dispeventunadvise"></a>IDispEventSimpleImpl::DispEventUnadvise  
 Przerywa połączenie ze źródłem zdarzenia reprezentowany przez *pUnk*.  
  
```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnk*  
 [in] Wskaźnik do **IUnknown** interfejsu zdarzeń obiektu źródłowego.  
  
 `piid`  
 Wskaźnik do identyfikatora IID obiektu źródła zdarzenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 `S_OK`lub jakiekolwiek niepowodzenie `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Gdy połączenie jest przerywane, zdarzenia nie będą kierowane do funkcje obsługi wymienionych w mapie obiekt sink zdarzenia.  
  
> [!NOTE]
>  Jeśli na klasę pochodną wielu `IDispEventSimpleImpl` klas, konieczne będzie odróżnienia wywołania tej metody przez zakresu wywołań z konkretnej klasy podstawowej planuje się.  
  
 `DispEventAdvise`przerywa połączenie, które zostało ustanowione źródło zdarzeń określony w `pdiid`.  
  
##  <a name="getidsofnames"></a>IDispEventSimpleImpl::GetIDsOfNames  
 Ta implementacja **funkcji IDispatch::GetIDsOfNames** zwraca **E_NOTIMPL**.  
  
```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [funkcji IDispatch::GetIDsOfNames](http://msdn.microsoft.com/en-us/6f6cf233-3481-436e-8d6a-51f93bf91619) w systemie Windows SDK.  
  
##  <a name="gettypeinfo"></a>IDispEventSimpleImpl::GetTypeInfo  
 Ta implementacja **IDispatch::GetTypeInfo** zwraca **E_NOTIMPL**.  
  
```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IDispatch::GetTypeInfo](http://msdn.microsoft.com/en-us/cc1ec9aa-6c40-4e70-819c-a7c6dd6b8c99) w systemie Windows SDK.  
  
##  <a name="gettypeinfocount"></a>IDispEventSimpleImpl::GetTypeInfoCount  
 Ta implementacja **IDispatch::GetTypeInfoCount** zwraca **E_NOTIMPL**.  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IDispatch::GetTypeInfoCount](http://msdn.microsoft.com/en-us/da876d53-cb8a-465c-a43e-c0eb272e2a12) w systemie Windows SDK.  
  
##  <a name="invoke"></a>IDispEventSimpleImpl::Invoke  
 Ta implementacja **IDispatch::Invoke** wywołań obsługi zdarzeń na liście zdarzeń zbiornika mapy.  
  
```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID /* riid */,
    LCID lcid,
    WORD /* wFlags */,
    DISPPARMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* /* pexcepinfo */,
    UINT* /* puArgErr */);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IDispatch::Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d).  
  
##  <a name="unadvise"></a>IDispEventSimpleImpl::Unadvise  
 Przerywa połączenie ze źródłem zdarzenia reprezentowany przez *pUnk*.  
  
```
HRESULT Unadvise(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnk*  
 [in] Wskaźnik do **IUnknown** interfejsu zdarzeń obiektu źródłowego.  
  
### <a name="return-value"></a>Wartość zwracana  
 `S_OK`lub jakiekolwiek niepowodzenie `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Gdy połączenie jest przerywane, zdarzenia nie będą kierowane do funkcje obsługi wymienionych w mapie obiekt sink zdarzenia.  
  
> [!NOTE]
>  Jeśli na klasę pochodną wielu `IDispEventSimpleImpl` klas, konieczne będzie odróżnienia wywołania tej metody przez zakresu wywołań z konkretnej klasy podstawowej planuje się.  
  
 `Unadvise`przerywa połączenie, które zostało ustanowione domyślne źródło zdarzeń określony w `pdiid`.  
  
 **Unavise** podziały połączenia ze źródłem zdarzenia domyślne, pobiera uzyskanie identyfikatora IID domyślne źródło zdarzeń obiektu zgodnie z ustaleniami [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura _ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)   
 [Klasa elementem IDispatchImpl](../../atl/reference/idispatchimpl-class.md)   
 [Klasa IDispEventImpl](../../atl/reference/idispeventimpl-class.md)   
 [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)   
 [Przegląd klas](../../atl/atl-class-overview.md)
