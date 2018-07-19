---
title: Klasa IDispEventImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b482baa9339a50b9a124c0d68b02f60b0236984e
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963754"
---
# <a name="idispeventimpl-class"></a>Klasa IDispEventImpl
Ta klasa zawiera implementacje `IDispatch` metody.  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
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
 *nID*  
 Unikatowy identyfikator obiektu źródłowego. Gdy `IDispEventImpl` jest klasą bazową dla kontrolki złożonej, skorzystaj z zasobów żądaną kontrolki zawartej dla tego parametru. W innych przypadkach należy użyć dowolną dodatnią liczbą całkowitą.  
  
 *T*  
 Klasa użytkownika, która jest pochodną `IDispEventImpl`.  
  
 *pdiid*  
 Wskaźnik do identyfikatora IID z Interfejs rozdzielania zdarzeń, zaimplementowane przez tę klasę. Ten interfejs musi być zdefiniowany w bibliotece typów wskazywane przez *plibid*, *wMajor*, i *wMinor*.  
  
 *plibid*  
 Wskaźnik do biblioteki typów, który definiuje interfejs ekspedycji wskazywany przez *pdiid*. Jeśli **& GUID_NULL**, biblioteka typów zostanie załadowana z obiektu określania źródła zdarzeń.  
  
 *wMajor*  
 Wersja główna biblioteki typów. Wartość domyślna to 0.  
  
 *wMinor*  
 Wersja pomocnicza biblioteki typów. Wartość domyślna to 0.  
  
 *tihclass*  
 Klasa używana do zarządzania informacji o typie *T*. Wartość domyślna to klasy typu `CComTypeInfoHolder`; jednak można zastąpić przy użyciu tego parametru szablonu, zapewniając klasy typu innego niż `CComTypeInfoHolder`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Publiczne definicje typów  
  
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
|[IDispEventImpl::GetFuncInfoFromId](#getfuncinfofromid)|Lokalizuje indeksu funkcji dla identyfikatora określonego wysyłania.|  
|[IDispEventImpl::GetIDsOfNames](#getidsofnames)|Mapuje jeden element członkowski i opcjonalny zestaw nazwy argumentu odpowiedni zestaw DISPID liczby całkowitej.|  
|[IDispEventImpl::GetTypeInfo](#gettypeinfo)|Pobiera informacje o typie dla obiektu.|  
|[IDispEventImpl::GetTypeInfoCount](#gettypeinfocount)|Pobiera liczbę interfejsów informacji typu.|  
|[IDispEventImpl::GetUserDefinedType](#getuserdefinedtype)|Pobiera typ podstawowy typu zdefiniowanego przez użytkownika.|  
  
## <a name="remarks"></a>Uwagi  
 `IDispEventImpl` zapewnia sposób implementowania Interfejs rozdzielania zdarzeń bez konieczności podać kod implementacji dla każdej metody/zdarzenia w tym interfejsie. `IDispEventImpl` zawiera implementacje `IDispatch` metody. Musisz podać implementacje dla zdarzenia wybrane w obsłudze.  
  
 `IDispEventImpl` działa w połączeniu z mapą obiekt sink zdarzenia w klasie do kierowanie zdarzeń do funkcji odpowiedni program obsługi. Aby użyć tej klasy:  
  

 Dodaj [SINK_ENTRY](composite-control-macros.md#sink_entry) lub [SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex) makra do mapy obiektu sink zdarzenia dla każdego zdarzenia dla każdego obiektu, który chcesz obsługiwać. Korzystając z `IDispEventImpl` jako klasa bazowa kontrolki złożonej, można wywołać [AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap) i przerwać połączenie ze źródłami zdarzeń, dla wszystkich wpisów w zdarzeniu ujścia mapy. W innych przypadkach, lub Aby uzyskać większą kontrolę, wywołanie [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) do nawiązywania połączenia między obiektu źródłowego oraz klasy bazowej. Wywołaj [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise) aby przerwać połączenie.  

  
 Muszą pochodzić od `IDispEventImpl` (przy użyciu unikatową wartość dla *nID*) dla każdego obiektu, dla których potrzebujesz do obsługi zdarzeń. Można ponownie użyć klasy bazowej przez unadvising względem obiektu jednego źródła, następnie wniosku względem obiektu innego źródła, ale maksymalna liczba obiektów źródłowej, które są obsługiwane przez pojedynczy obiekt w tym samym czasie, jest ograniczona przez liczbę `IDispEventImpl` klas bazowych.  
  
 `IDispEventImpl` udostępnia taką samą funkcjonalność jak [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md), z wyjątkiem otrzymuje typ informacji na temat interfejsu z biblioteki typów, niż musieć go podana jako wskaźnik do [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) Struktura. Użyj `IDispEventSimpleImpl` podczas nie masz biblioteki typów, opisujący interfejs zdarzenia lub aby uniknąć obciążenia związanego z używaniem biblioteki typów.  
  
> [!NOTE]
> `IDispEventImpl` i `IDispEventSimpleImpl` zapewniali własną implementację programu `IUnknown::QueryInterface` włączania każdej `IDispEventImpl` i `IDispEventSimpleImpl` klasy bazowej na działania jako osobne tożsamości COM wciąż zezwalając bezpośredni dostęp do elementów członkowskich klasy w głównym obiektu COM.  
  
 Implementacja CE ATL ActiveX zdarzenia sink tylko obsługuje zwracanej wartości typu HRESULT lub void ze swojej metody obsługi zdarzeń; Dowolna inna wartość zwracana nie jest obsługiwany, a jego zachowanie jest niezdefiniowane.  
  
 Aby uzyskać więcej informacji, zobacz [Obsługa interfejsu IDispEventImpl](../../atl/supporting-idispeventimpl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `_IDispEvent`  
  
 `_IDispEventLocator`  
  
 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)  
  
 `IDispEventImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="getfuncinfofromid"></a>  IDispEventImpl::GetFuncInfoFromId  
 Lokalizuje indeksu funkcji dla identyfikatora określonego wysyłania.  
  
```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```  
  
### <a name="parameters"></a>Parametry  
 *IID*  
 [in] Odwołanie do Identyfikatora funkcji.  
  
 *dispidMember*  
 [in] Identyfikator wysyłania funkcji.  
  
 *lcid*  
 [in] Ustawienia regionalne kontekstu identyfikatorem funkcji.  
  
 *Informacje o*  
 [in] Struktura, wskazujący, jak wywołania funkcji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT.  
  
##  <a name="getidsofnames"></a>  IDispEventImpl::GetIDsOfNames  
 Mapuje jeden element członkowski i opcjonalny zestaw nazwy argumentu odpowiedni zestaw liczby całkowitej DISPID, które mogą być używane w kolejnych wywołaniach [uwzględniając](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke).  
  
```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IDispatch::GetIDsOfNames](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-getidsofnames) w Windows SDK.  
  
##  <a name="gettypeinfo"></a>  IDispEventImpl::GetTypeInfo  
 Pobiera informacje o typie dla obiektu, których następnie można użyć do uzyskania informacji o typie interfejsu.  
  
```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="gettypeinfocount"></a>  IDispEventImpl::GetTypeInfoCount  
 Pobiera informację o liczbie typów interfejsów, jakie zawiera obiekt (0 lub 1).  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IDispatch::GetTypeInfoCount](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) w Windows SDK.  
  
##  <a name="getuserdefinedtype"></a>  IDispEventImpl::GetUserDefinedType  
 Pobiera typ podstawowy typu zdefiniowanego przez użytkownika.  
  
```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```  
  
### <a name="parameters"></a>Parametry  
 *pTI*  
 [in] Wskaźnik do [ITypeInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interfejs, zawierający typ zdefiniowany przez użytkownika.  
  
 *hrt*  
 [in] Dojście do opisu typu do pobrania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Typ variant.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [Metoda ITypeInfo::GetRefTypeInfo](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-itypeinfo-getreftypeinfo).  
  
##  <a name="idispeventimpl"></a>  IDispEventImpl::IDispEventImpl  
 Konstruktor. Przechowuje wartości parametrów szablonu klasy *plibid*, *pdiid*, *wMajor*, i *wMinor*.  
  
```
IDispEventImpl();
```  
  
##  <a name="tihclass"></a>  IDispEventImpl::tihclass  
 Ten element typedef jest wystąpieniem typu parametru szablonu klasy *tihclass*.  
  
```
typedef tihclass _tihclass;
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie klasa jest `CComTypeInfoHolder`. `CComTypeInfoHolder` zarządza informacji o typie klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura _ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)   
 [Klasa IDispatchImpl](../../atl/reference/idispatchimpl-class.md)   
 [Klasa IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)   
 [SINK_ENTRY](composite-control-macros.md#sink_entry)   
 [SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)   
 [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)