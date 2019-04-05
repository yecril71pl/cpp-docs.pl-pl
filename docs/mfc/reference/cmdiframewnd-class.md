---
title: Cmdiframewnd — klasa
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
ms.openlocfilehash: 9f5289491a7c14749865cfd163417440bc542aba
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776534"
---
# <a name="cmdiframewnd-class"></a>Cmdiframewnd — klasa

Oferuje funkcje Windows okna interfejsu wielu dokumentów (MDI) ramki, wraz z elementami członkowskimi do zarządzania oknem.

## <a name="syntax"></a>Składnia

```
class CMDIFrameWnd : public CFrameWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMDIFrameWnd::CMDIFrameWnd](#cmdiframewnd)|Konstruuje `CMDIFrameWnd`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMDIFrameWnd::CreateClient](#createclient)|Tworzy okno MdiClient — Windows, w tym `CMDIFrameWnd`. Wywoływane przez `OnCreate` funkcji składowej typu `CWnd`.|
|[CMDIFrameWnd::CreateNewChild](#createnewchild)|Tworzy nowe podrzędne okno.|
|[CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup)|Zwraca okno menu podręcznego.|
|[CMDIFrameWnd::MDIActivate](#mdiactivate)|Aktywuje różnych okno podrzędne MDI.|
|[CMDIFrameWnd::MDICascade](#mdicascade)|Rozmieszcza wszystkich okien podrzędnych w formacie kaskadowym.|
|[CMDIFrameWnd::MDIGetActive](#mdigetactive)|Pobiera aktualnie aktywne okno podrzędne MDI, wraz z Flaga wskazująca, czy element podrzędny jest zmaksymalizowane.|
|[CMDIFrameWnd::MDIIconArrange](#mdiiconarrange)|Rozmieszcza wszystkich okien podrzędnych dokumentu w trybie zminimalizowanym.|
|[CMDIFrameWnd::MDIMaximize](#mdimaximize)|Maksymalizuje okno podrzędne MDI.|
|[CMDIFrameWnd::MDINext](#mdinext)|Uaktywnia okna podrzędnego znajdującym się za okno podrzędne aktualnie aktywny, a następnie umieszcza okno podrzędne aktualnie aktywnego za inne okna podrzędnego.|
|[CMDIFrameWnd::MDIPrev](#mdiprev)|Aktywuje poprzednie okno podrzędne, a następnie umieszcza okno podrzędne aktualnie aktywne natychmiast związanych z nim.|
|[CMDIFrameWnd::MDIRestore](#mdirestore)|Przywraca okno podrzędne MDI na podstawie rozmiaru w trybie zmaksymalizowanym lub w trybie zminimalizowanym.|
|[CMDIFrameWnd::MDISetMenu](#mdisetmenu)|Zastępuje menu okna ramki MDI i/lub menu podręcznego okna.|
|[CMDIFrameWnd::MDITile](#mditile)|Rozmieszcza wszystkich okien podrzędnych w formacie fragmentacji.|

## <a name="remarks"></a>Uwagi

Aby utworzyć użyteczne okna ramki MDI dla aplikacji, należy wyprowadzić klasę z `CMDIFrameWnd`. Dodaj zmienne do klasy pochodnej w celu przechowywania danych specyficznych dla aplikacji. Implementowanie obsługi wiadomości elementów członkowskich, a także wiadomość, mapowania w klasie pochodnej, aby określić, co się stanie, gdy komunikaty są kierowane do okna.

Można utworzyć okna ramki MDI, wywołując [Utwórz](../../mfc/reference/cframewnd-class.md#create) lub [loadframe —](../../mfc/reference/cframewnd-class.md#loadframe) funkcji składowej typu `CFrameWnd`.

Przed wywołaniem `Create` lub `LoadFrame`, należy utworzyć obiekt okna ramki na stosie przy użyciu języka C++ **nowe** operatora. Przed wywołaniem `Create` można zarejestrować klasy okna za pomocą [afxregisterwndclass —](application-information-and-management.md#afxregisterwndclass) funkcja globalna, aby ustawić ikonę i klasa style ramki.

Użyj `Create` funkcja elementu członkowskiego do przekazania parametrów tworzenia ramki natychmiastowego jako argumenty.

`LoadFrame` wymaga mniej argumentów niż `Create`i zamiast tego pobiera najbardziej jej wartości domyślnej z zasobów, w tym podpis ramki, ikony, tabeli akceleratora i menu. Uzyskiwanie dostępu `LoadFrame`, te zasoby musi mieć ten sam identyfikator zasobów (na przykład IDR_MAINFRAME).

Chociaż `MDIFrameWnd` jest tworzony na podstawie `CFrameWnd`, pochodną klasę okna ramowego `CMDIFrameWnd` nie musi być zadeklarowana z `DECLARE_DYNCREATE`.

`CMDIFrameWnd` Klasa dziedziczy większość jego domyślna implementacja z `CFrameWnd`. Aby uzyskać szczegółową listę tych funkcji, zobacz [CFrameWnd](../../mfc/reference/cframewnd-class.md) klasy opis. `CMDIFrameWnd` Klasa ma następujące dodatkowe funkcje:

- Okno ramki MDI zarządza okno MDICLIENT, zmiana jego położenia w połączeniu z pasków sterowania. Okno klienckie MDI jest bezpośrednią lokacją nadrzędną okien ramek podrzędnych MDI. Style okna WS_HSCROLL i WS_VSCROLL określone na `CMDIFrameWnd` dotyczą okno klienckie MDI zamiast ramką głównego okna, dzięki czemu użytkownik może przewijać obszaru klienta MDI (tak jak Windows Menedżera programów, na przykład).

- Okno ramki MDI jest właścicielem menu domyślne, które jest używane jako pasek menu, gdy istnieje żadnego aktywnego okna podrzędnego MDI. W przypadku aktywnego elementu podrzędnego MDI pasek menu okna ramki MDI jest automatycznie zastępowany w menu okno podrzędne MDI.

- Okno ramki MDI działa w połączeniu z bieżącego okna podrzędnego MDI, jeśli taka istnieje. Na przykład komunikaty poleceń mają delegowane do aktualnie aktywnego elementu podrzędnego MDI przed oknem ramki aplikacji MDI.

- Okno ramki MDI ma obsługi domyślne dla następujących standardowego polecenia menu okna:

    - ID_WINDOW_TILE_VERT —

    - ID_WINDOW_TILE_HORZ

    - ID_WINDOW_CASCADE

    - ID_WINDOW_ARRANGE

- Okno ramki MDI ma również implementację id_window_new —, który umożliwia utworzenie nowej ramki i widok do bieżącego dokumentu. Aplikację można zastąpić te domyślnej implementacji polecenia, aby dostosować MDI okna obsługi.

Nie należy używać języka C++ **Usuń** operator można zniszczyć okna ramki. Zamiast nich należy używać słów kluczowych `CWnd::DestroyWindow`. `CFrameWnd` Implementacji `PostNcDestroy` spowoduje usunięcie obiektu języka C++, kiedy niszczony jest okna. Gdy użytkownik zamknie okno ramowe domyślnie `OnClose` wywoła procedurę obsługi `DestroyWindow`.

Aby uzyskać więcej informacji na temat `CMDIFrameWnd`, zobacz [Windows ramki](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIFrameWnd`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="cmdiframewnd"></a>  CMDIFrameWnd::CMDIFrameWnd

