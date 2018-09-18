---
title: Klasa IPropertyPageImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- property pages
- IPropertyPage ATL implementation
- IPropertyPageImpl class
ms.assetid: f9b7c8b1-7a04-4eab-aa63-63efddb740fa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2b07609b792b7080e2c4c432ed435381007ba286
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075231"
---
# <a name="ipropertypageimpl-class"></a>Klasa IPropertyPageImpl

Ta klasa implementuje `IUnknown` i udostępnia domyślną implementację elementu [IPropertyPage](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage) interfejsu.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class IPropertyPageImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `IPropertyPageImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IPropertyPageImpl::IPropertyPageImpl](#ipropertypageimpl)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IPropertyPageImpl::Activate](#activate)|Tworzy okno okno dialogowe strony właściwości.|
|[IPropertyPageImpl::Apply](#apply)|Dotyczy bieżące wartości strony właściwości określone przez obiekty źródłowe `SetObjects`. Implementacja biblioteki ATL, zwraca wartość S_OK.|
|[IPropertyPageImpl::Deactivate](#deactivate)|Niszczy okno utworzone za pomocą `Activate`.|
|[IPropertyPageImpl::GetPageInfo](#getpageinfo)|Pobiera informacje o stronie właściwości.|
|[IPropertyPageImpl::Help](#help)|Wywołuje Pomoc Windows dla strony właściwości.|
|[IPropertyPageImpl::IsPageDirty](#ispagedirty)|Wskazuje, czy strona właściwości uległy zmianie, ponieważ została ona aktywowana.|
|[IPropertyPageImpl::Move](#move)|Określa położenie i zmienia rozmiar okno dialogowe strony właściwości.|
|[IPropertyPageImpl::SetDirty](#setdirty)|Flagi stanu na stronie właściwości jako zmienione lub bez zmian.|
|[IPropertyPageImpl::SetObjects](#setobjects)|Oferuje szereg `IUnknown` wskaźniki dla obiektów skojarzonych z na stronie właściwości. Te obiekty otrzymują bieżące wartości właściwości dla strony za pomocą wywołania `Apply`.|
|[IPropertyPageImpl::SetPageSite](#setpagesite)|Miejsce na stronie właściwości, za pomocą `IPropertyPageSite` wskaźnika, za pomocą którego strony właściwości komunikuje się z ramka właściwości.|
|[IPropertyPageImpl::Show](#show)|Sprawia, że okno dialogowe strony właściwości widoczny lub niewidoczny.|
|[IPropertyPageImpl::TranslateAccelerator](#translateaccelerator)|Przetwarza określony naciśnięcia klawisza.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[IPropertyPageImpl::m_bDirty](#m_bdirty)|Określa, czy strona właściwości stan został zmieniony.|
|[IPropertyPageImpl::m_dwDocString](#m_dwdocstring)|Przechowuje identyfikator skojarzony z ciągu tekstowego, opisujący na stronie właściwości.|
|[IPropertyPageImpl::m_dwHelpContext](#m_dwhelpcontext)|Przechowuje identyfikator kontekstu tematu Pomocy skojarzone ze stroną właściwości.|
|[IPropertyPageImpl::m_dwHelpFile](#m_dwhelpfile)|Przechowuje identyfikator zasobu skojarzone z nazwą pliku pomocy opisem na stronie właściwości.|
|[IPropertyPageImpl::m_dwTitle](#m_dwtitle)|Przechowuje identyfikator skojarzony z ciąg tekstowy, który pojawia się na karcie dla strony właściwości.|
|[IPropertyPageImpl::m_nObjects](#m_nobjects)|Przechowuje liczbę obiektów skojarzonych z na stronie właściwości.|
|[IPropertyPageImpl::m_pPageSite](#m_ppagesite)|Wskazuje `IPropertyPageSite` interfejsu komunikuje za pomocą którego ramka właściwości na stronie właściwości.|
|[IPropertyPageImpl::m_ppUnk](#m_ppunk)|Wskazuje na tablicę `IUnknown` wskaźników do obiektów skojarzonych z na stronie właściwości.|
|[IPropertyPageImpl::m_size](#m_size)|Przechowuje wysokość i szerokość okna dialogowego strony właściwości, w pikselach.|

## <a name="remarks"></a>Uwagi

[IPropertyPage](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage) interfejs umożliwia zarządzanie określoną stronę właściwości w arkuszu właściwości obiektu. Klasa `IPropertyPageImpl` udostępnia domyślną implementację tego interfejsu i implementuje `IUnknown` , wysyłając informacje o do zrzutu kompilacji urządzenia podczas debugowania.

**Powiązane artykuły** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IPropertyPage`

`IPropertyPageImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

##  <a name="activate"></a>  IPropertyPageImpl::Activate

Tworzy okno okno dialogowe strony właściwości.

```
HRESULT Activate(  
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```

### <a name="remarks"></a>Uwagi

Domyślnie okno dialogowe zawsze jest niemodalne, bez względu na wartość *bModal* parametru.

Zobacz [IPropertyPage::Activate](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-activate) w Windows SDK.

##  <a name="apply"></a>  IPropertyPageImpl::Apply

Dotyczy bieżące wartości strony właściwości określone przez obiekty źródłowe `SetObjects`.

```
HRESULT Apply();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage::Apply](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-apply) w Windows SDK.

##  <a name="deactivate"></a>  IPropertyPageImpl::Deactivate

Niszczy okno dialogowe, utworzony za pomocą [Aktywuj](#activate).

```
HRESULT Deactivate();
```

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage::Deactivate](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-deactivate) w Windows SDK.

##  <a name="getpageinfo"></a>  IPropertyPageImpl::GetPageInfo

