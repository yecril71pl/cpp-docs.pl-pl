---
title: Klasa CMDIFrameWnd
ms.date: 11/04/2016
f1_keywords:
- CMDIFrameWnd
- AFXWIN/CMDIFrameWnd
- AFXWIN/CMDIFrameWnd::CMDIFrameWnd
- AFXWIN/CMDIFrameWnd::CreateClient
- AFXWIN/CMDIFrameWnd::CreateNewChild
- AFXWIN/CMDIFrameWnd::GetWindowMenuPopup
- AFXWIN/CMDIFrameWnd::MDIActivate
- AFXWIN/CMDIFrameWnd::MDICascade
- AFXWIN/CMDIFrameWnd::MDIGetActive
- AFXWIN/CMDIFrameWnd::MDIIconArrange
- AFXWIN/CMDIFrameWnd::MDIMaximize
- AFXWIN/CMDIFrameWnd::MDINext
- AFXWIN/CMDIFrameWnd::MDIPrev
- AFXWIN/CMDIFrameWnd::MDIRestore
- AFXWIN/CMDIFrameWnd::MDISetMenu
- AFXWIN/CMDIFrameWnd::MDITile
helpviewer_keywords:
- CMDIFrameWnd [MFC], CMDIFrameWnd
- CMDIFrameWnd [MFC], CreateClient
- CMDIFrameWnd [MFC], CreateNewChild
- CMDIFrameWnd [MFC], GetWindowMenuPopup
- CMDIFrameWnd [MFC], MDIActivate
- CMDIFrameWnd [MFC], MDICascade
- CMDIFrameWnd [MFC], MDIGetActive
- CMDIFrameWnd [MFC], MDIIconArrange
- CMDIFrameWnd [MFC], MDIMaximize
- CMDIFrameWnd [MFC], MDINext
- CMDIFrameWnd [MFC], MDIPrev
- CMDIFrameWnd [MFC], MDIRestore
- CMDIFrameWnd [MFC], MDISetMenu
- CMDIFrameWnd [MFC], MDITile
ms.assetid: fa8736e6-511b-4c51-8b4d-eba78378aeb9
ms.openlocfilehash: 321ad0364257d7c20d54f9fdc884073381117c6f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222956"
---
# <a name="cmdiframewnd-class"></a>Klasa CMDIFrameWnd

Oferuje funkcje okna ramki interfejsu Wielodokumentowego (MDI) systemu Windows wraz z elementami członkowskimi do zarządzania oknem.

## <a name="syntax"></a>Składnia

