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
ms.openlocfilehash: 3aead41f317d175eac9dcb094aa2070d82dc6185
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495499"
---
# <a name="iviewobjecteximpl-class"></a>Klasa IViewObjectExImpl

Ta klasa implementuje `IUnknown` i udostępnia domyślne implementacje interfejsów [IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)i [IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex) .

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class ATL_NO_VTABLE IViewObjectExImpl
   : public IViewObjectEx
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, która pochodzi od `IViewObjectExImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IViewObjectExImpl::D RAW](#draw)|Rysuje reprezentację formantu do kontekstu urządzenia.|
|[IViewObjectExImpl:: Zablokuj](#freeze)|Blokuje narysowanej reprezentację kontrolki, aby nie zmieniła `Unfreeze`się do. Implementacja ATL zwraca E_NOTIMPL.|
|[IViewObjectExImpl:: GetAdvise](#getadvise)|Pobiera istniejące, doradcze połączenie ujścia w kontrolce, jeśli istnieje.|
|[IViewObjectExImpl::GetColorSet](#getcolorset)|Zwraca paletę logiczną używaną przez formant do rysowania. Implementacja ATL zwraca E_NOTIMPL.|
|[IViewObjectExImpl:: getzakres](#getextent)|Pobiera rozmiar wyświetlania kontrolki w jednostkach HIMETRIC (0,01 milimetr na jednostkę) z elementu członkowskiego danych klasy sterowania [CComControlBase:: m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).|
|[IViewObjectExImpl::GetNaturalExtent](#getnaturalextent)|Zapewnia wskazówki dotyczące ustalania rozmiaru z kontenera dla obiektu, który ma być używany, gdy użytkownik zmienia jego rozmiar.|
|[IViewObjectExImpl:: getRect](#getrect)|Zwraca prostokąt opisujący żądany aspekt rysowania. Implementacja ATL zwraca E_NOTIMPL.|
|[IViewObjectExImpl::GetViewStatus](#getviewstatus)|Zwraca informacje o nieprzezroczystości obiektu oraz o tym, jakie aspekty rysowania są obsługiwane.|
|[IViewObjectExImpl::QueryHitPoint](#queryhitpoint)|Sprawdza, czy określony punkt znajduje się w określonym prostokącie i zwraca wartość [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) w `pHitResult`elemencie.|
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|Sprawdza, czy prostokąt wyświetlania kontrolki nakłada się na wszystkie punkty w określonym prostokącie lokalizacji i zwraca wartość HITRESULT w `pHitResult`.|
|[IViewObjectExImpl:: SetAdvise](#setadvise)|Konfiguruje połączenie między formantem a obiektem powiadamiającym, dzięki czemu można powiadomić ujścia o zmianach w widoku kontrolki.|
|[IViewObjectExImpl::Unfreeze](#unfreeze)|Odblokowuje narysowanej reprezentację formantu. Implementacja ATL zwraca E_NOTIMPL.|

## <a name="remarks"></a>Uwagi

Interfejsy [IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)i [IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex) umożliwiają kontrolce wyświetlanie samego siebie bezpośrednio oraz tworzenie i zarządzanie ujściam doradzania w celu powiadomienia kontenera zmian w formancie. `IViewObjectEx` Interfejs zapewnia obsługę funkcji rozszerzonej kontroli, takich jak rysowanie bez migotania, kontrolki nieprostokątne i przezroczyste oraz testy trafień (na przykład jak blisko kliknięcia myszą należy wziąć pod uwagę w formancie). Klasa `IViewObjectExImpl` udostępnia domyślną implementację tych interfejsów i implementuje `IUnknown` przez wysyłanie informacji do urządzenia zrzutu w kompilacjach debugowania.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IViewObjectEx`

`IViewObjectExImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl. h

##  <a name="draw"></a>IViewObjectExImpl::D RAW

Rysuje reprezentację formantu do kontekstu urządzenia.

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

Ta metoda wywołuje `CComControl::OnDrawAdvanced` , która z kolei wywołuje `OnDraw` metodę klasy formantu. `OnDraw` Metoda jest automatycznie dodawana do klasy formantów podczas tworzenia kontrolki za pomocą Kreatora kontrolki ATL. Domyślny `OnDraw` Kreator rysuje prostokąt z etykietą "ATL 3,0".

Zobacz [Widok IViewObject::D RAW](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw) w Windows SDK.

##  <a name="freeze"></a>IViewObjectExImpl:: Zablokuj

Blokuje narysowanej reprezentację kontrolki, aby nie zmieniła `Unfreeze`się do. Implementacja ATL zwraca E_NOTIMPL.

```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```

### <a name="remarks"></a>Uwagi

Zobacz [Widok IViewObject::](/windows/win32/api/oleidl/nf-oleidl-iviewobject-freeze) Zablokuj w Windows SDK.

##  <a name="getadvise"></a>IViewObjectExImpl:: GetAdvise

Pobiera istniejące, doradcze połączenie ujścia w kontrolce, jeśli istnieje.

```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```

### <a name="remarks"></a>Uwagi

Obiekt sink doradcy jest przechowywany w elemencie członkowskim danych klasy sterowania [CComControlBase:: m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink).

Zobacz [Widok IViewObject:: GetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getadvise) w Windows SDK.

##  <a name="getcolorset"></a>IViewObjectExImpl::GetColorSet

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

Zobacz [Widok IViewObject:: GetColorSet](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getcolorset) w Windows SDK.

##  <a name="getextent"></a>IViewObjectExImpl:: getzakres

Pobiera rozmiar wyświetlania kontrolki w jednostkach HIMETRIC (0,01 milimetr na jednostkę) z elementu członkowskiego danych klasy sterowania [CComControlBase:: m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).

```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```

### <a name="remarks"></a>Uwagi

Zobacz [IViewObject2:: getzakres](/windows/win32/api/oleidl/nf-oleidl-iviewobject2-getextent) w Windows SDK.

##  <a name="getnaturalextent"></a>IViewObjectExImpl::GetNaturalExtent

Zapewnia wskazówki dotyczące ustalania rozmiaru z kontenera dla obiektu, który ma być używany, gdy użytkownik zmienia jego rozmiar.

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

Jeśli `dwAspect` jest DVASPECT_CONTENT i *pExtentInfo-> dwExtentMode* to DVEXTENT_CONTENT, ustawia * `psizel` do elementu członkowskiego danych klasy kontroli [CComControlBase:: m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural). W przeciwnym razie zwraca błąd HRESULT.

Zobacz [IViewObjectEx:: GetNaturalExtent](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getnaturalextent) w Windows SDK.

##  <a name="getrect"></a>IViewObjectExImpl:: getRect

Zwraca prostokąt opisujący żądany aspekt rysowania. Implementacja ATL zwraca E_NOTIMPL.

```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```

### <a name="remarks"></a>Uwagi

Zobacz [IViewObjectEx:: getRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getrect) w Windows SDK.

##  <a name="getviewstatus"></a>IViewObjectExImpl::GetViewStatus

Zwraca informacje o nieprzezroczystości obiektu oraz o tym, jakie aspekty rysowania są obsługiwane.

```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```

### <a name="remarks"></a>Uwagi

Domyślnie zestawy `pdwStatus` ATL wskazują, że kontrolka obsługuje VIEWSTATUS_OPAQUE (możliwe wartości są w wyliczeniu [podwójne](/windows/win32/api/ocidl/ne-ocidl-viewstatus) ).

Zobacz [IViewObjectEx:: GetViewStatus](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getviewstatus) w Windows SDK.

##  <a name="queryhitpoint"></a>IViewObjectExImpl::QueryHitPoint

Sprawdza, czy określony punkt znajduje się w określonym prostokącie i zwraca wartość [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) w `pHitResult`elemencie.

```
STDMETHOD(QueryHitPoint)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    POINT ptlLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>Uwagi

