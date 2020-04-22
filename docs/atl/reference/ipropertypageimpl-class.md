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
ms.openlocfilehash: 154bfb5beb258ff26649f44f0bd4c23fb8708977
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745865"
---
# <a name="ipropertypageimpl-class"></a>Klasa IPropertyPageImpl

Ta klasa `IUnknown` implementuje i zapewnia domyślną implementację interfejsu [IPropertyPage.](/windows/win32/api/ocidl/nn-ocidl-ipropertypage)

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class IPropertyPageImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa, pochodząca od `IPropertyPageImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IPropertyPageImpl::IPropertyPageImpl](#ipropertypageimpl)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IPropertyPageImpl::Aktywuj](#activate)|Tworzy okno dialogowe strony właściwości.|
|[IPropertyPageImpl::Zastosuj](#apply)|Stosuje bieżące wartości strony właściwości do `SetObjects`podstawowych obiektów określonych za pośrednictwem . Implementacja ATL zwraca S_OK.|
|[IPropertyPageImpl::Daktywuj](#deactivate)|Niszczy okno utworzone `Activate`za pomocą pliku .|
|[IPropertyPageImpl::GetPageInfo](#getpageinfo)|Pobiera informacje o stronie właściwości.|
|[IPropertyPageImpl::Pomoc](#help)|Wywołuje pomoc systemu Windows dla strony właściwości.|
|[IPropertyPageImpl::IsPageDirty](#ispagedirty)|Wskazuje, czy strona właściwości została zmieniona od czasu jej aktywacji.|
|[IPropertyPageImpl::Przenieś](#move)|Umieszcza i zmienić rozmiar okna dialogowego strony właściwości.|
|[IPropertyPageImpl::SetDirty](#setdirty)|Oznacza stan strony właściwości jako zmieniony lub niezmieniony.|
|[IPropertyPageImpl::SetObjects](#setobjects)|Zawiera tablicę `IUnknown` wskaźników dla obiektów skojarzonych ze stroną właściwości. Obiekty te otrzymują bieżące wartości strony `Apply`właściwości za pośrednictwem wywołania .|
|[IPropertyPageImpl::SetPageWitite](#setpagesite)|Udostępnia stronie właściwości `IPropertyPageSite` wskaźnik, za pomocą którego strona właściwości komunikuje się z ramką właściwości.|
|[IPropertyPageImpl::Pokaż](#show)|Powoduje, że okno dialogowe strony właściwości jest widoczne lub niewidoczne.|
|[IPropertyPageImpl::TranslateAccelerator](#translateaccelerator)|Przetwarza określone naciśnięcie klawisza.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[IPropertyPageImpl::m_bDirty](#m_bdirty)|Określa, czy stan strony właściwości uległ zmianie.|
|[IPropertyPageImpl::m_dwDocString](#m_dwdocstring)|Przechowuje identyfikator zasobu skojarzony z ciągiem tekstowym opisującym stronę właściwości.|
|[IPropertyPageImpl::m_dwHelpContext](#m_dwhelpcontext)|Przechowuje identyfikator kontekstu dla tematu pomocy skojarzonego ze stroną właściwości.|
|[IPropertyPageImpl::m_dwHelpFile](#m_dwhelpfile)|Przechowuje identyfikator zasobu skojarzony z nazwą pliku pomocy opisującego stronę właściwości.|
|[IPropertyPageImpl::m_dwTitle](#m_dwtitle)|Przechowuje identyfikator zasobu skojarzony z ciągiem tekstowym wyświetlanym na karcie strony właściwości.|
|[IPropertyPageImpl::m_nObjects](#m_nobjects)|Przechowuje liczbę obiektów skojarzonych ze stroną właściwości.|
|[IPropertyPageImpl::m_pPageSite](#m_ppagesite)|Wskazuje interfejs, `IPropertyPageSite` za pośrednictwem którego strona właściwości komunikuje się z ramką właściwości.|
|[IPropertyPageImpl::m_ppUnk](#m_ppunk)|Wskazuje tablicę `IUnknown` wskaźników do obiektów skojarzonych ze stroną właściwości.|
|[IPropertyPageImpl::m_size](#m_size)|Przechowuje wysokość i szerokość okna dialogowego strony właściwości w pikselach.|

## <a name="remarks"></a>Uwagi

Interfejs [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) umożliwia obiektowi zarządzanie stroną określonej właściwości w arkuszu właściwości. Klasa `IPropertyPageImpl` zapewnia domyślną implementację tego `IUnknown` interfejsu i implementuje przez wysyłanie informacji do urządzenia zrzutu w kompilacjach debugowania.

**Podobne artykuły** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Tworzenie projektu [ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IPropertyPage`

`IPropertyPageImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

## <a name="ipropertypageimplactivate"></a><a name="activate"></a>IPropertyPageImpl::Aktywuj

Tworzy okno dialogowe strony właściwości.

```
HRESULT Activate(
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```

### <a name="remarks"></a>Uwagi

Domyślnie okno dialogowe jest zawsze niemodalne, niezależnie od wartości parametru *bModal.*

Zobacz [IPropertyPage::Aktywuj](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-activate) w windows SDK.

## <a name="ipropertypageimplapply"></a><a name="apply"></a>IPropertyPageImpl::Zastosuj

Stosuje bieżące wartości strony właściwości do `SetObjects`podstawowych obiektów określonych za pośrednictwem .

```
HRESULT Apply();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage::Apply](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-apply) w windows SDK.

## <a name="ipropertypageimpldeactivate"></a><a name="deactivate"></a>IPropertyPageImpl::Daktywuj

Niszczy okno dialogowe utworzone za pomocą [przycisku Aktywuj](#activate).

```
HRESULT Deactivate();
```

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage::Daaktywuj](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-deactivate) w usłudze Windows SDK.

## <a name="ipropertypageimplgetpageinfo"></a><a name="getpageinfo"></a>IPropertyPageImpl::GetPageInfo

Wypełnia strukturę *pPageInfo* informacjami zawartymi w członkach danych.

```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Uwagi

`GetPageInfo`ładuje zasoby ciągu skojarzone z [m_dwDocString](#m_dwdocstring) [, m_dwHelpFile](#m_dwhelpfile)i [m_dwTitle](#m_dwtitle).

Zobacz [IPropertyPage::GetPageInfo](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-getpageinfo) w usłudze Windows SDK.

## <a name="ipropertypageimplhelp"></a><a name="help"></a>IPropertyPageImpl::Pomoc

Wywołuje pomoc systemu Windows dla strony właściwości.

```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage::Pomoc](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-help) w windows SDK.

## <a name="ipropertypageimplipropertypageimpl"></a><a name="ipropertypageimpl"></a>IPropertyPageImpl::IPropertyPageImpl

Konstruktor.

```
IPropertyPageImpl();
```

### <a name="remarks"></a>Uwagi

Inicjuje wszystkie elementy członkowskie danych.

## <a name="ipropertypageimplispagedirty"></a><a name="ispagedirty"></a>IPropertyPageImpl::IsPageDirty

Wskazuje, czy strona właściwości została zmieniona od czasu jej aktywacji.

```
HRESULT IsPageDirty(void);
```

### <a name="remarks"></a>Uwagi

`IsPageDirty`zwraca S_OK, jeśli strona uległa zmianie od czasu jej aktywacji.

## <a name="ipropertypageimplm_bdirty"></a><a name="m_bdirty"></a>IPropertyPageImpl::m_bDirty

Określa, czy stan strony właściwości uległ zmianie.

```
BOOL m_bDirty;
```

## <a name="ipropertypageimplm_nobjects"></a><a name="m_nobjects"></a>IPropertyPageImpl::m_nObjects

Przechowuje liczbę obiektów skojarzonych ze stroną właściwości.

```
ULONG m_nObjects;
```

## <a name="ipropertypageimplm_dwhelpcontext"></a><a name="m_dwhelpcontext"></a>IPropertyPageImpl::m_dwHelpContext

Przechowuje identyfikator kontekstu dla tematu pomocy skojarzonego ze stroną właściwości.

```
DWORD m_dwHelpContext;
```

## <a name="ipropertypageimplm_dwdocstring"></a><a name="m_dwdocstring"></a>IPropertyPageImpl::m_dwDocString