```
class CMDIFrameWnd : public CFrameWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMDIFrameWnd::CMDIFrameWnd](#cmdiframewnd)|Konstruuje a `CMDIFrameWnd` .|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMDIFrameWnd:: isclient](#createclient)|Tworzy okno MDICLIENT systemu Windows `CMDIFrameWnd` . Wywoływane przez `OnCreate` funkcję członkowską `CWnd` .|
|[CMDIFrameWnd::CreateNewChild](#createnewchild)|Tworzy nowe okno podrzędne.|
|[CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup)|Zwraca menu wyskakujące okna.|
|[CMDIFrameWnd::MDIActivate](#mdiactivate)|Aktywuje inne podrzędne okno MDI.|
|[CMDIFrameWnd::MDICascade](#mdicascade)|Rozmieszcza wszystkie okna podrzędne w formacie kaskadowym.|
|[CMDIFrameWnd::MDIGetActive](#mdigetactive)|Pobiera aktualnie aktywne okno podrzędne MDI wraz z flagą wskazującą, czy element podrzędny jest zmaksymalizowany.|
|[CMDIFrameWnd::MDIIconArrange](#mdiiconarrange)|Rozmieszcza wszystkie zminimalizowane okna podrzędne dokumentu.|
|[CMDIFrameWnd::MDIMaximize](#mdimaximize)|Maksymalizuje okno podrzędne MDI.|
|[CMDIFrameWnd::MDINext](#mdinext)|Umożliwia aktywowanie okna podrzędnego bezpośrednio za aktualnie aktywnym oknem podrzędnym i umieszczenie aktualnie aktywnego okna podrzędnego za wszystkimi innymi oknami podrzędnymi.|
|[CMDIFrameWnd::MDIPrev](#mdiprev)|Uaktywnia poprzednie okno podrzędne i umieszcza aktualnie aktywne okno podrzędne bezpośrednio za nim.|
|[CMDIFrameWnd::MDIRestore](#mdirestore)|Przywraca rozmiar okna podrzędnego MDI z zmaksymalizowanej lub zminimalizowanej.|
|[CMDIFrameWnd::MDISetMenu](#mdisetmenu)|Zastępuje menu okna ramki MDI, menu podręcznego okna lub obu tych elementów.|
|[CMDIFrameWnd::MDITile](#mditile)|Rozmieszcza wszystkie okna podrzędne w formacie z układem sąsiadującym.|

## <a name="remarks"></a>Uwagi

Aby utworzyć użyteczne okno ramki MDI dla swojej aplikacji, Utwórz klasę z `CMDIFrameWnd` . Dodaj Zmienne Członkowskie do klasy pochodnej, aby przechowywać dane specyficzne dla aplikacji. Implementuj funkcje składowe programu obsługi komunikatów i mapę komunikatów w klasie pochodnej, aby określić, co się dzieje w przypadku kierowania komunikatów do okna.

Można utworzyć okno ramki MDI, wywołując funkcję członkowską [Create](../../mfc/reference/cframewnd-class.md#create) lub [LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe) `CFrameWnd` .

Przed wywołaniem `Create` lub należy `LoadFrame` skonstruować obiekt okna ramki na stercie przy użyciu **`new`** operatora C++. Przed wywołaniem `Create` można również zarejestrować klasę okna przy użyciu funkcji globalnej [AfxRegisterWndClass —](application-information-and-management.md#afxregisterwndclass) , aby ustawić style ikon i klas dla ramki.

Użyj `Create` funkcji członkowskiej, aby przekazać parametry tworzenia ramki jako natychmiastowe argumenty.

`LoadFrame`wymaga mniej argumentów niż `Create` , a zamiast tego pobiera większość wartości domyślnych z zasobów, w tym podpis ramki, ikonę, tabelę akceleratorów i menu. Aby uzyskać dostęp do programu `LoadFrame` , wszystkie te zasoby muszą mieć ten sam identyfikator zasobu (na przykład IDR_MAINFRAME).

Chociaż pochodzi `MDIFrameWnd` od `CFrameWnd` , Klasa okna ramki pochodnego od `CMDIFrameWnd` nie musi być zadeklarowana przy użyciu `DECLARE_DYNCREATE` .

`CMDIFrameWnd`Klasa dziedziczy większość implementacji domyślnej z `CFrameWnd` . Aby uzyskać szczegółową listę tych funkcji, zapoznaj się z opisem klasy [obiektu CFrameWnd](../../mfc/reference/cframewnd-class.md) . `CMDIFrameWnd`Klasa ma następujące dodatkowe funkcje:

- Okno ramka MDI zarządza oknem MDICLIENT, umieszczając je w połączeniu z paskami sterowania. Okno klienta MDI jest bezpośrednim elementem nadrzędnym okien ramki podrzędnej MDI. Style okna WS_HSCROLL i WS_VSCROLL określone w `CMDIFrameWnd` odniesieniu do okna klienta MDI zamiast okna ramki głównej, dzięki czemu użytkownik może przewijać obszar klienta MDI (jak na przykład w Menedżerze programów systemu Windows).

- Okno ramki MDI jest właścicielem domyślnego menu, które jest używane jako pasek menu, gdy nie ma aktywnego okna podrzędnego MDI. W przypadku aktywnego elementu podrzędnego MDI pasek menu okna ramki MDI jest automatycznie zastępowany przez menu podrzędnego interfejsu MDI.

- Okno ramek MDI działa w połączeniu z bieżącym oknem podrzędnym MDI, jeśli istnieje. Na przykład komunikaty poleceń są delegowane do aktualnie aktywnego elementu podrzędnego MDI przed oknem ramki MDI.

- Okno ramek MDI ma domyślne programy obsługi dla następujących poleceń menu standardowego okna:

  - ID_WINDOW_TILE_VERT

  - ID_WINDOW_TILE_HORZ

  - ID_WINDOW_CASCADE

  - ID_WINDOW_ARRANGE

- Okno ramki MDI zawiera również implementację ID_WINDOW_NEW, która tworzy nową ramkę i widok w bieżącym dokumencie. Aplikacja może zastąpić te domyślne implementacje poleceń, aby dostosować obsługę okna MDI.

Nie używaj **`delete`** operatora C++ do niszczenia okna ramki. Zamiast tego użyj polecenia cmdlet `CWnd::DestroyWindow`. `CFrameWnd`Implementacja programu `PostNcDestroy` spowoduje usunięcie obiektu C++, gdy okno zostanie zniszczone. Gdy użytkownik zamknie okno ramki, domyślnie `OnClose` zostanie wywołana procedura obsługi `DestroyWindow` .

Aby uzyskać więcej informacji na temat `CMDIFrameWnd` , zobacz [okna ramek](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIFrameWnd`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

