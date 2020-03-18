---
title: Klasa CContextMenuManager
ms.date: 11/04/2016
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
ms.openlocfilehash: c8a51a33c69b09d0ecd61520b5f1c9ff18c290a0
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420506"
---
# <a name="ccontextmenumanager-class"></a>Klasa CContextMenuManager

Obiekt `CContextMenuManager` zarządza menu skrótów, znane także jako menu kontekstowe.

## <a name="syntax"></a>Składnia

```
class CContextMenuManager : public CObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CContextMenuManager::CContextMenuManager](#ccontextmenumanager)|Konstruuje obiekt `CContextMenuManager`.|
|`CContextMenuManager::~CContextMenuManager`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CContextMenuManager:: Add— menu](#addmenu)|Dodaje nowe menu skrótów.|
|[CContextMenuManager::GetMenuById](#getmenubyid)|Zwraca uchwyt do menu skojarzonego z podanym IDENTYFIKATORem zasobu.|
|[CContextMenuManager::GetMenuByName](#getmenubyname)|Zwraca dojście do menu, które jest zgodne z podaną nazwą menu.|
|[CContextMenuManager::GetMenuNames](#getmenunames)|Zwraca listę nazw menu.|
|[CContextMenuManager:: LoadState](#loadstate)|Ładuje menu skrótów przechowywane w rejestrze systemu Windows.|
|[CContextMenuManager:: elementu ResetState](#resetstate)|Czyści menu skrótów z poziomu Menedżera menu kontekstowego.|
|[CContextMenuManager:: SaveState](#savestate)|Zapisuje menu skrótów do rejestru systemu Windows.|
|[CContextMenuManager::SetDontCloseActiveMenu](#setdontcloseactivemenu)|Określa, czy `CContextMenuManager` Zamyka aktywne menu skrótów, gdy pokazuje nowe menu skrótów.|
|[CContextMenuManager::ShowPopupMenu](#showpopupmenu)|Wyświetla określone menu skrótów.|
|[CContextMenuManager::TrackPopupMenu](#trackpopupmenu)|Wyświetla określone menu skrótów. Zwraca indeks wybranego polecenia menu.|

## <a name="remarks"></a>Uwagi

`CContextMenuManager` zarządza menu skrótów i zapewnia spójny wygląd.

Nie należy tworzyć ręcznie obiektu `CContextMenuManager`. Struktura aplikacji tworzy obiekt `CContextMenuManager`. Należy jednak wywołać [CWinAppEx:: InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) , gdy aplikacja zostanie zainicjowana. Po zainicjowaniu Menedżera kontekstu użyj metody [CWinAppEx::](../../mfc/reference/cwinappex-class.md#getcontextmenumanager) pretainmanager, aby uzyskać wskaźnik do Menedżera kontekstu dla aplikacji.

Możesz tworzyć menu skrótów w środowisku uruchomieniowym, wywołując `AddMenu`. Jeśli chcesz wyświetlić menu bez pierwszego odebrania danych wejściowych przez użytkownika, wywołaj `ShowPopupMenu`. `TrackPopupMenu` jest używany, gdy chcesz utworzyć menu i poczekać na dane wejściowe użytkownika. `TrackPopupMenu` zwraca indeks wybranego polecenia lub 0, jeśli użytkownik zakończył pracę bez zaznaczania żadnych elementów.

`CContextMenuManager` może również zapisać i załadować swój stan do rejestru systemu Windows.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak dodać menu do obiektu `CContextMenuManager` i jak zamknąć aktywne menu podręczne, gdy obiekt `CContextMenuManager` wyświetla nowy menu podręczne. Ten fragment kodu jest częścią [przykładu stron niestandardowych](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/cpp/ccontextmenumanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CContextMenuManager`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcontextmenumanager. h

##  <a name="addmenu"></a>CContextMenuManager:: Add— menu

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

*uiMenuNameResId*<br/>
podczas Identyfikator zasobu dla ciągu, który zawiera nazwę nowego menu.

*uiMenuResId*<br/>
podczas Identyfikator zasobu menu.

*lpszName*<br/>
podczas Ciąg, który zawiera nazwę nowego menu.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli metoda zakończyła się pomyślnie; 0, jeśli metoda zakończy się niepowodzeniem.

### <a name="remarks"></a>Uwagi

Ta metoda kończy się niepowodzeniem, jeśli *uiMenuResId* jest nieprawidłowa lub jeśli inne menu o tej samej nazwie już znajduje się w `CContextMenuManager`.

##  <a name="ccontextmenumanager"></a>CContextMenuManager::CContextMenuManager

Konstruuje obiekt [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) .