Konstruuje `CMDIFrameWnd` obiektu.

```
CMDIFrameWnd();
```

### <a name="remarks"></a>Uwagi

Wywołaj `Create` lub `LoadFrame` funkcji elementu członkowskiego, aby utworzyć widoczne oknem ramki aplikacji MDI.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#13](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_1.cpp)]

##  <a name="createclient"></a>  CMDIFrameWnd::CreateClient

Tworzy okno klienckie MDI, która zarządza `CMDIChildWnd` obiektów.

```
virtual BOOL CreateClient(
    LPCREATESTRUCT lpCreateStruct,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>Parametry

*lpCreateStruct*<br/>
Długie wskaźnik do [CREATESTRUCT](/windows/desktop/api/winuser/ns-winuser-tagcreatestructa) struktury.

*pWindowMenu*<br/>
Wskaźnik do menu podręcznego okna.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego powinna być wywoływana, jeśli zastąpisz `OnCreate` bezpośrednio funkcja elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#14](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_2.cpp)]

##  <a name="createnewchild"></a>  CMDIFrameWnd::CreateNewChild

Tworzy nowe podrzędne okno.

```
CMDIChildWnd* CreateNewChild(
    CRuntimeClass* pClass,
    UINT nResource,
    HMENU hMenu = NULL,
    HACCEL hAccel = NULL);
