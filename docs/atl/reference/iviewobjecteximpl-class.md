---
title: Klasa IViewObjectExImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a7364f86ad08f882660f49556853826bb7186f6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108433"
---
# <a name="iviewobjecteximpl-class"></a>Klasa IViewObjectExImpl

Ta klasa implementuje `IUnknown` i zawiera domyślne implementacje [IViewObject](/windows/desktop/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/desktop/api/oleidl/nn-oleidl-iviewobject2), i [IViewObjectEx](/windows/desktop/api/ocidl/nn-ocidl-iviewobjectex) interfejsów.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class ATL_NO_VTABLE IViewObjectExImpl 
   : public IViewObjectEx
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `IViewObjectExImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IViewObjectExImpl::Draw](#draw)|Rysuje reprezentację formant na kontekst urządzenia.|
|[IViewObjectExImpl::Freeze](#freeze)|Zawiesza się rysowane reprezentacja kontrolki, dzięki czemu nie zmienią się do `Unfreeze`. Implementacja biblioteki ATL zwraca E_NOTIMPL.|
|[IViewObjectExImpl::GetAdvise](#getadvise)|Pobiera istniejącego połączenia doradztwa technicznego dotyczącego obiektu sink w kontrolce, jeśli taka istnieje.|
|[IViewObjectExImpl::GetColorSet](#getcolorset)|Zwraca wartość logiczną paletę używanych przez kontrolkę na rysunku. Implementacja biblioteki ATL zwraca E_NOTIMPL.|
|[IViewObjectExImpl::GetExtent](#getextent)|Pobiera rozmiar wyświetlania kontrolki w jednostkach HIMETRIC (0,01 milimetra na jednostkę) z składowa danych klasy kontrolki [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).|
|[IViewObjectExImpl::GetNaturalExtent](#getnaturalextent)|Dostarcza wskazówek zmiany rozmiaru z kontenera dla obiektu do wykorzystania jako użytkownik zmienia jego rozmiar.|
|[IViewObjectExImpl::GetRect](#getrect)|Zwraca prostokąt opisujący żądany aspekt rysowania. Implementacja biblioteki ATL zwraca E_NOTIMPL.|
|[IViewObjectExImpl::GetViewStatus](#getviewstatus)|Zwraca informacje dotyczące przezroczystości obiektu oraz obsługiwanych aspektów rysujących.|
|[IViewObjectExImpl::QueryHitPoint](#queryhitpoint)|Sprawdza, czy określony punkt znajduje się w prostokącie określonego i zwraca [HITRESULT](/windows/desktop/api/ocidl/ne-ocidl-taghitresult) wartość w `pHitResult`.|
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|Sprawdza, czy prostokącie wyświetlania kontrolki nakłada się w dowolnym momencie w prostokącie określonej lokalizacji i zwraca wartość HITRESULT w `pHitResult`.|
|[IViewObjectExImpl::SetAdvise](#setadvise)|Konfiguruje połączenia między formantem i ujścia Porada, więc ujścia może zostać poinformowany o zmianach wprowadzonych w widoku formantu.|
|[IViewObjectExImpl::Unfreeze](#unfreeze)|Unfreezes rysowane reprezentacja formantu. Implementacja biblioteki ATL zwraca E_NOTIMPL.|

## <a name="remarks"></a>Uwagi

[IViewObject](/windows/desktop/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/desktop/api/oleidl/nn-oleidl-iviewobject2), i [IViewObjectEx](/windows/desktop/api/ocidl/nn-ocidl-iviewobjectex) interfejsy umożliwiają kontrolkę do wyświetlania się bezpośrednio, a także tworzyć i zarządzać ujścia Porada do powiadamiania kontener zmiany sposobu wyświetlania kontrolki. `IViewObjectEx` Interfejs zapewnia obsługę funkcji rozszerzonej kontroli, takich jak rysowanie pozbawionej migotania, formanty innych niż prostokątne i przejrzystości i testowanie trafień (na przykład, jak blisko kliknięcie myszą musi być wziąć pod uwagę w kontrolce). Klasa `IViewObjectExImpl` udostępnia domyślną implementację tych interfejsów i implementuje `IUnknown` , wysyłając informacje o do zrzutu kompilacji urządzenia podczas debugowania.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IViewObjectEx`

`IViewObjectExImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

##  <a name="draw"></a>  IViewObjectExImpl::Draw

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

Ta metoda wywołuje `CComControl::OnDrawAdvanced` który z kolei wywołuje Twojej klasy kontrolki `OnDraw` metody. `OnDraw` Metody jest automatycznie dodawany do klasy kontrolki, po utworzeniu kontrolki za pomocą Kreatora formantu biblioteki ATL. Domyślne kreatora `OnDraw` rysuje prostokąt z etykietą "ATL 3.0".

Zobacz [IViewObject::Draw](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-draw) w Windows SDK.

##  <a name="freeze"></a>  IViewObjectExImpl::Freeze

Zawiesza się rysowane reprezentacja kontrolki, dzięki czemu nie zmienią się do `Unfreeze`. Implementacja biblioteki ATL zwraca E_NOTIMPL.

```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```

### <a name="remarks"></a>Uwagi

Zobacz [IViewObject::Freeze](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-freeze) w Windows SDK.

##  <a name="getadvise"></a>  IViewObjectExImpl::GetAdvise

Pobiera istniejącego połączenia doradztwa technicznego dotyczącego obiektu sink w kontrolce, jeśli taka istnieje.

```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```

### <a name="remarks"></a>Uwagi

Poradnik ujścia jest przechowywany w składowa danych klasy kontrolki [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink).

Zobacz [IViewObject::GetAdvise](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-getadvise) w Windows SDK.

##  <a name="getcolorset"></a>  IViewObjectExImpl::GetColorSet

Zwraca wartość logiczną paletę używanych przez kontrolkę na rysunku. Implementacja biblioteki ATL zwraca E_NOTIMPL.

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

Zobacz [IViewObject::GetColorSet](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-getcolorset) w Windows SDK.

##  <a name="getextent"></a>  IViewObjectExImpl::GetExtent

Pobiera rozmiar wyświetlania kontrolki w jednostkach HIMETRIC (0,01 milimetra na jednostkę) z składowa danych klasy kontrolki [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).

```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```

### <a name="remarks"></a>Uwagi

Zobacz [IViewObject2::GetExtent](/windows/desktop/api/oleidl/nf-oleidl-iviewobject2-getextent) w Windows SDK.

##  <a name="getnaturalextent"></a>  IViewObjectExImpl::GetNaturalExtent

Dostarcza wskazówek zmiany rozmiaru z kontenera dla obiektu do wykorzystania jako użytkownik zmienia jego rozmiar.

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

Jeśli `dwAspect` jest DVASPECT_CONTENT i *pExtentInfo -> dwExtentMode* jest DVEXTENT_CONTENT, ustawia * `psizel` do klasy formantu element członkowski danych [CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural). W przeciwnym razie zwraca błąd HRESULT.

Zobacz [IViewObjectEx::GetNaturalExtent](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-getnaturalextent) w Windows SDK.

##  <a name="getrect"></a>  IViewObjectExImpl::GetRect

Zwraca prostokąt opisujący żądany aspekt rysowania. Implementacja biblioteki ATL zwraca E_NOTIMPL.

```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```

### <a name="remarks"></a>Uwagi

Zobacz [IViewObjectEx::GetRect](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-getrect) w Windows SDK.

##  <a name="getviewstatus"></a>  IViewObjectExImpl::GetViewStatus

Zwraca informacje dotyczące przezroczystości obiektu oraz obsługiwanych aspektów rysujących.

```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```

### <a name="remarks"></a>Uwagi

Domyślnie ustawia ATL `pdwStatus` do wskazania, że są obsługiwane przez kontrolkę VIEWSTATUS_OPAQUE (możliwe wartości to w [stan](/windows/desktop/api/ocidl/ne-ocidl-tagviewstatus) wyliczenia).

Zobacz [IViewObjectEx::GetViewStatus](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-getviewstatus) w Windows SDK.

##  <a name="queryhitpoint"></a>  IViewObjectExImpl::QueryHitPoint

Sprawdza, czy określony punkt znajduje się w prostokącie określonego i zwraca [HITRESULT](/windows/desktop/api/ocidl/ne-ocidl-taghitresult) wartość w `pHitResult`.

```
STDMETHOD(QueryHitPoint)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    POINT ptlLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>Uwagi