```
CContextMenuManager();
```

### <a name="remarks"></a>Uwagi

W większości przypadków nie należy tworzyć `CContextMenuManager` ręcznie. Struktura aplikacji tworzy obiekt `CContextMenuManager`. Podczas inicjowania aplikacji należy wywołać [CWinAppEx:: InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) . Aby uzyskać wskaźnik do Menedżera kontekstu, wywołaj metodę [CWinAppEx::](../../mfc/reference/cwinappex-class.md#getcontextmenumanager)pregetmanager.

##  <a name="getmenubyid"></a>CContextMenuManager::GetMenuById

Zwraca uchwyt do menu skojarzonego z danym IDENTYFIKATORem zasobu.

```
HMENU GetMenuById(UINT nMenuResId) const;
```

### <a name="parameters"></a>Parametry

*nMenuResId*<br/>
podczas Identyfikator zasobu dla menu.

### <a name="return-value"></a>Wartość zwrócona

Dojście do powiązanego menu lub `NULL`, jeśli nie można odnaleźć menu.

##  <a name="getmenubyname"></a>CContextMenuManager::GetMenuByName

Zwraca uchwyt do określonego menu.

```
HMENU GetMenuByName(
    LPCTSTR lpszName,
    UINT* puiOrigResID = NULL) const;
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
podczas Ciąg, który zawiera nazwę menu do pobrania.

*puiOrigResID*<br/>
określoną Wskaźnik do typu UINT. Ten parametr zawiera identyfikator zasobu określonego menu, jeśli został znaleziony.

### <a name="return-value"></a>Wartość zwrócona

Uchwyt do menu, który jest zgodny z nazwą określoną przez *lpszName*. Wartość NULL, jeśli nie istnieje menu o nazwie *lpszName*.

### <a name="remarks"></a>Uwagi

Jeśli ta metoda odnajdzie menu pasujące do *lpszName*, `GetMenuByName` przechowuje identyfikator zasobu menu w parametrze *puiOrigResID*.

##  <a name="getmenunames"></a>CContextMenuManager::GetMenuNames

Zwraca listę nazw menu dodanych do [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

```
void GetMenuNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>Parametry

*listOfNames*<br/>
określoną Odwołanie do parametru [CStringList](../../mfc/reference/cstringlist-class.md) . Ta metoda zapisuje listę nazw menu dla tego parametru.

##  <a name="loadstate"></a>CContextMenuManager:: LoadState

Ładuje informacje skojarzone z [klasą CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) z rejestru systemu Windows.

```
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
podczas Ciąg, który zawiera ścieżkę względną klucza rejestru.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli metoda zakończy się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Parametr *lpszProfileName* nie jest ścieżką bezwzględną dla wpisu rejestru. Jest to ścieżka względna, która jest dodawana na końcu domyślnego klucza rejestru dla aplikacji. Aby uzyskać lub ustawić domyślny klucz rejestru, należy użyć metod [CWinAppEx:: GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) i [CWinAppEx:: SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) odpowiednio.

Użyj metody [CContextMenuManager:: SaveState](#savestate) , aby zapisać menu skrótów do rejestru.

##  <a name="resetstate"></a>CContextMenuManager:: elementu ResetState

Czyści wszystkie elementy z menu skrótów skojarzonych z [klasą CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

```
virtual BOOL ResetState();
```

### <a name="return-value"></a>Wartość zwrócona

Ma wartość TRUE, jeśli metoda zakończy się pomyślnie. Wartość FALSE, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Ta metoda czyści menu podręczne i usuwa je z `CContextMenuManager`.

##  <a name="savestate"></a>CContextMenuManager:: SaveState

Zapisuje informacje skojarzone z [klasą CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) w rejestrze systemu Windows.

```
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
podczas Ciąg, który zawiera ścieżkę względną klucza rejestru.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli metoda zakończy się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Parametr *lpszProfileName* nie jest ścieżką bezwzględną dla wpisu rejestru. Jest to ścieżka względna, która jest dodawana na końcu domyślnego klucza rejestru dla aplikacji. Aby uzyskać lub ustawić domyślny klucz rejestru, należy użyć metod [CWinAppEx:: GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) i [CWinAppEx:: SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) odpowiednio.

Użyj metody [CContextMenuManager:: LoadState](#loadstate) , aby załadować menu skrótów z rejestru.

##  <a name="setdontcloseactivemenu"></a>CContextMenuManager::SetDontCloseActiveMenu

Określa, czy [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) Zamyka aktywne menu podręczne po wyświetleniu nowego menu podręcznego.

```
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parametry

*bSet*<br/>
podczas Parametr logiczny, który określa, czy zamknąć aktywne menu podręczne. Wartość TRUE wskazuje, że aktywne menu podręczne nie jest zamknięte. Wartość FALSE wskazuje, że aktywne menu podręczne jest zamknięte.

### <a name="remarks"></a>Uwagi

Domyślnie `CContextMenuManager` Zamyka aktywne menu podręczne.

##  <a name="showpopupmenu"></a>CContextMenuManager::ShowPopupMenu

Wyświetla określone menu skrótów.

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

*uiMenuResId*<br/>
podczas Identyfikator zasobu menu, które zostanie wyświetlone w tej metodzie.

*y*<br/>
podczas Przesunięcie w poziomie menu skrótów we współrzędnych klienta.

*t*<br/>
podczas Przesunięcie w pionie dla menu skrótów we współrzędnych klienta

*pWndOwner*<br/>
podczas Wskaźnik do okna nadrzędnego menu skrótów.

*bOwnMessage*<br/>
podczas Parametr logiczny, który wskazuje sposób, w jaki są kierowane komunikaty. Jeśli *bOwnMessage* ma wartość false, używana jest Standardowa usługa routingu MFC. W przeciwnym razie *pWndOwner* odbiera komunikaty.

*hmenuPopup*<br/>
podczas Uchwyt menu, które zostanie wyświetlone w tej metodzie.

*bAutoDestroy*<br/>
podczas Parametr logiczny, który wskazuje, czy menu zostanie automatycznie zniszczone.

*bRightAlign*<br/>
podczas Parametr logiczny, który wskazuje, jak są wyrównane elementy menu. Jeśli *bRightAlign* ma wartość true, menu jest wyrównane do prawej strony dla kolejności odczytywania od prawej do lewej.

### <a name="return-value"></a>Wartość zwrócona

Pierwsze Przeciążenie metody zwraca wartość różną od zera, jeśli metoda pomyślnie wyświetli menu; w przeciwnym razie 0. Drugie Przeciążenie metody zwraca wskaźnik do [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) , jeśli menu skrótów jest wyświetlane prawidłowo; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Ta metoda przypomina metodę [CContextMenuManager:: TrackPopupMenu](#trackpopupmenu) w przypadku, gdy obie metody wyświetlają menu skrótów. Jednak `TrackPopupMenu` zwraca indeks wybranego polecenia menu.

Jeśli parametr *bAutoDestroy* ma wartość false, należy ręcznie wywołać metodę dziedziczonej `DestroyMenu` w celu zwolnienia zasobów pamięci. Domyślna implementacja `ShowPopupMenu` nie używa parametru *bAutoDestroy*. Jest ona dostępna do użytku w przyszłości lub dla klas niestandardowych pochodnych z klasy `CContextMenuManager`.

##  <a name="trackpopupmenu"></a>CContextMenuManager::TrackPopupMenu

Wyświetla określone menu skrótów i zwraca indeks wybranego polecenia menu skrótów.

```
virtual UINT TrackPopupMenu(
    HMENU hmenuPopup,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bRightAlign = FALSE);
```

### <a name="parameters"></a>Parametry

*hmenuPopup*<br/>
podczas Uchwyt menu skrótów, które jest wyświetlane w tej metodzie.

*y*<br/>
podczas Przesunięcie w poziomie menu skrótów we współrzędnych klienta.

*t*<br/>
podczas Przesunięcie w pionie menu skrótów we współrzędnych klienta.

*pWndOwner*<br/>
podczas Wskaźnik do okna nadrzędnego menu skrótów.

*bRightAlign*<br/>
podczas Parametr logiczny, który wskazuje, jak są wyrównane elementy menu. Jeśli *bRightAlign* ma wartość true, menu jest wyrównane do prawej strony dla kolejności odczytywania od prawej do lewej. Jeśli *bRightAlign* ma wartość false, menu jest wyrównane do lewej strony w kolejności czytania od lewej do prawej.

### <a name="return-value"></a>Wartość zwrócona

Identyfikator polecenia menu polecenia wybranego przez użytkownika; 0 Jeśli użytkownik zamknie menu skrótów bez wybierania polecenia menu.

### <a name="remarks"></a>Uwagi

Ta metoda działa jako wywołanie modalne do wyświetlania menu skrótów. Aplikacja nie przejdzie do następującego wiersza w kodzie, dopóki użytkownik nie zamknie menu skrótów lub wybierze polecenie. Alternatywną metodą wyświetlania menu skrótów jest [CContextMenuManager:: ShowPopupMenu](#showpopupmenu). Ta metoda nie jest wywołaniem modalnym i nie zwróci identyfikatora wybranego polecenia.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)