Wartość może być równa HITRESULT_HIT lub HITRESULT_OUTSIDE.

Jeśli `dwAspect` jest równa [DVASPECT_CONTENT](/windows/win32/api/wtypes/ne-wtypes-dvaspect), metoda zwraca S_OK. W przeciwnym razie metoda zwraca wartość E_FAIL.

Zobacz [IViewObjectEx:: QueryHitPoint](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitpoint) w Windows SDK.

##  <a name="queryhitrect"></a>IViewObjectExImpl::QueryHitRect

Sprawdza, czy prostokąt wyświetlania kontrolki nakłada się na wszystkie punkty w określonym prostokącie lokalizacji i zwraca wartość [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) w `pHitResult`.

```
STDMETHOD(QueryHitRect)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    LPRECT prcLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>Uwagi

Wartość może być równa HITRESULT_HIT lub HITRESULT_OUTSIDE.

Jeśli `dwAspect` jest równa [DVASPECT_CONTENT](/windows/win32/api/wtypes/ne-wtypes-dvaspect), metoda zwraca S_OK. W przeciwnym razie metoda zwraca wartość E_FAIL.

Zobacz [IViewObjectEx:: QueryHitRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitrect) w Windows SDK.

##  <a name="setadvise"></a>IViewObjectExImpl:: SetAdvise

Konfiguruje połączenie między formantem a obiektem powiadamiającym, dzięki czemu można powiadomić ujścia o zmianach w widoku kontrolki.

```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```

### <a name="remarks"></a>Uwagi

Wskaźnik do interfejsu [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) w ujściach doradzania jest przechowywany w klasie danych klasy sterowania [CComControlBase:: m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink).

Zobacz [Widok IViewObject:: SetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-setadvise) w Windows SDK.

##  <a name="unfreeze"></a>IViewObjectExImpl:: unfree

Odblokowuje narysowanej reprezentację formantu. Implementacja ATL zwraca E_NOTIMPL.

```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```

### <a name="remarks"></a>Uwagi

Zobacz [Widok IViewObject:: unfree](/windows/win32/api/oleidl/nf-oleidl-iviewobject-unfreeze) in Windows SDK.

##  <a name="closehandle"></a>IWorkerThreadClient:: CloseHandle

Zaimplementuj tę metodę, aby zamknąć dojście skojarzone z tym obiektem.

```
HRESULT CloseHandle(HANDLE hHandle);
```

### <a name="parameters"></a>Parametry

*hHandle*<br/>
Uchwyt, który ma zostać zamknięty.

### <a name="return-value"></a>Wartość zwracana

Zwróć S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Dojście przesłane do tej metody zostało wcześniej skojarzone z tym obiektem przez wywołanie [CWorkerThread:: AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Przykład

Poniższy kod pokazuje prostą implementację programu `IWorkerThreadClient::CloseHandle`.

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]

##  <a name="execute"></a>IWorkerThreadClient:: Execute

Zaimplementuj tę metodę, aby wykonać kod, gdy dojście skojarzone z tym obiektem zostanie zasygnalizowane.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>Parametry

*dwParam*<br/>
Parametr użytkownika.

*hObject*<br/>
Uchwyt, który został zasygnalizowani.

### <a name="return-value"></a>Wartość zwracana

Zwróć S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Dojście i wskaźnik DWORD przekazano do tej metody, które zostały wcześniej skojarzone z tym obiektem przez wywołanie [CWorkerThread:: AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Przykład

Poniższy kod pokazuje prostą implementację programu `IWorkerThreadClient::Execute`.

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]

## <a name="see-also"></a>Zobacz także

[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Interfejsy formantów ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Samouczek](../../atl/active-template-library-atl-tutorial.md)<br/>
[Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