## <a name="cmdiframewndcmdiframewnd"></a><a name="cmdiframewnd"></a>CMDIFrameWnd::CMDIFrameWnd

Konstruuje `CMDIFrameWnd` obiekt.

```
CMDIFrameWnd();
```

### <a name="remarks"></a>Uwagi

Wywołaj `Create` `LoadFrame` funkcję elementu członkowskiego, aby utworzyć widoczne okno ramki MDI.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#13](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_1.cpp)]

## <a name="cmdiframewndcreateclient"></a><a name="createclient"></a>CMDIFrameWnd:: isclient

Tworzy okno klienta MDI, które zarządza `CMDIChildWnd` obiektami.

```
virtual BOOL CreateClient(
    LPCREATESTRUCT lpCreateStruct,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>Parametry

*lpCreateStruct*<br/>
Długi wskaźnik [do struktury elementu](/windows/win32/api/winuser/ns-winuser-createstructw) .

*pWindowMenu*<br/>
Wskaźnik do menu podręcznego okna.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska powinna być wywoływana, jeśli przesłonisz `OnCreate` funkcję elementu członkowskiego bezpośrednio.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#14](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_2.cpp)]

## <a name="cmdiframewndcreatenewchild"></a><a name="createnewchild"></a>CMDIFrameWnd::CreateNewChild

Tworzy nowe okno podrzędne.

```
CMDIChildWnd* CreateNewChild(
    CRuntimeClass* pClass,
    UINT nResource,
    HMENU hMenu = NULL,
    HACCEL hAccel = NULL);