Wartość może być HITRESULT_HIT lub HITRESULT_OUTSIDE.

Jeśli `dwAspect` jest równa [DVASPECT_CONTENT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect), metoda zwraca wartość S_OK. W przeciwnym razie metoda zwraca E_FAIL.

Zobacz [IViewObjectEx::QueryHitPoint](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-queryhitpoint) w Windows SDK.

##  <a name="queryhitrect"></a>  IViewObjectExImpl::QueryHitRect

Sprawdza, czy prostokącie wyświetlania kontrolki nakłada się w dowolnym momencie w prostokącie określonej lokalizacji i zwraca [HITRESULT](/windows/desktop/api/ocidl/ne-ocidl-taghitresult) wartość w `pHitResult`.

```
STDMETHOD(QueryHitRect)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    LPRECT prcLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>Uwagi

Wartość może być HITRESULT_HIT lub HITRESULT_OUTSIDE.

Jeśli `dwAspect` jest równa [DVASPECT_CONTENT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect), metoda zwraca wartość S_OK. W przeciwnym razie metoda zwraca E_FAIL.

Zobacz [IViewObjectEx::QueryHitRect](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-queryhitrect) w Windows SDK.

##  <a name="setadvise"></a>  IViewObjectExImpl::SetAdvise

Konfiguruje połączenia między formantem i ujścia Porada, więc ujścia może zostać poinformowany o zmianach wprowadzonych w widoku formantu.

```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```

### <a name="remarks"></a>Uwagi

Wskaźnik do [IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink) interfejsu na obiekt sink Porada są przechowywane w składowej danych klasy kontrolki [CComControlBase::m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink).  

Zobacz [IViewObject::SetAdvise](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-setadvise) w Windows SDK.

##  <a name="unfreeze"></a>  IViewObjectExImpl::Unfreeze

Unfreezes rysowane reprezentacja formantu. Implementacja biblioteki ATL zwraca E_NOTIMPL.

```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```

### <a name="remarks"></a>Uwagi

Zobacz [IViewObject::Unfreeze](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-unfreeze) w Windows SDK.

##  <a name="closehandle"></a>  IWorkerThreadClient::CloseHandle

Zaimplementuj tę metodę, aby zamknąć dojście skojarzone z tym obiektem.

```
HRESULT CloseHandle(HANDLE hHandle);
```

### <a name="parameters"></a>Parametry

*hHandle*<br/>
Uchwyt zostanie zamknięty.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na powodzenie lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Dojście przekazane do tej metody był wcześniej skojarzony z tym obiektem przez wywołanie [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Przykład

Poniższy kod przedstawia proste wdrażanie `IWorkerThreadClient::CloseHandle`.

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]

##  <a name="execute"></a>  IWorkerThreadClient::Execute

Zaimplementuj tę metodę w celu wykonania kodu, gdy staje się sygnalizowane uchwyt skojarzone z tym obiektem.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>Parametry

*dwParam*<br/>
Parametr użytkownika.

*hObject*<br/>
Uchwyt, który ma być sygnalizowane.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na powodzenie lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Dojście i przekazany do tej metody na wskaźnik typu DWORD były wcześniej skojarzone z tego obiektu przez wywołanie [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Przykład

Poniższy kod przedstawia proste wdrażanie `IWorkerThreadClient::Execute`.

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Interfejsy kontrolki ActiveX](/windows/desktop/com/activex-controls-interfaces)<br/>
[Samouczek](../../atl/active-template-library-atl-tutorial.md)<br/>
[Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
