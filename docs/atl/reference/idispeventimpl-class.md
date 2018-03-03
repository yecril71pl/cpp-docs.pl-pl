---
title: Klasa IDispEventImpl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDispEventImpl
- ATLCOM/ATL::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::GetFuncInfoFromId
- ATLCOM/ATL::IDispEventImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventImpl::GetUserDefinedType
dev_langs:
- C++
helpviewer_keywords:
- IDispEventImpl class
ms.assetid: a64b5288-35cb-4638-aad6-2d15b1c7cf7b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f052ddf0194cf28a0845ae51b9503841ca880912
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="idispeventimpl-class"></a>Klasa IDispEventImpl
Ta klasa zawiera implementacje `IDispatch` metody.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <UINT nID, class T,
    const IID* pdiid = &IID_NULL,
    const GUID* plibid = &GUID_NULL,
    WORD wMajor = 0,
    WORD wMinor = 0, 
    class tihclass = CcomTypeInfoHolder>  
class ATL_NO_VTABLE IDispEventImpl : public IDispEventSimpleImpl<nID, T, pdiid>
```  
  
#### <a name="parameters"></a>Parametry  
 `nID`  
 Unikatowy identyfikator dla obiekt źródłowy. Gdy `IDispEventImpl` jest klasą bazową dla formantu złożonego, należy użyć Identyfikatora zasobu żądanego formantu zawartych w niej dla tego parametru. W innych przypadkach należy użyć dowolną dodatnią liczbą całkowitą.  
  
 `T`  
 Klasa użytkownika, która jest pochodną `IDispEventImpl`.  
  
 `pdiid`  
 Wskaźnik do uzyskanie identyfikatora IID Interfejs rozdzielania zdarzeń implementowana przez tę klasę. Ten interfejs musi być zdefiniowany w bibliotece typów wskazywane przez `plibid`, `wMajor`, i `wMinor`.  
  
 `plibid`  
 Wskaźnik do biblioteki typów, który definiuje interfejs wysyłania wskazywana przez `pdiid`. Jeśli **& GUID_NULL**, biblioteki typów zostaną załadowane z obiektu źródłem zdarzenia.  
  
 `wMajor`  
 Wersja główna biblioteki typów. Wartość domyślna to 0.  
  
 `wMinor`  
 Wersja pomocnicza biblioteki typów. Wartość domyślna to 0.  
  
 `tihclass`  
 Klasa używana do zarządzania informacji o typie `T`. Wartość domyślna to klasy typu `CComTypeInfoHolder`, jednak można zastąpić tego parametru szablonu, zapewniając klasy typu innego niż `CComTypeInfoHolder`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IDispEventImpl::_tihclass](../../atl/reference/idispeventimpl-class.md)|Klasa używana do zarządzania informacjami o typie. Domyślnie `CComTypeInfoHolder`.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IDispEventImpl::IDispEventImpl](#idispeventimpl)|Konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IDispEventImpl::GetFuncInfoFromId](#getfuncinfofromid)|Lokalizuje indeksu funkcja wysyłania określonego identyfikatora.|  
|[IDispEventImpl::GetIDsOfNames](#getidsofnames)|Mapuje pojedynczy element członkowski i opcjonalny zestaw argument nazwy do odpowiedniego zestawu całkowitą identyfikator DISPID.|  
|[IDispEventImpl::GetTypeInfo](#gettypeinfo)|Pobiera informacje o typie dla obiekt.|  
|[IDispEventImpl::GetTypeInfoCount](#gettypeinfocount)|Pobiera liczbę typu informacji interfejsów.|  
|[IDispEventImpl::GetUserDefinedType](#getuserdefinedtype)|Pobiera typ podstawowy typu zdefiniowanego przez użytkownika.|  
  
## <a name="remarks"></a>Uwagi  
 `IDispEventImpl`zapewnia sposób wdrażania Interfejs rozdzielania zdarzeń, bez konieczności podać kod implementacji dla każdej metody lub zdarzenia w tym interfejsie. `IDispEventImpl`zawiera implementacje `IDispatch` metody. Należy dostarczyć implementacje wybrane w obsłudze zdarzeń.  
  
 `IDispEventImpl`działa w połączeniu z mapą obiekt sink zdarzenia w klasie zdarzeń trasy do funkcji obsługi odpowiednie. Aby użyć tej klasy:  
  

 Dodaj [SINK_ENTRY](composite-control-macros.md#sink_entry) lub [SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex) makro do mapy obiekt sink zdarzenia dla każdego zdarzenia dla każdego obiektu, który ma obsługiwać. Korzystając z `IDispEventImpl` jako klasa podstawowa formantu złożonego, należy wywołać [AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap) i przerwać połączenie ze źródła zdarzeń dla wszystkich wpisów w zdarzeniu sink mapy. W innych przypadkach lub większą kontrolę, wywołaj [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) do nawiązywania połączenia między obiektu źródłowego i klasy podstawowej. Wywołanie [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise) aby przerwać połączenie.  

  
 Musi pochodzić od `IDispEventImpl` (przy użyciu unikatową wartość `nID`) dla każdego obiektu, dla których potrzebujesz do obsługi zdarzeń. Można ponownie użyć klasy podstawowej przez unadvising względem obiektu jednego źródła, następnie udzielanie porad względem obiektu innego źródła, ale maksymalna liczba obiektów źródła, które są obsługiwane przez jeden obiekt w tym samym czasie jest ograniczona liczba `IDispEventImpl` klasy podstawowej.  
  
 `IDispEventImpl`zapewnia te same funkcje co [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md), z wyjątkiem pobiera z biblioteki typów zamiast go podana jako wskaźnik do typu informacji na temat interfejsu [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) Struktura. Użyj `IDispEventSimpleImpl` gdy nie masz biblioteki typów dla interfejsu zdarzenia opisujące lub aby uniknąć obciążenia związanego z przy użyciu biblioteki typów.  
  
> [!NOTE]
> `IDispEventImpl`i `IDispEventSimpleImpl` podać własne implementacja **IUnknown::QueryInterface** każda Włączanie `IDispEventImpl` i `IDispEventSimpleImpl` klasy do działania jako osobna tożsamość COM, umożliwiając bezpośredniego dostępu do klasy podstawowej Członkowie w głównym obiektu COM.  
  
 Implementacja CE ATL ActiveX event sink tylko obsługuje zwracanych wartości typu HRESULT lub void z metody obsługi zdarzeń; inne wartości zwracanej jest nieobsługiwany i jego zachowanie jest niezdefiniowana.  
  
 Aby uzyskać więcej informacji, zobacz [Obsługa IDispEventImpl](../../atl/supporting-idispeventimpl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `_IDispEvent`  
  
 `_IDispEventLocator`  
  
 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)  
  
 `IDispEventImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="getfuncinfofromid"></a>IDispEventImpl::GetFuncInfoFromId  
 Lokalizuje indeksu funkcja wysyłania określonego identyfikatora.  
  