```

### <a name="parameters"></a>Parametry

*pClass*<br/>
Klasa czasu wykonywania tworzonego okna podrzędnego.

*nResource*<br/>
Identyfikator zasobów udostępnionych skojarzonych z oknem podrzędnym.

*hMenu*<br/>
Menu okna podrzędnego.

*hAccel*<br/>
Akcelerator okna podrzędnego.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do tworzenia okien podrzędnych okna ramki MDI.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]

## <a name="cmdiframewndgetwindowmenupopup"></a><a name="getwindowmenupopup"></a>CMDIFrameWnd::GetWindowMenuPopup

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać uchwyt do bieżącego menu podręcznego o nazwie "okno" (menu podręczne z elementami menu dla zarządzania oknem MDI).

```
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```

### <a name="parameters"></a>Parametry

*hMenuBar*<br/>
Bieżący pasek menu.

### <a name="return-value"></a>Wartość zwracana

Menu rozwijane okno, jeśli taki istnieje; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wyszukuje menu podręczne zawierające polecenia menu standardowego okna, takie jak ID_WINDOW_NEW i ID_WINDOW_TILE_HORZ.

Zastąp tę funkcję elementu członkowskiego, jeśli masz menu okna, które nie używa standardowych identyfikatorów poleceń menu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#16](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]

## <a name="cmdiframewndmdiactivate"></a><a name="mdiactivate"></a>CMDIFrameWnd::MDIActivate

Aktywuje inne podrzędne okno MDI.

```cpp
void MDIActivate(CWnd* pWndActivate);
```

### <a name="parameters"></a>Parametry

*pWndActivate*<br/>
Wskazuje okno potomne MDI, które ma zostać aktywowane.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska wysyła komunikat [WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate) do aktywowanego okna podrzędnego i dezaktywowanego okna podrzędnego.

Jest to ten sam komunikat, który jest wysyłany, gdy użytkownik zmieni fokus w oknie podrzędnym MDI przy użyciu myszy lub klawiatury.

> [!NOTE]
> Okno podrzędne MDI jest aktywowane niezależnie od okna ramki MDI. Gdy ramka zostanie uaktywniona, okno podrzędne, które było ostatnio aktywowane, jest wysyłane [WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate) komunikatem, aby narysować ramkę aktywnego okna i pasek napisów, ale nie otrzymają kolejnego komunikatu WM_MDIACTIVATE.

### <a name="example"></a>Przykład

Zobacz przykład dla [CMDIFrameWnd:: GetWindowMenuPopup](#getwindowmenupopup).

## <a name="cmdiframewndmdicascade"></a><a name="mdicascade"></a>CMDIFrameWnd::MDICascade

Rozmieszcza wszystkie okna podrzędne MDI w formacie kaskadowym.

```cpp
void MDICascade();
void MDICascade(int nType);
```

### <a name="parameters"></a>Parametry

*Npowiadomienia*<br/>
Określa flagę kaskadową. Można określić tylko następującą flagę: MDITILE_SKIPDISABLED, co uniemożliwia kaskadowe wyświetlanie okien podrzędnych MDI.

### <a name="remarks"></a>Uwagi

Pierwsza wersja programu `MDICascade` , bez parametrów, kaskaduje wszystkie okna podrzędne MDI, w tym wyłączone. Druga wersja opcjonalnie nie powoduje kaskadowego wyłączania okien podrzędnych MDI, jeśli określono MDITILE_SKIPDISABLED dla parametru *npowiadomienia* .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]

## <a name="cmdiframewndmdigetactive"></a><a name="mdigetactive"></a>CMDIFrameWnd::MDIGetActive

Pobiera bieżące aktywne okno podrzędne MDI wraz z flagą wskazującą, czy okno podrzędne jest zmaksymalizowane.

```
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;
```

### <a name="parameters"></a>Parametry

*pbMaximized*<br/>
Wskaźnik do LOGICZNEj wartości zwracanej. Ustaw na wartość TRUE, jeśli okno jest zmaksymalizowane; w przeciwnym razie FALSE.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do aktywnego okna podrzędnego MDI.

### <a name="example"></a>Przykład

Zobacz przykład dla [CMDIChildWnd:: MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).

## <a name="cmdiframewndmdiiconarrange"></a><a name="mdiiconarrange"></a>CMDIFrameWnd::MDIIconArrange

Rozmieszcza wszystkie zminimalizowane okna podrzędne dokumentu.

```cpp
void MDIIconArrange();
```

### <a name="remarks"></a>Uwagi

Nie ma to wpływu na okna podrzędne, które nie są zminimalizowane.

### <a name="example"></a>Przykład

Zobacz przykład dla [CMDIFrameWnd:: MDICascade](#mdicascade).

## <a name="cmdiframewndmdimaximize"></a><a name="mdimaximize"></a>CMDIFrameWnd::MDIMaximize

Maksymalizuje określone okno podrzędne MDI.

```cpp
void MDIMaximize(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskazuje okno, które ma zostać zmaksymalizowane.

### <a name="remarks"></a>Uwagi

Gdy okno podrzędne jest zmaksymalizowane, system Windows zmienia jego rozmiar, aby wypełniał okno klienta w obszarze klienta. System Windows umieści menu sterowania okna podrzędnego na pasku menu ramki, aby użytkownik mógł przywrócić lub zamknąć okno podrzędne. Dodaje również tytuł okna podrzędnego do tytułu okna ramki.

Jeśli inne okno podrzędne MDI jest aktywowane, gdy aktywne okno podrzędne MDI jest zmaksymalizowane, system Windows przywraca aktualnie aktywny element podrzędny i maksymalizuje nowo uaktywnione okno podrzędne.

### <a name="example"></a>Przykład

Zobacz przykład dla [CMDIChildWnd:: MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).

## <a name="cmdiframewndmdinext"></a><a name="mdinext"></a>CMDIFrameWnd::MDINext

Umożliwia aktywowanie okna podrzędnego bezpośrednio za aktualnie aktywnym oknem podrzędnym i umieszczenie aktualnie aktywnego okna podrzędnego za wszystkimi innymi oknami podrzędnymi.

```cpp
void MDINext();
```

### <a name="remarks"></a>Uwagi

Jeśli aktualnie aktywne okno podrzędne MDI jest zmaksymalizowane, funkcja członkowska przywraca aktualnie aktywny element podrzędny i maksymalizuje nowo uaktywniony element podrzędny.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]

