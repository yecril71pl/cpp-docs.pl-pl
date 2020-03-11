---
title: Klasa IPropertyPageImpl
ms.date: 11/04/2016
f1_keywords:
- IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl::IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl::Activate
- ATLCTL/ATL::IPropertyPageImpl::Apply
- ATLCTL/ATL::IPropertyPageImpl::Deactivate
- ATLCTL/ATL::IPropertyPageImpl::GetPageInfo
- ATLCTL/ATL::IPropertyPageImpl::Help
- ATLCTL/ATL::IPropertyPageImpl::IsPageDirty
- ATLCTL/ATL::IPropertyPageImpl::Move
- ATLCTL/ATL::IPropertyPageImpl::SetDirty
- ATLCTL/ATL::IPropertyPageImpl::SetObjects
- ATLCTL/ATL::IPropertyPageImpl::SetPageSite
- ATLCTL/ATL::IPropertyPageImpl::Show
- ATLCTL/ATL::IPropertyPageImpl::TranslateAccelerator
- ATLCTL/ATL::IPropertyPageImpl::m_bDirty
- ATLCTL/ATL::IPropertyPageImpl::m_dwDocString
- ATLCTL/ATL::IPropertyPageImpl::m_dwHelpContext
- ATLCTL/ATL::IPropertyPageImpl::m_dwHelpFile
- ATLCTL/ATL::IPropertyPageImpl::m_dwTitle
- ATLCTL/ATL::IPropertyPageImpl::m_nObjects
- ATLCTL/ATL::IPropertyPageImpl::m_pPageSite
- ATLCTL/ATL::IPropertyPageImpl::m_ppUnk
- ATLCTL/ATL::IPropertyPageImpl::m_size
helpviewer_keywords:
- property pages
- IPropertyPage ATL implementation
- IPropertyPageImpl class
ms.assetid: f9b7c8b1-7a04-4eab-aa63-63efddb740fa
ms.openlocfilehash: 69842e77aecaa94be66432e5fbba437a6fa3c5a4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864986"
---
# <a name="ipropertypageimpl-class"></a>Klasa IPropertyPageImpl