Przechowuje identyfikator zasobu skojarzony z ciągiem tekstowym opisującym stronę właściwości.

```
UINT m_dwDocString;
```

## <a name="ipropertypageimplm_dwhelpfile"></a><a name="m_dwhelpfile"></a>IPropertyPageImpl::m_dwHelpFile

Przechowuje identyfikator zasobu skojarzony z nazwą pliku pomocy opisującego stronę właściwości.

```
UINT m_dwHelpFile;
```

## <a name="ipropertypageimplm_dwtitle"></a><a name="m_dwtitle"></a>IPropertyPageImpl::m_dwTitle

Przechowuje identyfikator zasobu skojarzony z ciągiem tekstowym wyświetlanym na karcie strony właściwości.

```
UINT m_dwTitle;
```

## <a name="ipropertypageimplm_ppagesite"></a><a name="m_ppagesite"></a>IPropertyPageImpl::m_pPageSite

Wskazuje interfejs [IPropertyPageSite,](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite) za pośrednictwem którego strona właściwości komunikuje się z ramką właściwości.

```
IPropertyPageSite* m_pPageSite;
```

## <a name="ipropertypageimplm_ppunk"></a><a name="m_ppunk"></a>IPropertyPageImpl::m_ppUnk

Wskazuje tablicę `IUnknown` wskaźników do obiektów skojarzonych ze stroną właściwości.

```
IUnknown** m_ppUnk;
```

## <a name="ipropertypageimplm_size"></a><a name="m_size"></a>IPropertyPageImpl::m_size

Przechowuje wysokość i szerokość okna dialogowego strony właściwości w pikselach.

```
SIZE m_size;
```

## <a name="ipropertypageimplmove"></a><a name="move"></a>IPropertyPageImpl::Przenieś

Umieszcza i zmienić rozmiar okna dialogowego strony właściwości.

```
HRESULT Move(LPCRECT pRect);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage::Przenieś w](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-move) windows SDK.

## <a name="ipropertypageimplsetdirty"></a><a name="setdirty"></a>IPropertyPageImpl::SetDirty

Oznacza stan strony właściwości jako zmieniony lub niezmieniony, w zależności od wartości *bDirty*.

```cpp
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>Parametry

*bDirty*<br/>
[w] Jeśli true, stan strony właściwości jest oznaczony jako zmieniony. W przeciwnym razie jest oznaczony jako niezmieniony.

### <a name="remarks"></a>Uwagi

W razie `SetDirty` potrzeby informuje ramkę, że strona właściwości została zmieniona.

## <a name="ipropertypageimplsetobjects"></a><a name="setobjects"></a>IPropertyPageImpl::SetObjects

Zawiera tablicę `IUnknown` wskaźników dla obiektów skojarzonych ze stroną właściwości.

```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage::SetObjects](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setobjects) w zestawie Windows SDK.

## <a name="ipropertypageimplsetpagesite"></a><a name="setpagesite"></a>IPropertyPageImpl::SetPageWitite

Udostępnia stronę właściwości ze [wskaźnikiem IPropertyPageSite,](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite) za pośrednictwem którego strona właściwości komunikuje się z ramką właściwości.

```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage::SetPageSite](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setpagesite) w zestawie Windows SDK.

## <a name="ipropertypageimplshow"></a><a name="show"></a>IPropertyPageImpl::Pokaż

Powoduje, że okno dialogowe strony właściwości jest widoczne lub niewidoczne.

```
HRESULT Show(UINT nCmdShow);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage::Show](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-show) w windows SDK.

## <a name="ipropertypageimpltranslateaccelerator"></a><a name="translateaccelerator"></a>IPropertyPageImpl::TranslateAccelerator

Przetwarza naciśnięcie klawisza `pMsg`określone w pliku .

```
HRESULT TranslateAccelerator(MSG* pMsg);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage::TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-translateaccelerator) w windows SDK.

## <a name="see-also"></a>Zobacz też

[Klasa IPropertyPage2Impl](../../atl/reference/ipropertypage2impl-class.md)<br/>
[Klasa IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl Klasa](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
