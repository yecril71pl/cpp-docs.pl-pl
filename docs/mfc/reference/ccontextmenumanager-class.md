---
title: Klasa CContextMenuManager | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager::CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager::AddMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuById
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuByName
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuNames
- AFXCONTEXTMENUMANAGER/CContextMenuManager::LoadState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::ResetState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::SaveState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::SetDontCloseActiveMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::ShowPopupMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::TrackPopupMenu
dev_langs:
- C++
helpviewer_keywords:
- CContextMenuManager [MFC], CContextMenuManager
- CContextMenuManager [MFC], AddMenu
- CContextMenuManager [MFC], GetMenuById
- CContextMenuManager [MFC], GetMenuByName
- CContextMenuManager [MFC], GetMenuNames
- CContextMenuManager [MFC], LoadState
- CContextMenuManager [MFC], ResetState
- CContextMenuManager [MFC], SaveState
- CContextMenuManager [MFC], SetDontCloseActiveMenu
- CContextMenuManager [MFC], ShowPopupMenu
- CContextMenuManager [MFC], TrackPopupMenu
ms.assetid: 1de20640-243c-47e1-85de-1baa4153bc83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1eb3bb0d96723f14f6dec56853d52860f0568c03
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357718"
---
# <a name="ccontextmenumanager-class"></a>Klasa CContextMenuManager
`CContextMenuManager` Zarządza obiekt menu skrótów, znanej także jako menu kontekstowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CContextMenuManager : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CContextMenuManager::CContextMenuManager](#ccontextmenumanager)|Konstruuje `CContextMenuManager` obiektu.|  
|`CContextMenuManager::~CContextMenuManager`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CContextMenuManager::AddMenu](#addmenu)|Dodaje nowe menu skrótów.|  
|[CContextMenuManager::GetMenuById](#getmenubyid)|Zwraca dojście do menu skojarzona z identyfikatorem zasobu udostępnionego.|  
|[CContextMenuManager::GetMenuByName](#getmenubyname)|Zwraca dojście do menu, która jest zgodna z nazwą podana menu.|  
|[CContextMenuManager::GetMenuNames](#getmenunames)|Zwraca listę nazw menu.|  
|[CContextMenuManager::LoadState](#loadstate)|Ładuje menu skrótów przechowywane w rejestrze systemu Windows.|  
|[CContextMenuManager::ResetState](#resetstate)|Czyści menu skrótów z Menedżera menu kontekstowego.|  
|[CContextMenuManager::SaveState](#savestate)|Menu skrótów jest zapisywany w rejestrze systemu Windows.|  
|[CContextMenuManager::SetDontCloseActiveMenu](#setdontcloseactivemenu)|Formanty czy `CContextMenuManager` Zamyka menu skrótów active, gdy widoczny jest nowe menu skrótów.|  
|[CContextMenuManager::ShowPopupMenu](#showpopupmenu)|Wyświetla menu skrótów określony.|  
|[CContextMenuManager::TrackPopupMenu](#trackpopupmenu)|Wyświetla menu skrótów określony. Zwraca indeks wybrane polecenie.|  
  
## <a name="remarks"></a>Uwagi  
 `CContextMenuManager` zarządza menu skrótów i upewnia się, że mają one spójny wygląd.  
  
 Nie należy tworzyć `CContextMenuManager` obiekt ręcznie. Struktura aplikacji tworzy `CContextMenuManager` obiektu. Jednak należy wywołać [CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) po zainicjowaniu aplikacji. Po inicjowania Menedżera kontekstu, należy użyć metody [CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager) uzyskać wskaźnik do Menedżera kontekstu aplikacji.  
  
 Menu skrótów można utworzyć w czasie wykonywania, wywołując `AddMenu`. Jeśli chcesz wyświetlić menu bez pierwszy odbierania danych wejściowych użytkownika, wywołanie `ShowPopupMenu`. `TrackPopupMenu` jest używany, gdy użytkownik chce utworzyć menu i poczekaj, aż dane wejściowe użytkownika. `TrackPopupMenu` Zwraca indeks wybranego polecenia lub wartość 0, jeśli użytkownik zakończyła pracę bez zaznaczania czegokolwiek.  
  
 `CContextMenuManager` Można także zapisać i załaduj jego stan w rejestrze systemu Windows.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak dodać menu `CContextMenuManager` obiekt i jak nie zamknąć Aktywne menu podręczne podczas `CContextMenuManager` obiekt wyświetla nowy menu podręczne. Następujący fragment kodu jest częścią [próbki niestandardowych stron](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/cpp/ccontextmenumanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CContextMenuManager`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcontextmenumanager.h  
  
##  <a name="addmenu"></a>  CContextMenuManager::AddMenu  
 Dodaje nowe menu skrótów do [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).  
  
```  
BOOL AddMenu(
    UINT uiMenuNameResId,  
    UINT uiMenuResId);

 
BOOL AddMenu(
    LPCTSTR lpszName,  
    UINT uiMenuResId);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `uiMenuNameResId`  
 Identyfikator zasobu ciągu zawierającego nazwę nowego menu.  
  
 [in] `uiMenuResId`  
 Identyfikator zasobu menu.  
  
 [in] `lpszName`  
 Ciąg zawierający nazwę nowego menu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli metoda zakończyło się pomyślnie; 0, jeśli metoda nie powiedzie się.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zakończy się niepowodzeniem, jeśli `uiMenuResId` jest nieprawidłowy lub jeśli innym menu o takiej samej nazwie jest już w `CContextMenuManager`.  
  
##  <a name="ccontextmenumanager"></a>  CContextMenuManager::CContextMenuManager  
 Konstruuje [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) obiektu.  
  
```  
CContextMenuManager();
```  
  
### <a name="remarks"></a>Uwagi  
 W większości przypadków, nie należy tworzyć `CContextMenuManager` ręcznie. Struktura aplikacji tworzy `CContextMenuManager` obiektu. Należy wywołać [CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) podczas inicjowania aplikacji. Aby uzyskać wskaźnika menedżera kontekstu, wywołaj [CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager).  
  
##  <a name="getmenubyid"></a>  CContextMenuManager::GetMenuById  
 Zwraca dojście do menu skojarzona z identyfikatorem zasobu.  
  
```  
HMENU GetMenuById(UINT nMenuResId) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] `nMenuResId`  
 Identyfikator zasobu menu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do menu skojarzona lub `NULL` Jeśli menu nie zostanie znaleziony.  
  
##  <a name="getmenubyname"></a>  CContextMenuManager::GetMenuByName  
 Zwraca dojście do określonych menu.  
  
```  
HMENU GetMenuByName(
    LPCTSTR lpszName,  
    UINT* puiOrigResID = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] `lpszName`  
 Ciąg zawierający nazwę menu do pobrania.  
  
 [out] `puiOrigResID`  
 Wskaźnik do `UINT`. Ten parametr zawiera menu określony identyfikator zasobu, jeśli znaleziono.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do menu, która jest zgodna z nazwą określoną przez `lpszName`. `NULL` Jeśli jest menu nie wywołuje `lpszName`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ta metoda umożliwia znalezienie menu, która odpowiada `lpszName`, `GetMenuByName` przechowuje identyfikator zasobu menu w parametrze `puiOrigResID`.  
  
##  <a name="getmenunames"></a>  CContextMenuManager::GetMenuNames  
 Zwraca listę nazw menu dodane do [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).  
  
```  
void GetMenuNames(CStringList& listOfNames) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out] `listOfNames`  
 Odwołanie do [CStringList](../../mfc/reference/cstringlist-class.md) parametru. Ta metoda zapisuje listę nazw menu tego parametru.  
  
##  <a name="loadstate"></a>  CContextMenuManager::LoadState  
 Ładuje informacje związane z [klasy CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) z rejestru systemu Windows.  
  
```  
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `lpszProfileName`  
 Ciąg, który zawiera względną ścieżkę klucza rejestru.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli metoda zakończy się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 `lpszProfileName` Parametr nie jest ścieżką bezwzględną wpisu rejestru. Jest ścieżką względną, który zostanie dodany na końcu domyślny klucz rejestru dla aplikacji. Aby pobrać lub ustawić klucz rejestru domyślne, należy użyć metod [CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) i [CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) odpowiednio.  
  
 Użyj metody [CContextMenuManager::SaveState](#savestate) zapisać menu skrótów do rejestru.  
  
##  <a name="resetstate"></a>  CContextMenuManager::ResetState  
 Czyści wszystkie elementy z menu skrótów skojarzone z [CContextMenuManager klasy](../../mfc/reference/ccontextmenumanager-class.md).  
  
```  
virtual BOOL ResetState();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli metoda zakończy się pomyślnie; `FALSE` Jeśli wystąpi błąd.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda usuwa menu podręcznego i usuwa je z `CContextMenuManager`.  
  
##  <a name="savestate"></a>  CContextMenuManager::SaveState  
 Zapisuje informacje związane z [klasy CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) w rejestrze systemu Windows.  
  
```  
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `lpszProfileName`  
 Ciąg, który zawiera względną ścieżkę klucza rejestru.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli metoda zakończy się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 `lpszProfileName` Parametr nie jest ścieżką bezwzględną wpisu rejestru. Jest ścieżką względną, który zostanie dodany na końcu domyślny klucz rejestru dla aplikacji. Aby pobrać lub ustawić klucz rejestru domyślne, należy użyć metod [CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) i [CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) odpowiednio.  
  
 Użyj metody [CContextMenuManager::LoadState](#loadstate) załadować menu skrótów z rejestru.  
  
##  <a name="setdontcloseactivemenu"></a>  CContextMenuManager::SetDontCloseActiveMenu  
 Formanty czy [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) zamyka aktywne menu podręczne wyświetlanych nowego menu podręczne.  
  
```  
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `bSet`  
 Wartość logiczna parametr, który określa, czy zamknąć Aktywne menu podręczne. Wartość `TRUE` wskazuje aktywne menu podręczne nie jest zamknięty. `FALSE` Wskazuje, że aktywne menu podręczne jest zamknięty.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie `CContextMenuManager` zamyka aktywne menu podręczne.  
  
##  <a name="showpopupmenu"></a>  CContextMenuManager::ShowPopupMenu  
 Wyświetla menu skrótów określony.  
  
```  
virtual BOOL ShowPopupMenu(
    UINT uiMenuResId,  
    int x,  
    int y,  
    CWnd* pWndOwner,  
    BOOL bOwnMessage = FALSE,  
    BOOL bRightAlign = FALSE);

 
virtual CMFCPopupMenu* ShowPopupMenu(
    HMENU hmenuPopup,  
    int x,  
    int y,  
    CWnd* pWndOwner,  
    BOOL bOwnMessage = FALSE,  
    BOOL bAutoDestroy = TRUE,  
    BOOL bRightAlign = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `uiMenuResId`  
 Identyfikator zasobu menu, która służy do wyświetlenia tej metody.  
  
 [in] `x`  
 Poziomej przesunięcia menu skrótów we współrzędnych klienta.  
  
 [in] `y`  
 Przesunięcie w pionie menu skrótów we współrzędnych klienta  
  
 [in] `pWndOwner`  
 Wskaźnik do menu skrótów okna nadrzędnego.  
  
 [in] `bOwnMessage`  
 Parametrów typu Boolean wskazującą sposób kierowania wiadomości. Jeśli `bOwnMessage` jest `FALSE`, standardowego MFC routing jest używany. W przeciwnym razie `pWndOwner` odbiera komunikaty.  
  
 [in] `hmenuPopup`  
 Dojście menu, która służy do wyświetlenia tej metody.  
  
 [in] `bAutoDestroy`  
 Parametrów typu Boolean wskazującą, czy menu zostaną automatycznie usunięte.  
  
 [in] `bRightAlign`  
 Parametrów typu Boolean, która wskazuje sposób wyrównania elementów menu. Jeśli `bRightAlign` jest `TRUE`, menu jest wyrównany do kolejność czytania od prawej do lewej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy przeciążenie metody zwraca różną od zera, jeśli metoda zawiera menu pomyślnie; w przeciwnym razie 0. Drugi przeciążenie metody zwraca wskaźnik do [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) Jeśli menu skrótów wyświetlane prawidłowo; w przeciwnym razie `NULL`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest podobny metody [CContextMenuManager::TrackPopupMenu](#trackpopupmenu) w tym obu metod wyświetlić menu skrótów. Jednak `TrackPopupMenu` zwraca indeks wybrane polecenie.  
  
 Jeśli parametr `bAutoDestroy` jest `FALSE`, należy wywołać ręcznie dziedziczonego `DestroyMenu` metodę, aby zwolnić zasoby pamięci. Domyślna implementacja `ShowPopupMenu` nie używa parametru `bAutoDestroy`. Podano do użytku w przyszłości lub niestandardowych klas pochodnych `CContextMenuManager` klasy.  
  
##  <a name="trackpopupmenu"></a>  CContextMenuManager::TrackPopupMenu  
 Wyświetla menu skrótów określonego i zwraca indeks polecenia menu skrótów wybrane.  
  
```  
virtual UINT TrackPopupMenu(
    HMENU hmenuPopup,  
    int x,  
    int y,  
    CWnd* pWndOwner,  
    BOOL bRightAlign = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `hmenuPopup`  
 Dojście menu skrótów, które zawiera tę metodę.  
  
 [in] `x`  
 Poziomej przesunięcia menu skrótów we współrzędnych klienta.  
  
 [in] `y`  
 Pionowej przesunięcia menu skrótów we współrzędnych klienta.  
  
 [in] `pWndOwner`  
 Wskaźnik do menu skrótów okna nadrzędnego.  
  
 [in] `bRightAlign`  
 Parametrów typu Boolean, która wskazuje sposób wyrównania elementów menu. Jeśli `bRightAlign` jest `TRUE`, menu jest wyrównany do kolejność czytania od prawej do lewej. Jeśli `bRightAlign` jest `FALSE`, menu jest wyrównany do kolejność czytania od lewej do prawej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator polecenia menu polecenia, które użytkownik wybierze; 0, jeśli użytkownik zamyka menu skrótów bez zaznaczania polecenia menu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda działa jako modalne wywołanie, aby wyświetlić menu skrótów. Aplikacja nie będzie kontynuowane do następującej pozycji w kodzie, dopóki użytkownik zamyka menu skrótów lub wybierze polecenie. Alternatywne metody, której można użyć, aby wyświetlić menu skrótów [CContextMenuManager::ShowPopupMenu](#showpopupmenu). Tej metody nie jest wywołaniem modalne i nie będzie zwracać identyfikator wybranego polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)