```

### <a name="parameters"></a>Parametry

*pClass*<br/>
Klasa czasu wykonywania okna podrzędnego, który ma zostać utworzony.

*Zasobów*<br/>
Identyfikator skojarzony z okna podrzędnego zasobów udostępnionych.

*hMenu*<br/>
Menu okna podrzędnego.

*hAccel*<br/>
Akcelerator okna podrzędnego.

### <a name="remarks"></a>Uwagi

Ta funkcja umożliwia utworzenie podrzędnych windows okna ramki MDI.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]

##  <a name="getwindowmenupopup"></a>  CMDIFrameWnd::GetWindowMenuPopup

Wywołaj tę funkcję elementu członkowskiego, można uzyskać dojścia do bieżącego menu podręczne o nazwie "Okno" (wyskakujących menu z elementami menu MDI okna zarządzania).

```
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```

### <a name="parameters"></a>Parametry

*hMenuBar*<br/>
Bieżący pasek menu.

### <a name="return-value"></a>Wartość zwracana

Menu wyskakujące okno, jeśli taki istnieje. w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Domyślna implementacja szuka zawierający standardowego polecenia menu okna, takie jak id_window_new — i id_window_tile_horz — menu podręcznego.

Jeśli masz menu okna, która nie korzysta z polecenia standardowe menu identyfikatorów, musi zostać zastąpiona tej funkcji elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#16](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]

##  <a name="mdiactivate"></a>  CMDIFrameWnd::MDIActivate

Aktywuje różnych okno podrzędne MDI.

```
void MDIActivate(CWnd* pWndActivate);
```

### <a name="parameters"></a>Parametry

*pWndActivate*<br/>
Wskazuje okno podrzędne MDI zostanie uaktywniony.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego wysyła [WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate) wiadomości do okna podrzędnego aktywowane i okna podrzędnego dezaktywowane.

Jest to ten sam komunikat, który jest wysyłana, gdy użytkownik zmieni fokus na okno podrzędne MDI za pomocą myszy lub klawiatury.

> [!NOTE]
>  Okno podrzędne MDI aktywowano niezależnie od oknem ramki aplikacji MDI. Podczas uaktywniania ramki okna podrzędnego, który został ostatnio aktywowany wysłaniu [WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate) wiadomości, aby narysować obramowanie aktywnego okna i pasek podpisu, ale nie otrzyma inny komunikat WM_MDIACTIVATE.

### <a name="example"></a>Przykład

Zobacz przykład [CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup).

##  <a name="mdicascade"></a>  CMDIFrameWnd::MDICascade

Rozmieszcza wszystkich okien podrzędnych MDI w formacie cascade.

```
void MDICascade();
void MDICascade(int nType);
```

### <a name="parameters"></a>Parametry

*nType*<br/>
Określa flagi cascade. Można określić tylko następujące flagi: MDITILE_SKIPDISABLED, co zapobiega on kaskadowy wyłączone oknami podrzędnymi MDI.

### <a name="remarks"></a>Uwagi

Pierwsza wersja `MDICascade`, bez parametrów, dokonuje kaskadowych wszystkich okien podrzędnych MDI, w tym wyłączone z nich. Druga wersja jest opcjonalnie nie cascade wyłączone oknami podrzędnymi MDI w przypadku określenia MDITILE_SKIPDISABLED dla *nNie* parametru.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]

##  <a name="mdigetactive"></a>  CMDIFrameWnd::MDIGetActive

Pobiera bieżące aktywne okno podrzędne MDI, oraz flagę wskazującą, czy jest zmaksymalizowane okno podrzędne.

```
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;
```

### <a name="parameters"></a>Parametry

*pbMaximized*<br/>
Wskaźnik do wartości zwracanej typu Logicznego. Wartość TRUE na powrót, jeśli okno jest zmaksymalizowane; w przeciwnym razie wartość FALSE.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do aktywnego okna podrzędnego MDI.

### <a name="example"></a>Przykład

Zobacz przykład [CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).

##  <a name="mdiiconarrange"></a>  CMDIFrameWnd::MDIIconArrange

Rozmieszcza wszystkich okien podrzędnych dokumentu w trybie zminimalizowanym.

```
void MDIIconArrange();
```

### <a name="remarks"></a>Uwagi

Nie ma wpływu na okien podrzędnych, które nie są zminimalizowane.

### <a name="example"></a>Przykład

Zobacz przykład [CMDIFrameWnd::MDICascade](#mdicascade).

##  <a name="mdimaximize"></a>  CMDIFrameWnd::MDIMaximize

Maksymalizuje określonego okna podrzędnego MDI.

```
void MDIMaximize(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskazuje okna w celu maksymalizacji.

### <a name="remarks"></a>Uwagi

Kiedy jest zmaksymalizowane okno podrzędne, zmienia rozmiar Windows, aby obszaru klienckiego Wypełnianie okna klienta. Windows umieszcza okno podrzędne menu kontroli na pasku menu ramki, dzięki czemu użytkownik może przywrócić lub zamknąć okno podrzędne. Dodaje także tytuł okna podrzędnego do tytułu ramki okna.

Jeśli inne okno podrzędne MDI jest aktywowany, gdy aktualnie aktywne okno podrzędne MDI jest zmaksymalizowane, Windows przywraca aktualnie aktywny element podrzędny i Maksymalizuje okno podrzędne nowo aktywowanego.

### <a name="example"></a>Przykład

Zobacz przykład [CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).

##  <a name="mdinext"></a>  CMDIFrameWnd::MDINext

Uaktywnia okna podrzędnego znajdującym się za okno podrzędne aktualnie aktywny, a następnie umieszcza okno podrzędne aktualnie aktywnego za inne okna podrzędnego.

```
void MDINext();
```

### <a name="remarks"></a>Uwagi

Jeśli aktualnie aktywne okno podrzędne MDI jest zmaksymalizowane, funkcja elementu członkowskiego przywraca aktualnie aktywny element podrzędny i maksymalizuje nowo aktywowanego elementu podrzędnego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]