Wypełnia *pPageInfo* strukturę z informacjami zawartymi w składowych danych.

```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Uwagi

`GetPageInfo` ładuje zasoby ciągu skojarzone z [m_dwDocString](#m_dwdocstring), [m_dwHelpFile](#m_dwhelpfile), i [m_dwTitle](#m_dwtitle).

Zobacz [IPropertyPage::GetPageInfo](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-getpageinfo) w Windows SDK.

##  <a name="help"></a>  IPropertyPageImpl::Help

Wywołuje Pomoc Windows dla strony właściwości.

```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage::Help](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-help) w Windows SDK.

##  <a name="ipropertypageimpl"></a>  IPropertyPageImpl::IPropertyPageImpl

Konstruktor.

```
IPropertyPageImpl();
```

### <a name="remarks"></a>Uwagi

Inicjuje wszystkie elementy członkowskie danych.

##  <a name="ispagedirty"></a>  IPropertyPageImpl::IsPageDirty

Wskazuje, czy strona właściwości uległy zmianie, ponieważ została ona aktywowana.

```
HRESULT IsPageDirty(void);
```

### <a name="remarks"></a>Uwagi

`IsPageDirty` Zwraca wartość S_OK, jeśli strony uległ zmianie, ponieważ została ona aktywowana.

##  <a name="m_bdirty"></a>  IPropertyPageImpl::m_bDirty

Określa, czy strona właściwości stan został zmieniony.

```
BOOL m_bDirty;
```

##  <a name="m_nobjects"></a>  IPropertyPageImpl::m_nObjects

Przechowuje liczbę obiektów skojarzonych z na stronie właściwości.

```
ULONG m_nObjects;
```

##  <a name="m_dwhelpcontext"></a>  IPropertyPageImpl::m_dwHelpContext

Przechowuje identyfikator kontekstu tematu Pomocy skojarzone ze stroną właściwości.

```
DWORD m_dwHelpContext;
```

##  <a name="m_dwdocstring"></a>  IPropertyPageImpl::m_dwDocString

Przechowuje identyfikator skojarzony z ciągu tekstowego, opisujący na stronie właściwości.

```
UINT m_dwDocString;
```

##  <a name="m_dwhelpfile"></a>  IPropertyPageImpl::m_dwHelpFile

Przechowuje identyfikator zasobu skojarzone z nazwą pliku pomocy opisem na stronie właściwości.

```
UINT m_dwHelpFile;
```

##  <a name="m_dwtitle"></a>  IPropertyPageImpl::m_dwTitle

Przechowuje identyfikator skojarzony z ciąg tekstowy, który pojawia się na karcie dla strony właściwości.

```
UINT m_dwTitle;
```

##  <a name="m_ppagesite"></a>  IPropertyPageImpl::m_pPageSite

Wskazuje [IPropertyPageSite](/windows/desktop/api/ocidl/nn-ocidl-ipropertypagesite) interfejsu komunikuje za pomocą którego ramka właściwości na stronie właściwości.

```
IPropertyPageSite* m_pPageSite;
```

##  <a name="m_ppunk"></a>  IPropertyPageImpl::m_ppUnk

Wskazuje na tablicę `IUnknown` wskaźników do obiektów skojarzonych z na stronie właściwości.

```
IUnknown** m_ppUnk;
```

##  <a name="m_size"></a>  IPropertyPageImpl::m_size

Przechowuje wysokość i szerokość okna dialogowego strony właściwości, w pikselach.

```
SIZE m_size;
```

##  <a name="move"></a>  IPropertyPageImpl::Move

Określa położenie i zmienia rozmiar okno dialogowe strony właściwości.

```
HRESULT Move(LPCRECT pRect);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage::Move](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-move) w Windows SDK.

##  <a name="setdirty"></a>  IPropertyPageImpl::SetDirty

Na stronie właściwości Stan zmienionego lub bez zmian, w zależności od wartości flagi *bDirty*.

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>Parametry

*bDirty*<br/>
[in] W przypadku opcji TRUE stanu strony właściwość jest oznaczona zgodnie zmieniona. W przeciwnym razie jest ona oznaczona jako niezmieniony.

### <a name="remarks"></a>Uwagi

Jeśli to konieczne, `SetDirty` informuje ramki, który zmienił się na stronie właściwości.

##  <a name="setobjects"></a>  IPropertyPageImpl::SetObjects

Oferuje szereg `IUnknown` wskaźniki dla obiektów skojarzonych z na stronie właściwości.

```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage::SetObjects](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-setobjects) w Windows SDK.

##  <a name="setpagesite"></a>  IPropertyPageImpl::SetPageSite

Miejsce na stronie właściwości, za pomocą [IPropertyPageSite](/windows/desktop/api/ocidl/nn-ocidl-ipropertypagesite) wskaźnika, za pomocą którego strony właściwości komunikuje się z ramka właściwości.

```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage::SetPageSite](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-setpagesite) w Windows SDK.

##  <a name="show"></a>  IPropertyPageImpl::Show

Sprawia, że okno dialogowe strony właściwości widoczny lub niewidoczny.

```
HRESULT Show(UINT nCmdShow);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage::Show](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-show) w Windows SDK.

##  <a name="translateaccelerator"></a>  IPropertyPageImpl::TranslateAccelerator

Przetwarza naciśnięcia klawisza określone w `pMsg`.

```
HRESULT TranslateAccelerator(MSG* pMsg);
```

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage::TranslateAccelerator](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage-translateaccelerator) w Windows SDK.

## <a name="see-also"></a>Zobacz też

[Klasa IPropertyPage2Impl](../../atl/reference/ipropertypage2impl-class.md)<br/>
[Klasa IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[Klasa ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
