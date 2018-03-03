---
title: Klasa IViewObjectExImpl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IViewObjectExImpl
- ATLCTL/ATL::IViewObjectExImpl
- ATLCTL/ATL::IViewObjectExImpl::Draw
- ATLCTL/ATL::IViewObjectExImpl::Freeze
- ATLCTL/ATL::IViewObjectExImpl::GetAdvise
- ATLCTL/ATL::IViewObjectExImpl::GetColorSet
- ATLCTL/ATL::IViewObjectExImpl::GetExtent
- ATLCTL/ATL::IViewObjectExImpl::GetNaturalExtent
- ATLCTL/ATL::IViewObjectExImpl::GetRect
- ATLCTL/ATL::IViewObjectExImpl::GetViewStatus
- ATLCTL/ATL::IViewObjectExImpl::QueryHitPoint
- ATLCTL/ATL::IViewObjectExImpl::QueryHitRect
- ATLCTL/ATL::IViewObjectExImpl::SetAdvise
- ATLCTL/ATL::IViewObjectExImpl::Unfreeze
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], drawing
- IViewObjectEx ATL implementation
- advise sinks
- IViewObjectExImpl class
ms.assetid: ad6de760-1ee5-4883-b033-ae57beffc369
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 742198b0bf6c5c615baed033e8a0fab7e73b06ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="iviewobjecteximpl-class"></a>Klasa IViewObjectExImpl
Ta klasa implementuje **IUnknown** i zawiera domyślne implementacje [IViewObject](http://msdn.microsoft.com/library/windows/desktop/ms680763), [IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318), i [IViewObjectEx](http://msdn.microsoft.com/library/windows/desktop/ms682375)interfejsów.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>  
class ATL_NO_VTABLE IViewObjectExImpl 
   : public IViewObjectEx
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IViewObjectExImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IViewObjectExImpl::Draw](#draw)|Rysuje reprezentację formant na kontekst urządzenia.|  
|[IViewObjectExImpl::Freeze](#freeze)|Zawiesza się narysowanego reprezentację formantu, więc nie zmieni się do `Unfreeze`. Zwraca implementację ATL **E_NOTIMPL**.|  
|[IViewObjectExImpl::GetAdvise](#getadvise)|Pobiera istniejące połączenie advisory zbiornika w formancie, jeśli istnieje.|  
|[IViewObjectExImpl::GetColorSet](#getcolorset)|Zwraca wartość logiczną paletę używanych przez formant na rysunku. Zwraca implementację ATL **E_NOTIMPL**.|  
|[IViewObjectExImpl::GetExtent](#getextent)|Pobiera rozmiar wyświetlania formantu w jednostkach HIMETRIC (0,01 milimetra na jednostkę) z element członkowski danych klasy formantu [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).|  
|[IViewObjectExImpl::GetNaturalExtent](#getnaturalextent)|Zawiera wskazówki dotyczące zmiany rozmiaru w kontenerze dla obiekt, który ma być używana jako użytkownik zmienia jego rozmiar.|  
|[IViewObjectExImpl::GetRect](#getrect)|Zwraca prostokąt opisujący żądany aspekt rysowania. Zwraca implementację ATL **E_NOTIMPL**.|  
|[IViewObjectExImpl::GetViewStatus](#getviewstatus)|Zwraca informacje dotyczące przezroczystości obiektu oraz obsługiwanych aspektów rysujących.|  
|[IViewObjectExImpl::QueryHitPoint](#queryhitpoint)|Sprawdza, czy określony punkt znajduje się w prostokącie określonego i zwraca [HITRESULT](http://msdn.microsoft.com/library/windows/desktop/ms682187) wartość w `pHitResult`.|  
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|Sprawdza, czy prostokątny obszar wyświetlania formantu nakłada się na dowolnym etapie prostokąt określonej lokalizacji i zwraca **HITRESULT** wartość w `pHitResult`.|  
|[IViewObjectExImpl::SetAdvise](#setadvise)|Konfiguruje połączenia między formantem a zbiornika Porada — obiekt sink można powiadamiani o zmianach wprowadzonych w widoku formantu.|  
|[IViewObjectExImpl::Unfreeze](#unfreeze)|Unfreezes narysowanego reprezentację formantu. Zwraca implementację ATL **E_NOTIMPL**.|  
  
## <a name="remarks"></a>Uwagi  
 [IViewObject](http://msdn.microsoft.com/library/windows/desktop/ms680763), [IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318), i [IViewObjectEx](http://msdn.microsoft.com/library/windows/desktop/ms682375) interfejsy umożliwiają formantu do wyświetlenia się bezpośrednio oraz do tworzenia i zarządzania zbiornika Porada powiadomiono kontener zmiany sposobu wyświetlania formantu. **IViewObjectEx** interfejsu zapewnia obsługę funkcji rozszerzonej kontroli, takich jak pozbawione migotania rysunku, formanty nieregularnych i przejrzysty i trafień testów (na przykład, jak blisko kliknięcie należy wziąć pod uwagę na kontrola). Klasa `IViewObjectExImpl` udostępnia domyślną implementację tych interfejsów i implementuje **IUnknown** , wysyłając informacje o do zrzutu kompilacje urządzenia podczas debugowania.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IViewObjectEx`  
  
 `IViewObjectExImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
##  <a name="draw"></a>IViewObjectExImpl::Draw  
 Rysuje reprezentację formant na kontekst urządzenia.  
  
```
STDMETHOD(Draw)(
    DWORD dwDrawAspect,
    LONG lindex,
    void* pvAspect,
    DVTARGETDEVICE* ptd,
    HDC hicTargetDev,
    LPCRECTL prcBounds,
    LPCRECTL prcWBounds,
    BOOL(_stdcall* /* pfnContinue*/) (DWORD_PTR dwContinue),
    DWORD_PTR /* dwContinue */);
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wywołuje **CComControl::OnDrawAdvanced** które z kolei wywołuje Twojej klasy kontrolki `OnDraw` metody. `OnDraw` Metody jest automatycznie dodawany do Twojej klasy kontrolki, podczas tworzenia formantu z Kreator formantu ATL. Domyślne kreatora `OnDraw` rysuje prostokąt z etykietą "ATL 3.0".  
  
 Zobacz [IViewObject::Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655) w systemie Windows SDK.  
  
##  <a name="freeze"></a>IViewObjectExImpl::Freeze  
 Zawiesza się narysowanego reprezentację formantu, więc nie zmieni się do `Unfreeze`. Zwraca implementację ATL **E_NOTIMPL**.  
  
```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IViewObject::Freeze](http://msdn.microsoft.com/library/windows/desktop/ms688728) w systemie Windows SDK.  
  
##  <a name="getadvise"></a>IViewObjectExImpl::GetAdvise  
 Pobiera istniejące połączenie advisory zbiornika w formancie, jeśli istnieje.  
  
```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```  
  
### <a name="remarks"></a>Uwagi  
 Zespół Doradczy zbiornika są przechowywane w element członkowski danych klasy formantu [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink).  
  
 Zobacz [IViewObject::GetAdvise](http://msdn.microsoft.com/library/windows/desktop/ms692772) w systemie Windows SDK.  
  
##  <a name="getcolorset"></a>IViewObjectExImpl::GetColorSet  
 Zwraca wartość logiczną paletę używanych przez formant na rysunku. Zwraca implementację ATL **E_NOTIMPL**.  
  
```
STDMETHOD(GetColorSet)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DVTARGETDEVICE* /* ptd */,
    HDC /* hicTargetDevice */,
    LOGPALETTE** /* ppColorSet */);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IViewObject::GetColorSet](http://msdn.microsoft.com/library/windows/desktop/ms686553) w systemie Windows SDK.  
  
##  <a name="getextent"></a>IViewObjectExImpl::GetExtent  
 Pobiera rozmiar wyświetlania formantu w jednostkach HIMETRIC (0,01 milimetra na jednostkę) z element członkowski danych klasy formantu [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).  
  
```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IViewObject2::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms684032) w systemie Windows SDK.  
  
##  <a name="getnaturalextent"></a>IViewObjectExImpl::GetNaturalExtent  
 Zawiera wskazówki dotyczące zmiany rozmiaru w kontenerze dla obiekt, który ma być używana jako użytkownik zmienia jego rozmiar.  
  
```
STDMETHOD(GetNaturalExtent)(
    DWORD dwAspect,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    HDC /* hicTargetDevice */,
    DVEXTENTINFO* pExtentInfo,
    LPSIZEL psizel);
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `dwAspect` jest `DVASPECT_CONTENT` i *pExtentInfo -> dwExtentMode* jest **DVEXTENT_CONTENT**, ustawia * `psizel` na element członkowski danych klasy formantu [CComControlBase: : m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural). W przeciwnym razie zwraca błąd `HRESULT`.  
  
 Zobacz [IViewObjectEx::GetNaturalExtent](http://msdn.microsoft.com/library/windows/desktop/ms683718) w systemie Windows SDK.  
  
##  <a name="getrect"></a>IViewObjectExImpl::GetRect  
 Zwraca prostokąt opisujący żądany aspekt rysowania. Zwraca implementację ATL **E_NOTIMPL**.  
  
```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IViewObjectEx::GetRect](http://msdn.microsoft.com/library/windows/desktop/ms695246) w systemie Windows SDK.  
  
##  <a name="getviewstatus"></a>IViewObjectExImpl::GetViewStatus  
 Zwraca informacje dotyczące przezroczystości obiektu oraz obsługiwanych aspektów rysujących.  
  
```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ustawia ATL `pdwStatus` wskazująca, czy kontrolka obsługuje **VIEWSTATUS_OPAQUE** (możliwe wartości to w [podwójne](http://msdn.microsoft.com/library/windows/desktop/ms687201) wyliczenie).  
  
 Zobacz [IViewObjectEx::GetViewStatus](http://msdn.microsoft.com/library/windows/desktop/ms693371) w systemie Windows SDK.  
  
##  <a name="queryhitpoint"></a>IViewObjectExImpl::QueryHitPoint  
 Sprawdza, czy określony punkt znajduje się w prostokącie określonego i zwraca [HITRESULT](http://msdn.microsoft.com/library/windows/desktop/ms682187) wartość w `pHitResult`.  
  
```
STDMETHOD(QueryHitPoint)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    POINT ptlLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```  
  
### <a name="remarks"></a>Uwagi  
 Wartość może być albo **HITRESULT_HIT** lub **HITRESULT_OUTSIDE**.  
  
 Jeśli `dwAspect` jest równe [DVASPECT_CONTENT](http://msdn.microsoft.com/library/windows/desktop/ms690318), metoda zwraca `S_OK`. W przeciwnym razie metoda zwraca **E_FAIL**.  
  
 Zobacz [IViewObjectEx::QueryHitPoint](http://msdn.microsoft.com/library/windows/desktop/ms691209) w systemie Windows SDK.  
  
##  <a name="queryhitrect"></a>IViewObjectExImpl::QueryHitRect  
 Sprawdza, czy prostokątny obszar wyświetlania formantu nakłada się na dowolnym etapie prostokąt określonej lokalizacji i zwraca [HITRESULT](http://msdn.microsoft.com/library/windows/desktop/ms682187) wartość w `pHitResult`.  
  
```
STDMETHOD(QueryHitRect)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    LPRECT prcLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```  
  
### <a name="remarks"></a>Uwagi  
 Wartość może być albo **HITRESULT_HIT** lub **HITRESULT_OUTSIDE**.  
  
 Jeśli `dwAspect` jest równe [DVASPECT_CONTENT](http://msdn.microsoft.com/library/windows/desktop/ms690318), metoda zwraca `S_OK`. W przeciwnym razie metoda zwraca **E_FAIL**.  
  
 Zobacz [IViewObjectEx::QueryHitRect](http://msdn.microsoft.com/library/windows/desktop/ms693797) w systemie Windows SDK.  
  
##  <a name="setadvise"></a>IViewObjectExImpl::SetAdvise  
 Konfiguruje połączenia między formantem a zbiornika Porada — obiekt sink można powiadamiani o zmianach wprowadzonych w widoku formantu.  
  
```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```  
  
### <a name="remarks"></a>Uwagi  

 Wskaźnik do [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513) interfejsu zbiornika Porada są przechowywane w element członkowski danych klasy formantu [CComControlBase::m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink).  

  
 Zobacz [IViewObject::SetAdvise](http://msdn.microsoft.com/library/windows/desktop/ms683950) w systemie Windows SDK.  
  
##  <a name="unfreeze"></a>IViewObjectExImpl::Unfreeze  
 Unfreezes narysowanego reprezentację formantu. Zwraca implementację ATL **E_NOTIMPL**.  
  
```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IViewObject::Unfreeze](http://msdn.microsoft.com/library/windows/desktop/ms686641) w systemie Windows SDK.  
  
##  <a name="closehandle"></a>IWorkerThreadClient::CloseHandle  
 Zaimplementuj tę metodę, aby zamknąć dojścia skojarzone z tym obiektem.  
  
```
HRESULT CloseHandle(HANDLE hHandle);
```  
  
### <a name="parameters"></a>Parametry  
 *hHandle*  
 Dojście do zamknięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK na powodzenie lub błąd HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Dojście przekazane do tej metody został wcześniej skojarzony z tym obiektem przez wywołanie do [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).  
  
### <a name="example"></a>Przykład  
 Poniższy kod przedstawia prostych implementacji `IWorkerThreadClient::CloseHandle`.  
  
 [!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]  
  
##  <a name="execute"></a>IWorkerThreadClient::Execute  
 Zaimplementuj tę metodę do wykonania kodu, gdy staje się sygnalizowane dojścia skojarzone z tym obiektem.  
  
```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```  
  
### <a name="parameters"></a>Parametry  
 `dwParam`  
 Parametr użytkownika.  
  
 `hObject`  
 Dojście stają się sygnalizowane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK na powodzenie lub błąd HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Dojście i przekazane do tej metody na wskaźnik DWORD były wcześniej skojarzone z tym obiektem przez wywołanie do [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).  
  
### <a name="example"></a>Przykład  
 Poniższy kod przedstawia prostych implementacji `IWorkerThreadClient::Execute`.  
  
 [!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Interfejsy formantów ActiveX](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Samouczek](../../atl/active-template-library-atl-tutorial.md)   
 [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