```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [in] Odwołanie do Identyfikatora funkcji.  
  
 *dispidMember*  
 [in] Identyfikator wysyłania funkcji.  
  
 `lcid`  
 [in] Kontekst ustawień regionalnych z identyfikatorem funkcji.  
  
 `info`  
 [in] Struktura wskazującą sposób wywołania funkcji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
##  <a name="getidsofnames"></a>IDispEventImpl::GetIDsOfNames  
 Mapuje jeden element członkowski i opcjonalny zestaw argument nazwy do odpowiedniego zestawu całkowitą identyfikator DISPID, które mogą być używane w kolejnych wywołań [IDispatch::Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d).  
  
```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [funkcji IDispatch::GetIDsOfNames](http://msdn.microsoft.com/en-us/6f6cf233-3481-436e-8d6a-51f93bf91619) w systemie Windows SDK.  
  
##  <a name="gettypeinfo"></a>IDispEventImpl::GetTypeInfo  
 Pobiera informacje o typie dla obiektu, których następnie można użyć do uzyskania informacji o typie interfejsu.  
  
```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="gettypeinfocount"></a>IDispEventImpl::GetTypeInfoCount  
 Pobiera informację o liczbie typów interfejsów, jakie zawiera obiekt (0 lub 1).  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IDispatch::GetTypeInfoCount](http://msdn.microsoft.com/en-us/da876d53-cb8a-465c-a43e-c0eb272e2a12) w systemie Windows SDK.  
  
##  <a name="getuserdefinedtype"></a>IDispEventImpl::GetUserDefinedType  
 Pobiera typ podstawowy typu zdefiniowanego przez użytkownika.  
  
```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```  
  
### <a name="parameters"></a>Parametry  
 `pTI`  
 [in] Wskaźnik do [ITypeInfo](http://msdn.microsoft.com/en-us/f3356463-3373-4279-bae1-953378aa2680) interfejs zawierający typ zdefiniowany przez użytkownika.  
  
 *hrt*  
 [in] Dojście do opisu typu, które mają zostać pobrane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Typ wariantu.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [Metoda ITypeInfo::GetRefTypeInfo](http://msdn.microsoft.com/en-us/61d3b31d-6591-4e55-9e82-5246a168be00).  
  
##  <a name="idispeventimpl"></a>IDispEventImpl::IDispEventImpl  
 Konstruktor. Przechowuje wartości parametrów szablonu klasy `plibid`, `pdiid`, `wMajor`, i `wMinor`.  
  
```
IDispEventImpl();
```  
  
##  <a name="tihclass"></a>IDispEventImpl::tihclass  
 Ten element typedef jest wystąpieniem klasy parametru szablonu `tihclass`.  
  
```
typedef tihclass _tihclass;
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie jest klasa `CComTypeInfoHolder`. `CComTypeInfoHolder`zarządza informacji o typie dla klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura _ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)   
 [Klasa elementem IDispatchImpl](../../atl/reference/idispatchimpl-class.md)   
 [Klasa IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)   
 [SINK_ENTRY](composite-control-macros.md#sink_entry)   
 [SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)   
 [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)   
 [Przegląd klas](../../atl/atl-class-overview.md)