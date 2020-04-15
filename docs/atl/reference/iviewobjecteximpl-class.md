---
title: Klasa IViewObjectExImpl
ms.date: 11/04/2016
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
helpviewer_keywords:
- ActiveX controls [C++], drawing
- IViewObjectEx ATL implementation
- advise sinks
- IViewObjectExImpl class
ms.assetid: ad6de760-1ee5-4883-b033-ae57beffc369
ms.openlocfilehash: 59c5657dcd892544f7e790b52325cb9ecba0dd56
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326343"
---
# <a name="iviewobjecteximpl-class"></a>Klasa IViewObjectExImpl

Ta klasa `IUnknown` implementuje i udostępnia domyślne implementacje interfejsów [IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)i [IViewObjectEx.](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex)

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class ATL_NO_VTABLE IViewObjectExImpl
   : public IViewObjectEx
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa, pochodząca od `IViewObjectExImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IViewObjectExImpl::Draw](#draw)|Rysuje reprezentację formantu w kontekście urządzenia.|
|[IViewObjectExImpl::Freeze](#freeze)|Zawiesza narysowaną reprezentację formantu, aby nie `Unfreeze`zmieniał się do momentu. Implementacja ATL zwraca E_NOTIMPL.|
|[IViewObjectExImpl::GetAdvise](#getadvise)|Pobiera istniejące połączenie ujścia doradczego na formancie, jeśli istnieje.|
|[IViewObjectExImpl::GetColorSet](#getcolorset)|Zwraca paletę logiczną używaną przez formant do rysowania. Implementacja ATL zwraca E_NOTIMPL.|
|[IViewObjectExImpImpl::GetExtent](#getextent)|Pobiera rozmiar wyświetlania formantu w jednostkach HIMETRIC (0,01 milimetra na jednostkę) z elementu danych klasy kontrolnej [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).|
|[IViewObjectExImpl::GetNaturalExtent](#getnaturalextent)|Zawiera wskazówki dotyczące rozmiaru z kontenera dla obiektu do użycia, gdy użytkownik go zmienić rozmiar.|
|[IViewObjectExImpl::GetRect](#getrect)|Zwraca prostokąt opisujący żądany aspekt rysunku. Implementacja ATL zwraca E_NOTIMPL.|
|[IViewObjectExImpl::GetViewStatus](#getviewstatus)|Zwraca informacje o krycie obiektu i jakie aspekty rysunku są obsługiwane.|
|[IViewObjectExImpl::QueryHitPoint](#queryhitpoint)|Sprawdza, czy określony punkt znajduje się w określonym prostokącie `pHitResult`i zwraca wartość [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) w pliku .|
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|Sprawdza, czy prostokąt wyświetlania formantu nakłada się na dowolny punkt w określonym prostokącie lokalizacji i zwraca wartość HITRESULT w `pHitResult`pliku .|
|[IViewObjectExImpl::SetAdvise](#setadvise)|Konfiguruje połączenie między formantem a doradzić sink więc ujście można powiadomić o zmianach w widoku formantu.|
|[IViewObjectExImpl::Odblokuj](#unfreeze)|Odmrożenia narysowanej reprezentacji formantu. Implementacja ATL zwraca E_NOTIMPL.|

## <a name="remarks"></a>Uwagi

Interfejsy [IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)i [IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex) umożliwiają formantowi wyświetlanie się bezpośrednio oraz tworzenie i zarządzanie doradzić zlewu, aby powiadomić kontener o zmianach na ekranie sterowania. Interfejs `IViewObjectEx` zapewnia obsługę rozszerzonych funkcji sterowania, takich jak rysowanie bez migotania, nie prostokątne i przezroczyste formanty oraz testowanie trafień (na przykład, jak blisko kliknięcia myszą należy wziąć pod uwagę w formancie). Klasa `IViewObjectExImpl` zapewnia domyślną implementację tych `IUnknown` interfejsów i implementuje przez wysyłanie informacji do urządzenia zrzutu w kompilacjach debugowania.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IViewObjectEx`

`IViewObjectExImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

## <a name="iviewobjecteximpldraw"></a><a name="draw"></a>IViewObjectExImpl::Draw

Rysuje reprezentację formantu w kontekście urządzenia.

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

Ta metoda `CComControl::OnDrawAdvanced` wywołuje, co z kolei `OnDraw` wywołuje metodę klasy kontroli. Metoda `OnDraw` jest automatycznie dodawana do klasy sterowania podczas tworzenia formantu za pomocą Kreatora sterowania ATL. Domyślnie `OnDraw` Kreator rysuje prostokąt z etykietą "ATL 3.0".

Zobacz [IViewObject::Draw](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw) w windows SDK.

## <a name="iviewobjecteximplfreeze"></a><a name="freeze"></a>IViewObjectExImpl::Freeze

Zawiesza narysowaną reprezentację formantu, aby nie `Unfreeze`zmieniał się do momentu. Implementacja ATL zwraca E_NOTIMPL.

```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```

### <a name="remarks"></a>Uwagi

Zobacz [IViewObject::Freeze](/windows/win32/api/oleidl/nf-oleidl-iviewobject-freeze) w windows SDK.

## <a name="iviewobjecteximplgetadvise"></a><a name="getadvise"></a>IViewObjectExImpl::GetAdvise

Pobiera istniejące połączenie ujścia doradczego na formancie, jeśli istnieje.

```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```

### <a name="remarks"></a>Uwagi

Ujście doradcze jest przechowywane w elementów członkowskich danych klasy kontrolnej [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink).

Zobacz [IViewObject::GetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getadvise) w windows SDK.

## <a name="iviewobjecteximplgetcolorset"></a><a name="getcolorset"></a>IViewObjectExImpl::GetColorSet

Zwraca paletę logiczną używaną przez formant do rysowania. Implementacja ATL zwraca E_NOTIMPL.

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

Zobacz [IViewObject::GetColorSet](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getcolorset) w zestawie Windows SDK.

## <a name="iviewobjecteximplgetextent"></a><a name="getextent"></a>IViewObjectExImpImpl::GetExtent

Pobiera rozmiar wyświetlania formantu w jednostkach HIMETRIC (0,01 milimetra na jednostkę) z elementu danych klasy kontrolnej [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).

```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```

### <a name="remarks"></a>Uwagi

Zobacz [IViewObject2::GetExtent](/windows/win32/api/oleidl/nf-oleidl-iviewobject2-getextent) w windows SDK.

## <a name="iviewobjecteximplgetnaturalextent"></a><a name="getnaturalextent"></a>IViewObjectExImpl::GetNaturalExtent

Zawiera wskazówki dotyczące rozmiaru z kontenera dla obiektu do użycia, gdy użytkownik go zmienić rozmiar.

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

Jeśli `dwAspect` jest DVASPECT_CONTENT i *pExtentInfo->dwExtentMode* jest DVEXTENT_CONTENT, ustawia `psizel` * do elementu członkowskiego danych klasy kontrolnej [CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural). W przeciwnym razie zwraca błąd HRESULT.

Zobacz [IViewObjectEx::GetNaturalExtent](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getnaturalextent) w windows SDK.

## <a name="iviewobjecteximplgetrect"></a><a name="getrect"></a>IViewObjectExImpl::GetRect

Zwraca prostokąt opisujący żądany aspekt rysunku. Implementacja ATL zwraca E_NOTIMPL.

```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```

### <a name="remarks"></a>Uwagi

Zobacz [IViewObjectEx::GetRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getrect) w windows SDK.

## <a name="iviewobjecteximplgetviewstatus"></a><a name="getviewstatus"></a>IViewObjectExImpl::GetViewStatus

Zwraca informacje o krycie obiektu i jakie aspekty rysunku są obsługiwane.

```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```

### <a name="remarks"></a>Uwagi

Domyślnie ATL `pdwStatus` ustawia, aby wskazać, że formant obsługuje VIEWSTATUS_OPAQUE (możliwe wartości znajdują się w [wyliczeniu VIEWSTATUS).](/windows/win32/api/ocidl/ne-ocidl-viewstatus)

Zobacz [IViewObjectEx::GetViewStatus](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getviewstatus) w zestawie Windows SDK.

## <a name="iviewobjecteximplqueryhitpoint"></a><a name="queryhitpoint"></a>IViewObjectExImpl::QueryHitPoint

Sprawdza, czy określony punkt znajduje się w określonym prostokącie `pHitResult`i zwraca wartość [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) w pliku .

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

Jeśli `dwAspect` [jest równa DVASPECT_CONTENT,](/windows/win32/api/wtypes/ne-wtypes-dvaspect)metoda zwraca S_OK. W przeciwnym razie metoda zwraca E_FAIL.

Zobacz [IViewObjectEx::QueryHitPoint](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitpoint) w windows SDK.

## <a name="iviewobjecteximplqueryhitrect"></a><a name="queryhitrect"></a>IViewObjectExImpl::QueryHitRect

Sprawdza, czy prostokąt wyświetlania formantu nakłada się na dowolny punkt w określonym prostokącie lokalizacji i zwraca wartość [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) w `pHitResult`pliku .

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

Jeśli `dwAspect` [jest równa DVASPECT_CONTENT,](/windows/win32/api/wtypes/ne-wtypes-dvaspect)metoda zwraca S_OK. W przeciwnym razie metoda zwraca E_FAIL.

Zobacz [IViewObjectEx::QueryHitRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitrect) w windows SDK.

## <a name="iviewobjecteximplsetadvise"></a><a name="setadvise"></a>IViewObjectExImpl::SetAdvise

Konfiguruje połączenie między formantem a doradzić sink więc ujście można powiadomić o zmianach w widoku formantu.

```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```

### <a name="remarks"></a>Uwagi

Wskaźnik do interfejsu [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) na zlewie doradzania jest przechowywany w elementów członkowskich danych klasy kontrolnej [CComControlBase::m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink).

Zobacz [IViewObject::SetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-setadvise) w zestawie Windows SDK.

## <a name="iviewobjecteximplunfreeze"></a><a name="unfreeze"></a>IViewObjectExImpl::Odblokuj

Odmrożenia narysowanej reprezentacji formantu. Implementacja ATL zwraca E_NOTIMPL.

```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```

### <a name="remarks"></a>Uwagi

Zobacz [IViewObject::Odblokowuj](/windows/win32/api/oleidl/nf-oleidl-iviewobject-unfreeze) w windows SDK.

## <a name="iworkerthreadclientclosehandle"></a><a name="closehandle"></a>IWorkerThreadClient::Zamknijhandle

Zaimplementuj tę metodę, aby zamknąć dojście skojarzone z tym obiektem.

```
HRESULT CloseHandle(HANDLE hHandle);
```

### <a name="parameters"></a>Parametry

*hRejsz*<br/>
Uchwyt do zamknięcia.

### <a name="return-value"></a>Wartość zwracana

Powrót S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Dojście przekazane do tej metody zostało wcześniej skojarzone z tym obiektem przez wywołanie [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Przykład

Poniższy kod przedstawia prostą implementację programu `IWorkerThreadClient::CloseHandle`.

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]

## <a name="iworkerthreadclientexecute"></a><a name="execute"></a>IWorkerThreadClient::Wykonaj

Zaimplementuj tę metodę, aby wykonać kod, gdy dojście skojarzone z tym obiektem staje się sygnalizowane.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>Parametry

*dwParam (polski)*<br/>
Parametr użytkownika.

*hObiekt*<br/>
Uchwyt, który stał się sygnalizowany.

### <a name="return-value"></a>Wartość zwracana

Powrót S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Dojście i DWORD/pointer przekazane do tej metody były wcześniej skojarzone z tym obiektem przez wywołanie [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Przykład

Poniższy kod przedstawia prostą implementację programu `IWorkerThreadClient::Execute`.

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Interfejsy sterowania ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Samouczek](../../atl/active-template-library-atl-tutorial.md)<br/>
[Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