## <a name="cmdiframewndmdiprev"></a><a name="mdiprev"></a>CMDIFrameWnd::MDIPrev

Uaktywnia poprzednie okno podrzędne i umieszcza aktualnie aktywne okno podrzędne bezpośrednio za nim.

```cpp
void MDIPrev();
```

### <a name="remarks"></a>Uwagi

Jeśli aktualnie aktywne okno podrzędne MDI jest zmaksymalizowane, funkcja członkowska przywraca aktualnie aktywny element podrzędny i maksymalizuje nowo uaktywniony element podrzędny.

## <a name="cmdiframewndmdirestore"></a><a name="mdirestore"></a>CMDIFrameWnd::MDIRestore

Przywraca rozmiar okna podrzędnego MDI z zmaksymalizowanej lub zminimalizowanej.

```cpp
void MDIRestore(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskazuje okno, które ma zostać przywrócone.

### <a name="example"></a>Przykład

Zobacz przykład dla [CMDIChildWnd:: MDIRestore](../../mfc/reference/cmdichildwnd-class.md#mdirestore).

## <a name="cmdiframewndmdisetmenu"></a><a name="mdisetmenu"></a>CMDIFrameWnd::MDISetMenu

Zastępuje menu okna ramki MDI, menu podręcznego okna lub obu tych elementów.

```
CMenu* MDISetMenu(
    CMenu* pFrameMenu,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>Parametry

*pFrameMenu*<br/>
Określa menu nowego okna z ramką. Jeśli wartość jest równa NULL, menu nie zostanie zmienione.

*pWindowMenu*<br/>
Określa menu nowego menu podręcznego okna. Jeśli wartość jest równa NULL, menu nie zostanie zmienione.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do menu okna z ramkami zastąpionych przez tę wiadomość. Wskaźnik może być tymczasowy i nie powinien być przechowywany do późniejszego użycia.

### <a name="remarks"></a>Uwagi

Po wywołaniu `MDISetMenu` aplikacja musi wywołać funkcję elementu członkowskiego [DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar) , `CWnd` Aby zaktualizować pasek menu.

Jeśli to wywołanie zastępuje menu podręcznego okna, elementy menu podrzędnego MDI są usuwane z menu poprzedniego okna i dodawane do nowego menu podręcznego okna.

Jeśli okno podrzędne MDI jest zmaksymalizowane, a to wywołanie zastępuje menu okna ramki MDI, menu sterowania i kontrolki przywracania zostaną usunięte z poprzedniego menu okna i dodane do nowego menu.

Nie wywołuj tej funkcji elementu członkowskiego, jeśli używasz platformy do zarządzania oknami podrzędnymi MDI.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#19](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]

[!code-cpp[NVC_MFCWindowing#20](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]

## <a name="cmdiframewndmditile"></a><a name="mditile"></a>CMDIFrameWnd::MDITile

Rozmieszcza wszystkie okna podrzędne w formacie z układem sąsiadującym.

```cpp
void MDITile();
void MDITile(int nType);
```

### <a name="parameters"></a>Parametry

*Npowiadomienia*<br/>
Określa flagę dzielenia. Ten parametr może mieć jedną z następujących flag:

- MDITILE_HORIZONTAL kafelki podrzędne okna MDI, aby jedno okno było wyświetlane powyżej innego okna.

- MDITILE_SKIPDISABLED uniemożliwia rozłączenie wyłączonych okien podrzędnych MDI.

- MDITILE_VERTICAL kafelki podrzędne okna MDI, aby jedno okno było wyświetlane obok innego.

### <a name="remarks"></a>Uwagi

Pierwsza wersja `MDITile` , bez parametrów, sąsiadująco w pionie w systemie Windows w wersji 3,1 i nowszych. Druga wersja składa w pionie lub poziomie systemu Windows, w zależności od wartości parametru *npowiadomienia* .

### <a name="example"></a>Przykład

Zobacz przykład dla [CMDIFrameWnd:: MDICascade](#mdicascade).

## <a name="see-also"></a>Zobacz także

[Przykładowy interfejs MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład MDIDOCVW MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład SNAPVW MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa obiektu CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Klasa CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)
