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
ms.openlocfilehash: 49e9b1cd12bee562daaf4ffb40492c80d8549ec3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50639349"
---
# <a name="ccontextmenumanager-class"></a>Klasa CContextMenuManager

`CContextMenuManager` Obiektu zarządza menu skrótów, nazywane także menu kontekstowe.

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
|[CContextMenuManager::GetMenuById](#getmenubyid)|Zwraca uchwyt do menu skojarzony z identyfikatorem udostępnionego zasobu.|
|[CContextMenuManager::GetMenuByName](#getmenubyname)|Zwraca uchwyt do menu, który odpowiada nazwie podanej menu.|
|[CContextMenuManager::GetMenuNames](#getmenunames)|Zwraca listę nazw menu.|
|[CContextMenuManager::LoadState](#loadstate)|Ładuje menu skrótów, przechowywane w rejestrze systemu Windows.|
|[CContextMenuManager::ResetState](#resetstate)|Czyści menu skrótów z Menedżera menu kontekstowego.|
|[CContextMenuManager::SaveState](#savestate)|Zapisuje menu skrótów w rejestrze systemu Windows.|
|[CContextMenuManager::SetDontCloseActiveMenu](#setdontcloseactivemenu)|Formanty czy `CContextMenuManager` zamyka się menu skrótów aktywne, gdy pokazuje nowe menu skrótów.|
|[CContextMenuManager::ShowPopupMenu](#showpopupmenu)|Wyświetla menu skrótów określony.|
|[CContextMenuManager::TrackPopupMenu](#trackpopupmenu)|Wyświetla menu skrótów określony. Zwraca indeks polecenia menu wybrane.|

## <a name="remarks"></a>Uwagi

`CContextMenuManager` zarządza menu skrótów i upewnia się, że mają one spójny wygląd.

Nie należy tworzyć `CContextMenuManager` obiektu ręcznie. Szablon aplikacja tworzy `CContextMenuManager` obiektu. Jednakże, należy wywołać [CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) po zainicjowaniu aplikacji. Po inicjowania Menedżera kontekstu, użyj metody [CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager) uzyskać wskaźnik do Menedżera kontekstu dla aplikacji.

Menu skrótów w czasie wykonywania można utworzyć przez wywołanie metody `AddMenu`. Jeśli chcesz wyświetlić menu bez pierwszy odbierania danych wejściowych użytkownika, wywołaj `ShowPopupMenu`. `TrackPopupMenu` jest używany, gdy użytkownik chce utworzyć menu i czeka na dane wejściowe użytkownika. `TrackPopupMenu` Zwraca indeks wybranego polecenia lub 0, jeśli użytkownik zakończył działanie bez zaznaczania żadnych.

`CContextMenuManager` Można także zapisać i załadować jej stan w rejestrze Windows.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak dodać menu `CContextMenuManager` obiektu oraz sposób nie Zamknij aktywne menu podręczne podczas `CContextMenuManager` obiekt wyświetla nowe menu podręcznego. Ten fragment kodu jest częścią [przykładowe niestandardowych stron](../../visual-cpp-samples.md).

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

*uiMenuNameResId*<br/>
[in] Identyfikator zasobu ciągu zawierającego nazwę nowego menu.

*uiMenuResId*<br/>
[in] Identyfikator zasobu menu

*lpszName*<br/>
[in] Ciąg, który zawiera nazwę nowego menu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli metoda zakończyła się pomyślnie; 0, jeśli metoda nie powiedzie się.

### <a name="remarks"></a>Uwagi

Ta metoda kończy się niepowodzeniem, jeśli *uiMenuResId* jest nieprawidłowa lub jeśli innym menu o takiej samej nazwie jest już w `CContextMenuManager`.

##  <a name="ccontextmenumanager"></a>  CContextMenuManager::CContextMenuManager

Konstruuje [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) obiektu.

```
CContextMenuManager();
```

### <a name="remarks"></a>Uwagi

W większości przypadków nie należy tworzyć `CContextMenuManager` ręcznie. Szablon aplikacja tworzy `CContextMenuManager` obiektu. Należy wywołać [CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) podczas inicjowania aplikacji. Aby uzyskać wskaźnik do Menedżera kontekstu, należy wywołać [CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager).

##  <a name="getmenubyid"></a>  CContextMenuManager::GetMenuById

Zwraca uchwyt do menu skojarzonych z identyfikatorem zasobu.

```
HMENU GetMenuById(UINT nMenuResId) const;
```

### <a name="parameters"></a>Parametry

*nMenuResId*<br/>
[in] Identyfikator zasobu menu.

### <a name="return-value"></a>Wartość zwracana

Dojście do związanych z menu lub `NULL` Jeśli menu nie zostanie znaleziony.

##  <a name="getmenubyname"></a>  CContextMenuManager::GetMenuByName

Zwraca uchwyt do określonego menu.

```
HMENU GetMenuByName(
    LPCTSTR lpszName,
    UINT* puiOrigResID = NULL) const;
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
[in] Ciąg, który zawiera nazwę menu aby pobrać.

*puiOrigResID*<br/>
[out] Wskaźnik do UINT. Ten parametr zawiera menu określony identyfikator zasobu, jeśli znaleziono.

### <a name="return-value"></a>Wartość zwracana

Dojście do menu które jest zgodna z nazwą określoną przez *lpszName*. Wartość NULL, jeśli ma nie menu o nazwie *lpszName*.

### <a name="remarks"></a>Uwagi

Jeśli ta metoda umożliwia znalezienie menu, który odpowiada *lpszName*, `GetMenuByName` przechowuje identyfikator zasobu menu w parametrze *puiOrigResID*.

##  <a name="getmenunames"></a>  CContextMenuManager::GetMenuNames

Zwraca listę wszystkich nazw menu dodane do [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

```
void GetMenuNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>Parametry

*listOfNames*<br/>
[out] Odwołanie do [CStringList](../../mfc/reference/cstringlist-class.md) parametru. Ta metoda zapisuje listę nazw menu tego parametru.

##  <a name="loadstate"></a>  CContextMenuManager::LoadState

Ładuje informacje związane z [klasa CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) z rejestru Windows.

```
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[in] Ciąg, który zawiera ścieżkę względną do klucza rejestru.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli metoda się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

*LpszProfileName* parametr nie jest ścieżka bezwzględna wpisu rejestru. Jest ścieżką względną, który jest dodawany do końca domyślny klucz rejestru dla aplikacji. Aby pobrać lub ustawić domyślny klucz rejestru, należy użyć metod [CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) i [CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) odpowiednio.

Użyj metody [CContextMenuManager::SaveState](#savestate) można zapisać w menu skrótów w rejestrze.

##  <a name="resetstate"></a>  CContextMenuManager::ResetState

Czyści wszystkie elementy z menu skrótów, skojarzone z [klasa CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

```
virtual BOOL ResetState();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli metoda się powiedzie; Wartość FALSE, jeśli wystąpi awaria.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa wyskakujących menu i usuwa je z `CContextMenuManager`.

##  <a name="savestate"></a>  CContextMenuManager::SaveState

Zapisuje informacje związane z [klasa CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) do rejestru Windows.

```
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[in] Ciąg, który zawiera ścieżkę względną do klucza rejestru.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli metoda się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

*LpszProfileName* parametr nie jest ścieżka bezwzględna wpisu rejestru. Jest ścieżką względną, który jest dodawany do końca domyślny klucz rejestru dla aplikacji. Aby pobrać lub ustawić domyślny klucz rejestru, należy użyć metod [CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) i [CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) odpowiednio.

Użyj metody [CContextMenuManager::LoadState](#loadstate) załadować menu skrótów z rejestru.

##  <a name="setdontcloseactivemenu"></a>  CContextMenuManager::SetDontCloseActiveMenu

Formanty czy [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) zamyka aktywne menu podręczne, gdy wyświetla nowe menu podręcznego.

```
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parametry

*bUstawienie*<br/>
[in] Parametrów logiczny, który określa, czy Zamknij aktywne menu podręczne. Wartość TRUE wskazuje, że nie zamknięto aktywne menu podręczne. Wartość FALSE wskazuje, że aktywne menu podręczne jest zamknięty.

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

*uiMenuResId*<br/>
[in] Identyfikator zasobu menu, które spowoduje wyświetlenie tej metody.

*x*<br/>
[in] Poziome, przesunięcie do menu skrótów na liście współrzędne klienta.

*y*<br/>
[in] Przesunięcie w pionie do menu skrótów na liście współrzędne klienta

*pWndOwner*<br/>
[in] Wskaźnik do nadrzędnego okna w menu skrótów.

*bOwnMessage*<br/>
[in] Parametr logiczny, który wskazuje, jak wiadomości są przesyłane. Jeśli *bOwnMessage* jest wartość FALSE, standard MFC routing jest używany. W przeciwnym razie *pWndOwner* odbiera komunikaty.

*hmenuPopup*<br/>
[in] Uchwyt menu, które spowoduje wyświetlenie tej metody.

*bAutoDestroy*<br/>
[in] Parametr logiczny, który wskazuje, czy menu zostaną automatycznie usunięte.

*bRightAlign*<br/>
[in] Parametrów logiczny, który określa sposób wyrównania elementów menu. Jeśli *bRightAlign* ma wartość PRAWDA, menu jest wyrównany do prawej kolejność czytania od prawej do lewej.

### <a name="return-value"></a>Wartość zwracana

Pierwsze przeciążenie metody zwraca wartość różną od zera, jeśli metoda zawiera menu pomyślnie; w przeciwnym razie 0. Drugie przeciążenie metody zwraca wskaźnik do [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) Jeśli Wyświetla menu skrótów prawidłowy; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Ta metoda przypomina metody [CContextMenuManager::TrackPopupMenu](#trackpopupmenu) w tym, że obie metody wyświetli menu skrótów. Jednak `TrackPopupMenu` zwraca indeks polecenia menu wybrane.

Jeśli parametr *bAutoDestroy* ma wartość FAŁSZ, należy ręcznie wywołać dziedziczonego `DestroyMenu` metodę, aby zwolnić zasoby pamięci. Domyślna implementacja klasy `ShowPopupMenu` parametr nie *bAutoDestroy*. Jest ona udostępniana do użytku w przyszłości lub niestandardowych klas pochodnych `CContextMenuManager` klasy.

##  <a name="trackpopupmenu"></a>  CContextMenuManager::TrackPopupMenu

Wyświetla menu skrótów określonego i zwraca indeks polecenia w menu skrótów wybrane.

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
[in] Uchwyt menu skrótów, które zawiera tę metodę.

*x*<br/>
[in] Poziome, przesunięcie do menu skrótów na liście współrzędne klienta.

*y*<br/>
[in] Przesunięcie do menu skrótów na liście współrzędne klienta w pionie.

*pWndOwner*<br/>
[in] Wskaźnik do nadrzędnego okna w menu skrótów.

*bRightAlign*<br/>
[in] Parametrów logiczny, który określa sposób wyrównania elementów menu. Jeśli *bRightAlign* ma wartość PRAWDA, menu jest wyrównany do prawej kolejność czytania od prawej do lewej. Jeśli *bRightAlign* ma wartość FAŁSZ, menu jest wyrównany do lewej kolejność czytania od lewej do prawej.

### <a name="return-value"></a>Wartość zwracana

Identyfikator polecenia menu polecenia, gdy użytkownik wybierze; 0, jeśli użytkownik zamknie menu skrótów bez zaznaczania polecenia menu.

### <a name="remarks"></a>Uwagi

Ta metoda działa jako modalne wywołanie, aby wyświetlić menu skrótów. Aplikacja nie będzie następujący wiersz w kodzie dopóki użytkownik zamyka menu skrótów lub wybierze polecenie. Jest alternatywną metodę, której można użyć, aby wyświetlić menu skrótów [CContextMenuManager::ShowPopupMenu](#showpopupmenu). Tej metody nie jest wywołaniem modalne i nie będzie zwracać identyfikator wybranego polecenia.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)
