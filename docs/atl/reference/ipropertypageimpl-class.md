---
title: Klasa IPropertyPageImpl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords:
- property pages
- IPropertyPage ATL implementation
- IPropertyPageImpl class
ms.assetid: f9b7c8b1-7a04-4eab-aa63-63efddb740fa
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fbc62bd72ee5a639e8df0ada365cd7baac7d0c31
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ipropertypageimpl-class"></a>Klasa IPropertyPageImpl
Ta klasa implementuje **IUnknown** i udostępnia domyślną implementację elementu [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) interfejsu.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>  
class IPropertyPageImpl
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IPropertyPageImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IPropertyPageImpl::IPropertyPageImpl](#ipropertypageimpl)|Konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IPropertyPageImpl::Activate](#activate)|Tworzy okno dialogowe strony właściwości.|  
|[IPropertyPageImpl::Apply](#apply)|Dotyczy bieżące wartości strony właściwości określonej za pomocą obiektów `SetObjects`. Zwraca implementację ATL `S_OK`.|  
|[IPropertyPageImpl::Deactivate](#deactivate)|Niszczy okno utworzone za pomocą **Aktywuj**.|  
|[IPropertyPageImpl::GetPageInfo](#getpageinfo)|Pobiera informacje o stronę właściwości.|  
|[IPropertyPageImpl::Help](#help)|Wywołuje Pomoc systemu Windows dla strony właściwości.|  
|[IPropertyPageImpl::IsPageDirty](#ispagedirty)|Wskazuje, czy strona właściwości zmieniła się od jego został aktywowany.|  
|[IPropertyPageImpl::Move](#move)|Określa położenie i zmienia rozmiar okna dialogowego strony właściwości.|  
|[IPropertyPageImpl::SetDirty](#setdirty)|Flagi stanu strony właściwości jako zmienione lub niezmieniony.|  
|[IPropertyPageImpl::SetObjects](#setobjects)|Zawiera tablicę **IUnknown** wskaźniki do obiektów skojarzonych z stronę właściwości. Te obiekty otrzymywać bieżące wartości właściwości strony za pomocą wywołania **Zastosuj**.|  
|[IPropertyPageImpl::SetPageSite](#setpagesite)|Zawiera stronę właściwości z `IPropertyPageSite` wskaźnika, za pomocą którego strony właściwości komunikuje się z ramka właściwości.|  
|[IPropertyPageImpl::Show](#show)|Powoduje, że okno dialogowe właściwości strony widoczny lub niewidoczny.|  
|[IPropertyPageImpl::TranslateAccelerator](#translateaccelerator)|Przetwarza określony naciśnięcie klawisza.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IPropertyPageImpl::m_bDirty](#m_bdirty)|Określa, czy strona właściwości stan został zmieniony.|  
|[IPropertyPageImpl::m_dwDocString](#m_dwdocstring)|Przechowuje identyfikator zasobu skojarzony z ciągu tekstowego opisujące stronę właściwości.|  
|[IPropertyPageImpl::m_dwHelpContext](#m_dwhelpcontext)|Przechowuje identyfikator kontekstu tematu pomocy skojarzony ze stroną właściwości.|  
|[IPropertyPageImpl::m_dwHelpFile](#m_dwhelpfile)|Przechowuje identyfikator zasobu skojarzone z nazwą pliku Pomocy opisujące stronę właściwości.|  
|[IPropertyPageImpl::m_dwTitle](#m_dwtitle)|Przechowuje identyfikator zasobu skojarzony z ciąg tekstowy wyświetlany na karcie strony właściwości.|  
|[IPropertyPageImpl::m_nObjects](#m_nobjects)|Przechowuje numer obiektów skojarzonych z stronę właściwości.|  
|[IPropertyPageImpl::m_pPageSite](#m_ppagesite)|Wskazuje `IPropertyPageSite` interfejsu za pomocą którego strony właściwości komunikuje się z ramka właściwości.|  
|[IPropertyPageImpl::m_ppUnk](#m_ppunk)|Wskazuje tablicę **IUnknown** wskaźników do obiektów skojarzonych z stronę właściwości.|  
|[IPropertyPageImpl::m_size](#m_size)|Przechowuje wysokość i szerokość okna dialogowego strony właściwości, w pikselach.|  
  
## <a name="remarks"></a>Uwagi  
 [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) interfejs umożliwia zarządzanie określoną stronę właściwości w arkuszu właściwości obiektu. Klasa `IPropertyPageImpl` udostępnia domyślną implementację tego interfejsu i implementuje **IUnknown** , wysyłając informacje o do zrzutu kompilacje urządzenia podczas debugowania.  
  
 **Innych pokrewnych artykułach** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [tworzenie Projekt ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IPropertyPage`  
  
 `IPropertyPageImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
##  <a name="activate"></a>IPropertyPageImpl::Activate  
 Tworzy okno dialogowe strony właściwości.  
  
```
HRESULT Activate(  
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie okno dialogowe zawsze jest niemodalne, niezależnie od wartości *bModal* parametru.  
  
 Zobacz [IPropertyPage::Activate](http://msdn.microsoft.com/library/windows/desktop/ms682250) w systemie Windows SDK.  
  
##  <a name="apply"></a>IPropertyPageImpl::Apply  
 Dotyczy bieżące wartości strony właściwości określonej za pomocą obiektów `SetObjects`.  
  
```
HRESULT Apply();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPropertyPage::Apply](http://msdn.microsoft.com/library/windows/desktop/ms691284) w systemie Windows SDK.  
  
##  <a name="deactivate"></a>IPropertyPageImpl::Deactivate  
 Niszczy okno okno dialogowe utworzone za pomocą [Aktywuj](#activate).  
  
```
HRESULT Deactivate();
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPropertyPage::Deactivate](http://msdn.microsoft.com/library/windows/desktop/ms682504) w systemie Windows SDK.  
  
##  <a name="getpageinfo"></a>IPropertyPageImpl::GetPageInfo  
 Wypełnia *pPageInfo* struktury z informacjami zawartymi w elementach członkowskich danych.  
  
```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```  
  
### <a name="remarks"></a>Uwagi  
 `GetPageInfo`ładuje zasoby skojarzone z [m_dwDocString](#m_dwdocstring), [m_dwHelpFile](#m_dwhelpfile), i [m_dwTitle](#m_dwtitle).  
  
 Zobacz [IPropertyPage::GetPageInfo](http://msdn.microsoft.com/library/windows/desktop/ms680714) w systemie Windows SDK.  
  
##  <a name="help"></a>IPropertyPageImpl::Help  
 Wywołuje Pomoc systemu Windows dla strony właściwości.  
  
```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPropertyPage::Help](http://msdn.microsoft.com/library/windows/desktop/ms691504) w systemie Windows SDK.  
  
##  <a name="ipropertypageimpl"></a>IPropertyPageImpl::IPropertyPageImpl  
 Konstruktor.  
  
```
IPropertyPageImpl();
```  
  
### <a name="remarks"></a>Uwagi  
 Inicjuje wszystkie elementy członkowskie danych.  
  
##  <a name="ispagedirty"></a>IPropertyPageImpl::IsPageDirty  
 Wskazuje, czy strona właściwości zmieniła się od jego został aktywowany.  
  
```
HRESULT IsPageDirty(void);
```  
  
### <a name="remarks"></a>Uwagi  
 `IsPageDirty`Zwraca `S_OK` Jeśli strony uległ zmianie od czasu jego został aktywowany.  
  
##  <a name="m_bdirty"></a>IPropertyPageImpl::m_bDirty  
 Określa, czy strona właściwości stan został zmieniony.  
  
```
BOOL m_bDirty;
```  
  
##  <a name="m_nobjects"></a>IPropertyPageImpl::m_nObjects  
 Przechowuje numer obiektów skojarzonych z stronę właściwości.  
  
```
ULONG m_nObjects;
```  
  
##  <a name="m_dwhelpcontext"></a>IPropertyPageImpl::m_dwHelpContext  
 Przechowuje identyfikator kontekstu tematu pomocy skojarzony ze stroną właściwości.  
  
```
DWORD m_dwHelpContext;
```  
  
##  <a name="m_dwdocstring"></a>IPropertyPageImpl::m_dwDocString  
 Przechowuje identyfikator zasobu skojarzony z ciągu tekstowego opisujące stronę właściwości.  
  
```
UINT m_dwDocString;
```  
  
##  <a name="m_dwhelpfile"></a>IPropertyPageImpl::m_dwHelpFile  
 Przechowuje identyfikator zasobu skojarzone z nazwą pliku Pomocy opisujące stronę właściwości.  
  
```
UINT m_dwHelpFile;
```  
  
##  <a name="m_dwtitle"></a>IPropertyPageImpl::m_dwTitle  
 Przechowuje identyfikator zasobu skojarzony z ciąg tekstowy wyświetlany na karcie strony właściwości.  
  
```
UINT m_dwTitle;
```  
  
##  <a name="m_ppagesite"></a>IPropertyPageImpl::m_pPageSite  
 Wskazuje [IPropertyPageSite](http://msdn.microsoft.com/library/windows/desktop/ms690583) interfejsu za pomocą którego strony właściwości komunikuje się z ramka właściwości.  
  
```
IPropertyPageSite* m_pPageSite;
```  
  
##  <a name="m_ppunk"></a>IPropertyPageImpl::m_ppUnk  
 Wskazuje tablicę **IUnknown** wskaźników do obiektów skojarzonych z stronę właściwości.  
  
```
IUnknown** m_ppUnk;
```  
  
##  <a name="m_size"></a>IPropertyPageImpl::m_size  
 Przechowuje wysokość i szerokość okna dialogowego strony właściwości, w pikselach.  
  
```
SIZE m_size;
```  
  
##  <a name="move"></a>IPropertyPageImpl::Move  
 Określa położenie i zmienia rozmiar okna dialogowego strony właściwości.  
  
```
HRESULT Move(LPCRECT pRect);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPropertyPage::Move](http://msdn.microsoft.com/library/windows/desktop/ms680118) w systemie Windows SDK.  
  
##  <a name="setdirty"></a>IPropertyPageImpl::SetDirty  
 Flagi stanu strony właściwości jako zmieniony lub bez zmian, w zależności od wartości `bDirty`.  
  
```
void SetDirty(BOOL bDirty);
```  
  
### <a name="parameters"></a>Parametry  
 `bDirty`  
 [in] Jeśli **TRUE**, stan strony właściwości jest oznaczony jako zmieniony. W przeciwnym razie jest ona oznaczona jako bez zmian.  
  
### <a name="remarks"></a>Uwagi  
 W razie potrzeby `SetDirty` informuje ramki, w której stronę właściwości została zmieniona.  
  
##  <a name="setobjects"></a>IPropertyPageImpl::SetObjects  
 Zawiera tablicę **IUnknown** wskaźniki do obiektów skojarzonych z stronę właściwości.  
  
```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPropertyPage::SetObjects](http://msdn.microsoft.com/library/windows/desktop/ms678529) w systemie Windows SDK.  
  
##  <a name="setpagesite"></a>IPropertyPageImpl::SetPageSite  
 Zawiera stronę właściwości z [IPropertyPageSite](http://msdn.microsoft.com/library/windows/desktop/ms690583) wskaźnika, za pomocą którego strony właściwości komunikuje się z ramka właściwości.  
  
```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPropertyPage::SetPageSite](http://msdn.microsoft.com/library/windows/desktop/ms690413) w systemie Windows SDK.  
  
##  <a name="show"></a>IPropertyPageImpl::Show  
 Powoduje, że okno dialogowe właściwości strony widoczny lub niewidoczny.  
  
```
HRESULT Show(UINT nCmdShow);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPropertyPage::Show](http://msdn.microsoft.com/library/windows/desktop/ms694467) w systemie Windows SDK.  
  
##  <a name="translateaccelerator"></a>IPropertyPageImpl::TranslateAccelerator  
 Przetwarza klawiszy określone w `pMsg`.  
  
```
HRESULT TranslateAccelerator(MSG* pMsg);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IPropertyPage::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms686603) w systemie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa IPropertyPage2Impl](../../atl/reference/ipropertypage2impl-class.md)   
 [Klasa IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [Klasa ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