##  <a name="mdiprev"></a>  CMDIFrameWnd::MDIPrev

Aktywuje poprzednie okno podrzędne, a następnie umieszcza okno podrzędne aktualnie aktywne natychmiast związanych z nim.

```
void MDIPrev();
```

### <a name="remarks"></a>Uwagi

Jeśli aktualnie aktywne okno podrzędne MDI jest zmaksymalizowane, funkcja elementu członkowskiego przywraca aktualnie aktywny element podrzędny i maksymalizuje nowo aktywowanego elementu podrzędnego.

##  <a name="mdirestore"></a>  CMDIFrameWnd::MDIRestore

Przywraca okno podrzędne MDI na podstawie rozmiaru w trybie zmaksymalizowanym lub w trybie zminimalizowanym.

```
void MDIRestore(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskazuje okna do przywrócenia.

### <a name="example"></a>Przykład

Zobacz przykład [CMDIChildWnd::MDIRestore](../../mfc/reference/cmdichildwnd-class.md#mdirestore).

##  <a name="mdisetmenu"></a>  CMDIFrameWnd::MDISetMenu

Zastępuje menu okna ramki MDI i/lub menu podręcznego okna.

```
CMenu* MDISetMenu(
    CMenu* pFrameMenu,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>Parametry

*pFrameMenu*<br/>
Określa menu nowe menu ramki okna. Jeśli ma wartość NULL, menu nie jest zmieniany.

*pWindowMenu*<br/>
Określa menu nowe menu podręcznego okna. Jeśli ma wartość NULL, menu nie jest zmieniany.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do menu Okno ramowe zastępuje ten komunikat. Wskaźnik mogą być tymczasowe i nie powinny być przechowywane do późniejszego użycia.

### <a name="remarks"></a>Uwagi

Po wywołaniu `MDISetMenu`, aplikacja musi wywołać [DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar) funkcji składowej typu `CWnd` do aktualizacji paska menu.

Jeśli to wywołanie zastępuje menu podręcznego okna, elementy menu okno podrzędne MDI są usuwane z poprzednim menu okna i dodane do nowego menu podręcznego okna.

Jeśli to wywołanie zastępuje menu okna ramki MDI jest zmaksymalizowane okno podrzędne MDI, kontroli wykonywanych menu i przywracania są usuwane z poprzednim menu Okno ramowe i dodany do menu Nowy.

Nie wywołuj tej funkcji elementu członkowskiego, jeśli używasz platformę do zarządzania z oknami podrzędnymi MDI.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#19](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]

[!code-cpp[NVC_MFCWindowing#20](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]

##  <a name="mditile"></a>  CMDIFrameWnd::MDITile

Rozmieszcza wszystkich okien podrzędnych w formacie fragmentacji.

```
void MDITile();
void MDITile(int nType);
```

### <a name="parameters"></a>Parametry

*nType*<br/>
Określa flagi fragmentacji. Ten parametr może być jednym z następujących flag:

- Oknami podrzędnymi MDI Kafelki MDITILE_HORIZONTAL, więc ten jedno okno pojawia się powyżej innym.

- Zapobiega MDITILE_SKIPDISABLED wyłączone oknami podrzędnymi MDI z jest podzielony na fragmenty.

- Oknami podrzędnymi MDI Kafelki MDITILE_VERTICAL, więc ten jedno okno pojawia się obok drugiego.

### <a name="remarks"></a>Uwagi

Pierwsza wersja `MDITile`, bez parametrów, Kafelki systemu windows w pionie, w obszarze Windows w wersji 3.1 lub nowszej. Druga wersja Kafelki systemu windows w pionie lub w poziomie, w zależności od wartości *nNie* parametru.

### <a name="example"></a>Przykład

Zobacz przykład [CMDIFrameWnd::MDICascade](#mdicascade).

## <a name="see-also"></a>Zobacz także

[Próbki MFC MDI](../../overview/visual-cpp-samples.md)<br/>
[Próbki MFC MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[Próbki MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[Diagram hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Cmdichildwnd — klasa](../../mfc/reference/cmdichildwnd-class.md)