Ta klasa implementuje `IUnknown` i udostępnia domyślną implementację interfejsu [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) .

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class IPropertyPageImpl
```

#### <a name="parameters"></a>Parametry

*&*<br/>
Klasa, która pochodzi od `IPropertyPageImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IPropertyPageImpl::IPropertyPageImpl](#ipropertypageimpl)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IPropertyPageImpl:: Activate](#activate)|Tworzy okno dialogowe dla strony właściwości.|
|[IPropertyPageImpl:: Apply](#apply)|Stosuje bieżące wartości strony właściwości do obiektów podstawowych określonych za pomocą `SetObjects`. Implementacja ATL zwraca S_OK.|
|[IPropertyPageImpl::D eactivate](#deactivate)|Niszczy okno utworzone za pomocą `Activate`.|
|[IPropertyPageImpl::GetPageInfo](#getpageinfo)|Pobiera informacje o stronie właściwości.|
|[IPropertyPageImpl:: help](#help)|Wywołuje Pomoc systemu Windows dla strony właściwości.|
|[IPropertyPageImpl::IsPageDirty](#ispagedirty)|Wskazuje, czy strona właściwości została zmieniona od czasu jej aktywacji.|
|[IPropertyPageImpl:: Move](#move)|Położenie i rozmiar okna dialogowego strony właściwości.|
|[IPropertyPageImpl:: SetDirty](#setdirty)|Flaguje stan strony właściwości jako zmieniony lub niezmieniony.|
|[IPropertyPageImpl:: SetObjects](#setobjects)|Dostarcza tablicę wskaźników `IUnknown` dla obiektów skojarzonych ze stroną właściwości. Te obiekty otrzymują bieżące wartości strony właściwości za pomocą wywołania do `Apply`.|
|[IPropertyPageImpl::SetPageSite](#setpagesite)|Udostępnia stronę właściwości ze wskaźnikiem `IPropertyPageSite`, za pomocą którego strona właściwości komunikuje się z ramką właściwości.|
|[IPropertyPageImpl:: show](#show)|Sprawia, że okno dialogowe strony właściwości jest widoczne lub niewidoczne.|
|[IPropertyPageImpl::TranslateAccelerator](#translateaccelerator)|Przetwarza określone naciśnięcie klawisza.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[IPropertyPageImpl:: m_bDirty](#m_bdirty)|Określa, czy stan strony właściwości został zmieniony.|
|[IPropertyPageImpl:: m_dwDocString](#m_dwdocstring)|Przechowuje identyfikator zasobu skojarzony z ciągiem tekstowym opisującym stronę właściwości.|
|[IPropertyPageImpl:: m_dwHelpContext](#m_dwhelpcontext)|Przechowuje identyfikator kontekstu dla tematu pomocy skojarzonego ze stroną właściwości.|
|[IPropertyPageImpl:: m_dwHelpFile](#m_dwhelpfile)|Przechowuje identyfikator zasobu skojarzony z nazwą pliku pomocy opisującego stronę właściwości.|
|[IPropertyPageImpl:: m_dwTitle](#m_dwtitle)|Przechowuje identyfikator zasobu skojarzony z ciągiem tekstowym, który pojawia się na karcie strony właściwości.|
|[IPropertyPageImpl:: m_nObjects](#m_nobjects)|Przechowuje liczbę obiektów skojarzonych ze stroną właściwości.|
|[IPropertyPageImpl:: m_pPageSite](#m_ppagesite)|Wskazuje interfejs `IPropertyPageSite`, za pomocą którego strona właściwości komunikuje się z ramką właściwości.|
|[IPropertyPageImpl:: m_ppUnk](#m_ppunk)|Wskazuje tablicę `IUnknown` wskaźników do obiektów skojarzonych ze stroną właściwości.|
|[IPropertyPageImpl:: m_size](#m_size)|Przechowuje wysokość i szerokość okna dialogowego strony właściwości (w pikselach).|

## <a name="remarks"></a>Uwagi

Interfejs [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) umożliwia obiektowi zarządzanie określoną stroną właściwości w arkuszu właściwości. `IPropertyPageImpl` klasy zapewnia domyślną implementację tego interfejsu i implementuje `IUnknown` przez wysyłanie informacji do urządzenia zrzutu w kompilacjach debugowania.

[Samouczki dotyczące biblioteki](../../atl/active-template-library-atl-tutorial.md)ATL, [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IPropertyPage`

`IPropertyPageImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl. h

##  <a name="activate"></a>IPropertyPageImpl:: Activate

Tworzy okno dialogowe dla strony właściwości.

```
HRESULT Activate(
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```

### <a name="remarks"></a>Uwagi

Domyślnie okno dialogowe jest zawsze niemodalne, niezależnie od wartości parametru *bModal* .

Zobacz [IPropertyPage:: Activate](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-activate) w Windows SDK.

##  <a name="apply"></a>IPropertyPageImpl:: Apply

Stosuje bieżące wartości strony właściwości do obiektów podstawowych określonych za pomocą `SetObjects`.

```
HRESULT Apply();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage:: Apply](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-apply) w Windows SDK.

##  <a name="deactivate"></a>IPropertyPageImpl::D eactivate

Niszczy okno dialogowe utworzone w ramach [aktywacji](#activate).

```
HRESULT Deactivate();
```

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage::D eactivate](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-deactivate) w Windows SDK.

##  <a name="getpageinfo"></a>IPropertyPageImpl::GetPageInfo

Wypełnia strukturę *pPageInfo* informacjami zawartymi w elementach członkowskich danych.

```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Uwagi

`GetPageInfo` ładuje zasoby ciągów skojarzone z [m_dwDocString](#m_dwdocstring), [m_dwHelpFile](#m_dwhelpfile)i [m_dwTitle](#m_dwtitle).

Zobacz [IPropertyPage:: GetPageInfo](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-getpageinfo) w Windows SDK.

##  <a name="help"></a>IPropertyPageImpl:: help

Wywołuje Pomoc systemu Windows dla strony właściwości.

```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage:: help](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-help) w Windows SDK.

##  <a name="ipropertypageimpl"></a>IPropertyPageImpl::IPropertyPageImpl

Konstruktor.

```
IPropertyPageImpl();
```

### <a name="remarks"></a>Uwagi

Inicjuje wszystkie elementy członkowskie danych.

##  <a name="ispagedirty"></a>IPropertyPageImpl::IsPageDirty

Wskazuje, czy strona właściwości została zmieniona od czasu jej aktywacji.

```
HRESULT IsPageDirty(void);
```

### <a name="remarks"></a>Uwagi

`IsPageDirty` zwraca S_OK, jeśli strona została zmieniona od czasu jej aktywacji.

##  <a name="m_bdirty"></a>IPropertyPageImpl:: m_bDirty

Określa, czy stan strony właściwości został zmieniony.

```
BOOL m_bDirty;
```

##  <a name="m_nobjects"></a>IPropertyPageImpl:: m_nObjects

Przechowuje liczbę obiektów skojarzonych ze stroną właściwości.

```
ULONG m_nObjects;
```

##  <a name="m_dwhelpcontext"></a>IPropertyPageImpl:: m_dwHelpContext

Przechowuje identyfikator kontekstu dla tematu pomocy skojarzonego ze stroną właściwości.

```
DWORD m_dwHelpContext;
```

##  <a name="m_dwdocstring"></a>IPropertyPageImpl:: m_dwDocString

Przechowuje identyfikator zasobu skojarzony z ciągiem tekstowym opisującym stronę właściwości.

```
UINT m_dwDocString;
```

##  <a name="m_dwhelpfile"></a>IPropertyPageImpl:: m_dwHelpFile

Przechowuje identyfikator zasobu skojarzony z nazwą pliku pomocy opisującego stronę właściwości.

```
UINT m_dwHelpFile;
```

##  <a name="m_dwtitle"></a>IPropertyPageImpl:: m_dwTitle

Przechowuje identyfikator zasobu skojarzony z ciągiem tekstowym, który pojawia się na karcie strony właściwości.

```
UINT m_dwTitle;
```

##  <a name="m_ppagesite"></a>IPropertyPageImpl:: m_pPageSite

Wskazuje interfejs [IPropertyPageSite](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite) , za pomocą którego strona właściwości komunikuje się z ramką właściwości.

```
IPropertyPageSite* m_pPageSite;
```

##  <a name="m_ppunk"></a>IPropertyPageImpl:: m_ppUnk

Wskazuje tablicę `IUnknown` wskaźników do obiektów skojarzonych ze stroną właściwości.

```
IUnknown** m_ppUnk;
```

##  <a name="m_size"></a>IPropertyPageImpl:: m_size

Przechowuje wysokość i szerokość okna dialogowego strony właściwości (w pikselach).

```
SIZE m_size;
```

##  <a name="move"></a>IPropertyPageImpl:: Move

Położenie i rozmiar okna dialogowego strony właściwości.

```
HRESULT Move(LPCRECT pRect);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage:: Move](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-move) w Windows SDK.

##  <a name="setdirty"></a>IPropertyPageImpl:: SetDirty

Flaguje stan strony właściwości jako zmieniony lub niezmieniony, w zależności od wartości *bDirty*.

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>Parametry

*bDirty*<br/>
podczas W przypadku wartości TRUE stan strony właściwości jest oznaczony jako zmieniony. W przeciwnym razie jest oznaczona jako niezmieniona.

### <a name="remarks"></a>Uwagi

W razie potrzeby `SetDirty` informuje ramkę o zmianie strony właściwości.

##  <a name="setobjects"></a>IPropertyPageImpl:: SetObjects

Dostarcza tablicę wskaźników `IUnknown` dla obiektów skojarzonych ze stroną właściwości.

```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage:: SetObjects](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setobjects) w Windows SDK.

##  <a name="setpagesite"></a>IPropertyPageImpl::SetPageSite

Udostępnia stronę właściwości ze wskaźnikiem [IPropertyPageSite](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite) , za pomocą którego strona właściwości komunikuje się z ramką właściwości.

```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage:: SetPageSite](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setpagesite) w Windows SDK.

##  <a name="show"></a>IPropertyPageImpl:: show

Sprawia, że okno dialogowe strony właściwości jest widoczne lub niewidoczne.

```
HRESULT Show(UINT nCmdShow);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage:: show](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-show) w Windows SDK.

##  <a name="translateaccelerator"></a>IPropertyPageImpl::TranslateAccelerator

Przetwarza naciśnięcie klawisza określone w `pMsg`.

```
HRESULT TranslateAccelerator(MSG* pMsg);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage:: TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-translateaccelerator) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa IPropertyPage2Impl](../../atl/reference/ipropertypage2impl-class.md)<br/>
[Klasa IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[Klasa ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
