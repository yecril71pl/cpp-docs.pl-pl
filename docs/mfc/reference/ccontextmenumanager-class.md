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
ms.openlocfilehash: c676355ebf44d6cc02bfa66ac870757627ae5a58
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754807"
---
# <a name="ccontextmenumanager-class"></a>Klasa CContextMenuManager

Obiekt `CContextMenuManager` zarządza menu skrótów, znany również jako menu kontekstowe.

## <a name="syntax"></a>Składnia

```
class CContextMenuManager : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CContextMenuManager::CContextMenuManager](#ccontextmenumanager)|Konstruuje `CContextMenuManager` obiekt.|
|`CContextMenuManager::~CContextMenuManager`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CContextMenuManager::Dodajmenu](#addmenu)|Dodaje nowe menu skrótów.|
|[CContextMenuManager::GetMenuById](#getmenubyid)|Zwraca dojście do menu skojarzonego z podanym identyfikatorem zasobu.|
|[CContextMenuManager::GetMenuByName](#getmenubyname)|Zwraca dojście do menu, które pasuje do podanej nazwy menu.|
|[CContextMenuManager::GetMenuNames](#getmenunames)|Zwraca listę nazw menu.|
|[CContextMenuManager::LoadState](#loadstate)|Ładuje menu skrótów przechowywane w rejestrze systemu Windows.|
|[CContextMenuManager::ResetState](#resetstate)|Czyści menu skrótów z menedżera menu kontekstowego.|
|[CContextMenuManager::Zapisz stan](#savestate)|Zapisuje menu skrótów w rejestrze systemu Windows.|
|[CContextMenuManager::SetDontCloseActiveMenu](#setdontcloseactivemenu)|Określa, `CContextMenuManager` czy menu aktywnych skrótów zamyka się po wyświetleniu nowego menu skrótów.|
|[CContextMenuManager::ShowPopupMenu](#showpopupmenu)|Wyświetla określone menu skrótów.|
|[CContextMenuManager::TrackPopupMenu](#trackpopupmenu)|Wyświetla określone menu skrótów. Zwraca indeks wybranego polecenia menu.|

## <a name="remarks"></a>Uwagi

`CContextMenuManager`zarządza menu skrótów i upewnia się, że mają one spójny wygląd.

Obiektu nie należy `CContextMenuManager` tworzyć ręcznie. Struktura aplikacji tworzy `CContextMenuManager` obiekt. Jednak należy wywołać [CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) po zainicjowaniu aplikacji. Po zainicjowaniu menedżera kontekstu, użyj metody [CWinAppEx::GetContextMenuManager,](../../mfc/reference/cwinappex-class.md#getcontextmenumanager) aby uzyskać wskaźnik do menedżera kontekstu dla aplikacji.

Menu skrótów można tworzyć w `AddMenu`czasie wykonywania, wywołując program . Jeśli chcesz wyświetlić menu bez uprzedniego odbierania danych wejściowych użytkownika, zadzwoń `ShowPopupMenu`. `TrackPopupMenu`jest używany, gdy chcesz utworzyć menu i czekać na dane wejściowe użytkownika. `TrackPopupMenu`zwraca indeks wybranego polecenia lub 0, jeśli użytkownik zakończył pracę bez wybierania czegokolwiek.

Można `CContextMenuManager` również zapisać i załadować swój stan do rejestru systemu Windows.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CContextMenuManager` dodać menu do obiektu i jak nie `CContextMenuManager` zamykać aktywnego menu podręcznego, gdy obiekt wyświetla nowe menu podręczne. Ten fragment kodu jest częścią [przykładu Strony niestandardowe](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/cpp/ccontextmenumanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CContextMenuManager`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcontextmenumanager.h

## <a name="ccontextmenumanageraddmenu"></a><a name="addmenu"></a>CContextMenuManager::Dodajmenu

Dodaje nowe menu skrótów do [programu CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

```
BOOL AddMenu(
    UINT uiMenuNameResId,
    UINT uiMenuResId);

BOOL AddMenu(
    LPCTSTR lpszName,
    UINT uiMenuResId);
```

### <a name="parameters"></a>Parametry

*interfejs użytkownika uiMenuNameResId*<br/>
[w] Identyfikator zasobu dla ciągu zawierającego nazwę nowego menu.

*interfejs użytkownika uiMenuResId*<br/>
[w] Identyfikator zasobu menu.

*Lpszname*<br/>
[w] Ciąg zawierający nazwę nowego menu.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli metoda zakończyła się pomyślnie; 0, jeśli metoda nie powiedzie się.

### <a name="remarks"></a>Uwagi

Ta metoda kończy się *niepowodzeniem, jeśli uiMenuResId* jest nieprawidłowy lub jeśli inne menu o tej samej nazwie jest już w `CContextMenuManager`.

## <a name="ccontextmenumanagerccontextmenumanager"></a><a name="ccontextmenumanager"></a>CContextMenuManager::CContextMenuManager

Konstruuje [obiekt CContextMenuManager.](../../mfc/reference/ccontextmenumanager-class.md)

```
CContextMenuManager();
```

### <a name="remarks"></a>Uwagi

W większości przypadków nie należy `CContextMenuManager` tworzyć ręcznie. Struktura aplikacji tworzy `CContextMenuManager` obiekt. Należy wywołać [CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) podczas inicjowania aplikacji. Aby uzyskać wskaźnik do menedżera kontekstu, zadzwoń [CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager).

## <a name="ccontextmenumanagergetmenubyid"></a><a name="getmenubyid"></a>CContextMenuManager::GetMenuById

Zwraca dojście do menu skojarzonego z danym identyfikatorem zasobu.

```
HMENU GetMenuById(UINT nMenuResId) const;
```

### <a name="parameters"></a>Parametry

*nMenuResId*<br/>
[w] Identyfikator zasobu dla menu.

### <a name="return-value"></a>Wartość zwracana

Uchwyt do skojarzonego menu `NULL` lub jeśli nie znaleziono menu.

## <a name="ccontextmenumanagergetmenubyname"></a><a name="getmenubyname"></a>CContextMenuManager::GetMenuByName

Zwraca uchwyt do określonego menu.

```
HMENU GetMenuByName(
    LPCTSTR lpszName,
    UINT* puiOrigResID = NULL) const;
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
[w] Ciąg zawierający nazwę menu do pobrania.

*puiOrigResID*<br/>
[na zewnątrz] Wskaźnik do UINT. Ten parametr zawiera identyfikator zasobu określonego menu, jeśli zostanie znaleziony.

### <a name="return-value"></a>Wartość zwracana

Dojście do menu, które pasuje do nazwy określonej przez *lpszName*. NULL, jeśli nie ma menu o nazwie *lpszName*.

### <a name="remarks"></a>Uwagi

Jeśli ta metoda znajdzie menu zgodne z `GetMenuByName` *lpszName,* przechowuje identyfikator zasobu menu w parametrze *puiOrigResID*.

## <a name="ccontextmenumanagergetmenunames"></a><a name="getmenunames"></a>CContextMenuManager::GetMenuNames

Zwraca listę nazw menu dodanych do [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

```cpp
void GetMenuNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>Parametry

*nazwa listy*<br/>
[na zewnątrz] Odwołanie do [parametru CStringList.](../../mfc/reference/cstringlist-class.md) Ta metoda zapisuje listę nazw menu do tego parametru.

## <a name="ccontextmenumanagerloadstate"></a><a name="loadstate"></a>CContextMenuManager::LoadState

Ładuje informacje skojarzone z [CContextMenuManager Klasy](../../mfc/reference/ccontextmenumanager-class.md) z rejestru systemu Windows.

```
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[w] Ciąg zawierający ścieżkę względną klucza rejestru.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli metoda zakończy się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Parametr *lpszProfileName* nie jest ścieżką bezwzględną wpisu rejestru. Jest to ścieżka względna, która jest dodawana na końcu domyślnego klucza rejestru dla aplikacji. Aby uzyskać lub ustawić domyślny klucz rejestru, należy użyć metod [CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) i [CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) odpowiednio.

Użyj metody [CContextMenuManager::SaveState,](#savestate) aby zapisać menu skrótów w rejestrze.

## <a name="ccontextmenumanagerresetstate"></a><a name="resetstate"></a>CContextMenuManager::ResetState

Usuwa wszystkie elementy z menu skrótów skojarzonych z [klasą CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

```
virtual BOOL ResetState();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli metoda zakończy się pomyślnie; FAŁSZ, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Ta metoda czyści menu podręczne i usuwa `CContextMenuManager`je z pliku .

## <a name="ccontextmenumanagersavestate"></a><a name="savestate"></a>CContextMenuManager::Zapisz stan

Zapisuje informacje skojarzone z [CContextMenuManager Klasy](../../mfc/reference/ccontextmenumanager-class.md) do rejestru systemu Windows.

```
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[w] Ciąg zawierający ścieżkę względną klucza rejestru.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli metoda zakończy się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Parametr *lpszProfileName* nie jest ścieżką bezwzględną wpisu rejestru. Jest to ścieżka względna, która jest dodawana na końcu domyślnego klucza rejestru dla aplikacji. Aby uzyskać lub ustawić domyślny klucz rejestru, należy użyć metod [CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) i [CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) odpowiednio.

Użyj metody [CContextMenuManager::LoadState,](#loadstate) aby załadować menu skrótów z rejestru.

## <a name="ccontextmenumanagersetdontcloseactivemenu"></a><a name="setdontcloseactivemenu"></a>CContextMenuManager::SetDontCloseActiveMenu

Określa, czy [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) zamyka aktywne menu podręczne, gdy wyświetla nowe menu podręczne.

```cpp
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parametry

*bStaw*<br/>
[w] Parametr logiczny, który określa, czy chcesz zamknąć aktywne menu podręczne. Wartość TRUE oznacza, że aktywne menu podręczne nie jest zamknięte. FALSE oznacza, że aktywne menu podręczne jest zamknięte.

### <a name="remarks"></a>Uwagi

Domyślnie `CContextMenuManager` zamyka aktywne menu podręczne.

## <a name="ccontextmenumanagershowpopupmenu"></a><a name="showpopupmenu"></a>CContextMenuManager::ShowPopupMenu

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

*interfejs użytkownika uiMenuResId*<br/>
[w] Identyfikator zasobu menu, które będzie wyświetlany w tej metodzie.

*X*<br/>
[w] Przesunięcie poziome menu skrótów we współrzędnych klienta.

*Y*<br/>
[w] Przesunięcie w pionie dla menu skrótów we współrzędnych klienta

*pWndOwner*<br/>
[w] Wskaźnik do okna nadrzędnego menu skrótów.

*bOwnMessage*<br/>
[w] Parametr logiczny wskazujący sposób kierowania wiadomości. Jeśli *bOwnMessage* jest FALSE, używana jest standardowa routing MFC. W przeciwnym razie *pWndOwner* odbiera wiadomości.

*hmenuPopup*<br/>
[w] Dojście menu, które ta metoda będzie wyświetlana.

*bAutoDestroj*<br/>
[w] Parametr logiczny wskazujący, czy menu zostanie automatycznie zniszczone.

*bPrawaAlign*<br/>
[w] Parametr logiczny wskazujący sposób wyrównania elementów menu. Jeśli *bRightAlign* jest TRUE, menu jest wyrównane do prawej dla kolejności czytania od prawej do lewej.

### <a name="return-value"></a>Wartość zwracana

Przeciążenie pierwszej metody zwraca nonzero, jeśli metoda pokazuje menu pomyślnie; w przeciwnym razie 0. Przeciążenie drugiej metody zwraca wskaźnik do [CMFCPopupMenu,](../../mfc/reference/cmfcpopupmenu-class.md) jeśli menu skrótów jest wyświetlane poprawnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Ta metoda przypomina metodę [CContextMenuManager::TrackPopupMenu](#trackpopupmenu) w tym obu metod wyświetlania menu skrótów. Zwraca `TrackPopupMenu` jednak indeks wybranego polecenia menu.

Jeśli parametr *bAutoDestroy* jest FALSE, należy ręcznie `DestroyMenu` wywołać metodę dziedziczoną, aby zwolnić zasoby pamięci. Domyślna implementacja `ShowPopupMenu` nie używa parametru *bAutoDestroy*. Jest on przeznaczony do użytku w przyszłości `CContextMenuManager` lub dla klas niestandardowych pochodzących z klasy .

## <a name="ccontextmenumanagertrackpopupmenu"></a><a name="trackpopupmenu"></a>CContextMenuManager::TrackPopupMenu

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
[w] Uchwyt menu skrótów wyświetlanych przez tę metodę.

*X*<br/>
[w] Przesunięcie poziome menu skrótów we współrzędnych klienta.

*Y*<br/>
[w] Przesunięcie w pionie dla menu skrótów we współrzędnych klienta.

*pWndOwner*<br/>
[w] Wskaźnik do okna nadrzędnego menu skrótów.

*bPrawaAlign*<br/>
[w] Parametr logiczny wskazujący sposób wyrównania elementów menu. Jeśli *bRightAlign* jest TRUE, menu jest wyrównane do prawej dla kolejności czytania od prawej do lewej. Jeśli *bRightAlign* jest FALSE, menu jest wyrównane do lewej dla kolejności czytania od lewej do prawej.

### <a name="return-value"></a>Wartość zwracana

Identyfikator polecenia menu polecenia wybranego przez użytkownika; 0, jeśli użytkownik zamknie menu skrótów bez wybierania polecenia menu.

### <a name="remarks"></a>Uwagi

Ta metoda działa jako wywołanie modalne, aby wyświetlić menu skrótów. Aplikacja nie będzie kontynuować do następującego wiersza w kodzie, dopóki użytkownik nie zamknie menu skrótów lub nie wybierze polecenia. Alternatywną metodą, której można użyć do wyświetlenia menu skrótów, jest [CContextMenuManager::ShowPopupMenu](#showpopupmenu). Ta metoda nie jest wywołaniem modalnym i nie zwróci identyfikatora wybranego polecenia.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)
