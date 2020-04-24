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
ms.openlocfilehash: d5c9bc12e6c3f0ab4742a940547087c9742caf73
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754547"
---
# <a name="cmdiframewnd-class"></a>Klasa CMDIFrameWnd

Udostępnia funkcje okna ramki interfejsu wielu dokumentów systemu Windows (MDI) wraz z członkami do zarządzania oknem.

## <a name="syntax"></a>Składnia

```
class CMDIFrameWnd : public CFrameWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMDIFrameWnd::CMDIFrameWnd](#cmdiframewnd)|Konstruuje `CMDIFrameWnd`plik .|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMDIFrameWnd::CreateClient](#createclient)|Tworzy dla tego `CMDIFrameWnd`okno MDICLIENT systemu Windows . Wywoływana `OnCreate` przez funkcję `CWnd`członkowki .|
|[CMDIFrameWnd::UtwórzNewChild](#createnewchild)|Tworzy nowe okno podrzędne.|
|[CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup)|Zwraca menu podręczne Okno.|
|[CMDIFrameWnd::MDIActivate](#mdiactivate)|Aktywuje inne okno podrzędne MDI.|
|[CMDIFrameWnd::MDICascade](#mdicascade)|Rozmieszcza wszystkie okna podrzędne w formacie kaskadowym.|
|[CMDIFrameWnd::MDIGetActive](#mdigetactive)|Pobiera aktualnie aktywne okno podrzędne MDI wraz z flagą wskazującą, czy dziecko jest zmaksymalizowane.|
|[CMDIFrameWnd::MDIIconArrange](#mdiiconarrange)|Rozmieszcza wszystkie zminimalizowane okna podrzędne dokumentu.|
|[CMDIFrameWnd::MDIMaximize](#mdimaximize)|Maksymalizuje okno podrzędne MDI.|
|[CMDIFrameWnd::MDINastępna](#mdinext)|Aktywuje okno podrzędne bezpośrednio za aktualnie aktywnym oknem podrzędnym i umieszcza aktualnie aktywne okno podrzędne za wszystkimi innymi oknami podrzędnymi.|
|[CMDIFrameWnd::MDIPrev](#mdiprev)|Aktywuje poprzednie okno podrzędne i umieszcza aktualnie aktywne okno podrzędne bezpośrednio za nim.|
|[CMDIFrameWnd::MDIRestore](#mdirestore)|Przywraca okno podrzędne MDI z maksymalnego lub zminimalizowanego rozmiaru.|
|[CMDIFrameWnd::MDISetMenu](#mdisetmenu)|Zastępuje menu okna ramki MDI, menu podręcznego Okno lub oba te opcje.|
|[CMDIFrameWnd::MDITile](#mditile)|Rozmieszcza wszystkie okna podrzędne w formacie kafelkowym.|

## <a name="remarks"></a>Uwagi

Aby utworzyć przydatne okno ramki MDI dla aplikacji, należy wyprowadzić klasę z pliku `CMDIFrameWnd`. Dodaj zmienne członkowskie do klasy pochodnej do przechowywania danych specyficznych dla aplikacji. Zaimplementuj funkcje członkowskie programu message-handler i mapę wiadomości w klasie pochodnej, aby określić, co się dzieje, gdy wiadomości są kierowane do okna.

Okno ramki MDI można utworzyć, wywołując funkcję elementu `CFrameWnd`członkowskiego [Create](../../mfc/reference/cframewnd-class.md#create) lub [LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe) .

Przed `Create` wywołaniem `LoadFrame`lub , należy skonstruować obiekt okna ramki na stosie przy użyciu **c++ nowy** operator. Przed `Create` wywołaniem można również zarejestrować klasę okna za pomocą [afxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) funkcji globalnej, aby ustawić ikonę i style klasy dla ramki.

Funkcja `Create` elementu członkowskiego służy do przekazywania parametrów tworzenia ramki jako argumentów natychmiastowych.

`LoadFrame`wymaga mniejszej `Create`liczby argumentów niż program , a zamiast tego pobiera większość wartości domyślnych z zasobów, w tym podpis ramki, ikonę, tabelę akceleratora i menu. Aby dostęp do `LoadFrame`nich był dostępny, wszystkie te zasoby muszą mieć ten sam identyfikator zasobu (na przykład IDR_MAINFRAME).

Chociaż `MDIFrameWnd` pochodzi od `CFrameWnd`, klasa okna ramki pochodzące `CMDIFrameWnd` `DECLARE_DYNCREATE`z nie muszą być zadeklarowane z .

Klasa `CMDIFrameWnd` dziedziczy większość swojej domyślnej implementacji z `CFrameWnd`. Aby uzyskać szczegółową listę tych funkcji, zobacz opis klasy [CFrameWnd.](../../mfc/reference/cframewnd-class.md) Klasa `CMDIFrameWnd` posiada następujące dodatkowe funkcje:

- Okno ramki MDI zarządza oknem MDICLIENT, przesuwając go w połączeniu z prętami sterującymi. Okno klienta MDI jest bezpośrednim elementem nadrzędnym okien ramek podrzędnych MDI. Style okna WS_HSCROLL i WS_VSCROLL określone w `CMDIFrameWnd` oknie klienta MDI, a nie w oknie ramki głównej, aby użytkownik mógł przewijać obszar klienta MDI (na przykład w Menedżerze programów systemu Windows).

- Okno ramki MDI jest właścicielem domyślnego menu, które jest używane jako pasek menu, gdy nie ma aktywnego okna podrzędnego MDI. Gdy istnieje aktywne dziecko MDI, pasek menu okna ramki MDI jest automatycznie zastępowany przez menu okna podrzędnego MDI.

- Okno ramki MDI działa w połączeniu z bieżącym podrzędnym oknem MDI, jeśli istnieje. Na przykład komunikaty poleceń są delegowane do aktualnie aktywnego dziecka MDI przed oknem ramki MDI.

- Okno ramki MDI ma domyślne programy obsługi dla następujących standardowych poleceń menu Okna:

  - ID_WINDOW_TILE_VERT

  - ID_WINDOW_TILE_HORZ

  - ID_WINDOW_CASCADE

  - ID_WINDOW_ARRANGE

- Okno ramki MDI ma również implementację ID_WINDOW_NEW, która tworzy nową ramkę i widok w bieżącym dokumencie. Aplikacja może zastąpić te domyślne implementacje poleceń, aby dostosować obsługę okien MDI.

Nie należy używać operatora **usuwania** języka C++, aby zniszczyć okno ramki. Zamiast tego użyj polecenia cmdlet `CWnd::DestroyWindow`. Implementacja `CFrameWnd` `PostNcDestroy` spowoduje usunięcie obiektu C++, gdy okno zostanie zniszczone. Gdy użytkownik zamknie okno ramki, wywoła domyślny `OnClose` program obsługi `DestroyWindow`.

Aby uzyskać `CMDIFrameWnd`więcej informacji na temat , zobacz [Ramka Systemu Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIFrameWnd`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cmdiframewndcmdiframewnd"></a><a name="cmdiframewnd"></a>CMDIFrameWnd::CMDIFrameWnd

Konstruuje `CMDIFrameWnd` obiekt.

```
CMDIFrameWnd();
```

### <a name="remarks"></a>Uwagi

Wywołanie `Create` `LoadFrame` funkcji lub elementu członkowskiego, aby utworzyć widoczne okno ramki MDI.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#13](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_1.cpp)]

## <a name="cmdiframewndcreateclient"></a><a name="createclient"></a>CMDIFrameWnd::CreateClient

Tworzy okno klienta MDI, `CMDIChildWnd` które zarządza obiektami.

```
virtual BOOL CreateClient(
    LPCREATESTRUCT lpCreateStruct,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>Parametry

*lpTwolać*<br/>
Długi wskaźnik do struktury [CREATESTRUCT.](/windows/win32/api/winuser/ns-winuser-createstructw)

*pWindowMenu*<br/>
Wskaźnik do wyskakującego menu Okno.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego powinna być `OnCreate` wywoływana, jeśli zastąpisz funkcję elementu członkowskiego bezpośrednio.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#14](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_2.cpp)]

## <a name="cmdiframewndcreatenewchild"></a><a name="createnewchild"></a>CMDIFrameWnd::UtwórzNewChild

Tworzy nowe okno podrzędne.

```
CMDIChildWnd* CreateNewChild(
    CRuntimeClass* pClass,
    UINT nResource,
    HMENU hMenu = NULL,
    HACCEL hAccel = NULL);
```

### <a name="parameters"></a>Parametry

*pClass (klasa pClass)*<br/>
Klasa wykonywania okna podrzędnego, które ma zostać utworzone.

*nŹródło*<br/>
Identyfikator zasobów udostępnionych skojarzonych z oknem podrzędnym.

*Hmenu*<br/>
Menu okna podrzędnego.

*hAccel (własówk.*<br/>
Akcelerator okna podrzędnego.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do tworzenia okien podrzędnych okna ramki MDI.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]

## <a name="cmdiframewndgetwindowmenupopup"></a><a name="getwindowmenupopup"></a>CMDIFrameWnd::GetWindowMenuPopup

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać dojście do bieżącego menu podręcznego o nazwie "Okno" (menu podręczne z elementami menu do zarządzania oknami MDI).

```
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```

### <a name="parameters"></a>Parametry

*hMenuBar (własnik)*<br/>
Bieżący pasek menu.

### <a name="return-value"></a>Wartość zwracana

Menu podręczne Okno, jeśli istnieje; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wyszukuje menu podręczne zawierające standardowe polecenia menu okna, takie jak ID_WINDOW_NEW i ID_WINDOW_TILE_HORZ.

Zastąpokaj tę funkcję elementu członkowskiego, jeśli masz menu Okno, które nie używa standardowych identyfikatorów poleceń menu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#16](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]

## <a name="cmdiframewndmdiactivate"></a><a name="mdiactivate"></a>CMDIFrameWnd::MDIActivate

Aktywuje inne okno podrzędne MDI.

```cpp
void MDIActivate(CWnd* pWndActivate);
```

### <a name="parameters"></a>Parametry

*pWndAktywniej*<br/>
Wskazuje okno podrzędne MDI, które ma zostać aktywowane.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego wysyła komunikat [WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate) do aktywowane okno podrzędne i okno podrzędne jest dezaktywowany.

Jest to ten sam komunikat, który jest wysyłany, jeśli użytkownik zmieni fokus na okno podrzędne MDI za pomocą myszy lub klawiatury.

> [!NOTE]
> Okno podrzędne MDI jest aktywowane niezależnie od okna ramki MDI. Gdy ramka stanie się aktywna, okno podrzędne, które zostało ostatnio aktywowane, jest wysyłane [WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate) wiadomości w celu narysowania aktywnej ramki okna i paska podpisu, ale nie otrzymuje innego komunikatu WM_MDIACTIVATE.

### <a name="example"></a>Przykład

Zobacz przykład [dla CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup).

## <a name="cmdiframewndmdicascade"></a><a name="mdicascade"></a>CMDIFrameWnd::MDICascade

Rozmieszcza wszystkie okna podrzędne MDI w formacie kaskadowym.

```cpp
void MDICascade();
void MDICascade(int nType);
```

### <a name="parameters"></a>Parametry

*nTyp*<br/>
Określa flagę kaskadową. Można określić tylko następującą flagę: MDITILE_SKIPDISABLED, co zapobiega kaskadowo wyłączonym oknom podrzędnym MDI.

### <a name="remarks"></a>Uwagi

Pierwsza wersja `MDICascade`, bez parametrów, kaskadowo wszystkie okna podrzędne MDI, w tym te wyłączone. Druga wersja opcjonalnie nie powoduje kaskadowej wyłączanie okien podrzędnych MDI, jeśli określisz MDITILE_SKIPDISABLED dla parametru *nType.*

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]

## <a name="cmdiframewndmdigetactive"></a><a name="mdigetactive"></a>CMDIFrameWnd::MDIGetActive

Pobiera bieżące aktywne okno podrzędne MDI wraz z flagą wskazującą, czy okno podrzędne jest zmaksymalizowane.

```
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;
```

### <a name="parameters"></a>Parametry

*pbMaximized*<br/>
Wskaźnik do wartości zwracanej BOOL. Ustaw wartość TRUE w zamian, jeśli okno jest zmaksymalizowane; w przeciwnym razie FALSE.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do aktywnego okna podrzędnego MDI.

### <a name="example"></a>Przykład

Zobacz przykład [dla CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).

## <a name="cmdiframewndmdiiconarrange"></a><a name="mdiiconarrange"></a>CMDIFrameWnd::MDIIconArrange

Rozmieszcza wszystkie zminimalizowane okna podrzędne dokumentu.

```cpp
void MDIIconArrange();
```

### <a name="remarks"></a>Uwagi

Nie ma to wpływu na okna podrzędne, które nie są zminimalizowane.

### <a name="example"></a>Przykład

Zobacz przykład [dla CMDIFrameWnd::MDICascade](#mdicascade).

## <a name="cmdiframewndmdimaximize"></a><a name="mdimaximize"></a>CMDIFrameWnd::MDIMaximize

Maksymalizuje określone okno podrzędne MDI.

```cpp
void MDIMaximize(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskazuje okno, aby zmaksymalizować.

### <a name="remarks"></a>Uwagi

Gdy okno podrzędne jest zmaksymalizowane, system Windows zmienia jego rozmiar, aby jego obszar klienta wypełniał okno klienta. System Windows umieszcza menu Sterowanie okna podrzędnego na pasku menu ramki, aby użytkownik mógł przywrócić lub zamknąć okno podrzędne. Dodaje również tytuł okna podrzędnego do tytułu okna ramki.

Jeśli inne okno podrzędne MDI jest aktywowane, gdy aktualnie aktywne okno podrzędne MDI jest zmaksymalizowane, system Windows przywraca aktualnie aktywne dziecko i maksymalizuje nowo aktywowane okno podrzędne.

### <a name="example"></a>Przykład

Zobacz przykład [dla CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).

## <a name="cmdiframewndmdinext"></a><a name="mdinext"></a>CMDIFrameWnd::MDINastępna

Aktywuje okno podrzędne bezpośrednio za aktualnie aktywnym oknem podrzędnym i umieszcza aktualnie aktywne okno podrzędne za wszystkimi innymi oknami podrzędnymi.

```cpp
void MDINext();
```

### <a name="remarks"></a>Uwagi

Jeśli aktualnie aktywne okno podrzędne MDI jest zmaksymalizowane, funkcja elementu członkowskiego przywraca aktualnie aktywny element podrzędny i maksymalizuje nowo aktywowane dziecko.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]

## <a name="cmdiframewndmdiprev"></a><a name="mdiprev"></a>CMDIFrameWnd::MDIPrev

Aktywuje poprzednie okno podrzędne i umieszcza aktualnie aktywne okno podrzędne bezpośrednio za nim.

```cpp
void MDIPrev();
```

### <a name="remarks"></a>Uwagi

Jeśli aktualnie aktywne okno podrzędne MDI jest zmaksymalizowane, funkcja elementu członkowskiego przywraca aktualnie aktywny element podrzędny i maksymalizuje nowo aktywowane dziecko.

## <a name="cmdiframewndmdirestore"></a><a name="mdirestore"></a>CMDIFrameWnd::MDIRestore

Przywraca okno podrzędne MDI z maksymalnego lub zminimalizowanego rozmiaru.

```cpp
void MDIRestore(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskazuje okno, aby przywrócić.

### <a name="example"></a>Przykład

Zobacz przykład [dla CMDIChildWnd::MDIRestore](../../mfc/reference/cmdichildwnd-class.md#mdirestore).

## <a name="cmdiframewndmdisetmenu"></a><a name="mdisetmenu"></a>CMDIFrameWnd::MDISetMenu

Zastępuje menu okna ramki MDI, menu podręcznego Okno lub oba te opcje.

```
CMenu* MDISetMenu(
    CMenu* pFrameMenu,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>Parametry

*pFrameMenu*<br/>
Określa menu nowego menu okna ramki. Jeśli null, menu nie zostanie zmienione.

*pWindowMenu*<br/>
Określa menu nowego menu podręcznego Okno. Jeśli null, menu nie zostanie zmienione.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do menu okna ramki zastąpiony tym komunikatem. Wskaźnik może być tymczasowy i nie powinny być przechowywane do późniejszego użycia.

### <a name="remarks"></a>Uwagi

Po `MDISetMenu`wywołaniu aplikacja musi wywołać funkcję członkowistą [DrawMenuBar,](../../mfc/reference/cwnd-class.md#drawmenubar) `CWnd` aby zaktualizować pasek menu.

Jeśli to wywołanie zastąpi menu podręczne Okno, elementy menu okna podrzędnego MDI zostaną usunięte z poprzedniego menu Okno i dodane do nowego menu podręcznego Okno.

Jeśli okno podrzędne MDI jest zmaksymalizowane, a to wywołanie zastępuje menu okna ramki MDI, menu Control i kontrolki przywracania zostaną usunięte z poprzedniego menu okna ramki i dodane do nowego menu.

Nie należy wywoływać tej funkcji elementu członkowskiego, jeśli używasz struktury do zarządzania oknami podrzędnymi MDI.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#19](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]

[!code-cpp[NVC_MFCWindowing#20](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]

## <a name="cmdiframewndmditile"></a><a name="mditile"></a>CMDIFrameWnd::MDITile

Rozmieszcza wszystkie okna podrzędne w formacie kafelkowym.

```cpp
void MDITile();
void MDITile(int nType);
```

### <a name="parameters"></a>Parametry

*nTyp*<br/>
Określa flagę kafli. Ten parametr może być dowolną z następujących flag:

- MDITILE_HORIZONTAL kafelki okien podrzędnych MDI, tak aby jedno okno pojawia się nad drugim.

- MDITILE_SKIPDISABLED Zapobiega sąsiadującu z wyłączonymi oknami podrzędnymi MDI.

- MDITILE_VERTICAL kafelki okien podrzędnych MDI, tak aby obok drugiego było wyświetlane jedno okno.

### <a name="remarks"></a>Uwagi

Pierwsza wersja `MDITile`, bez parametrów, kafelki okien pionowo w wersji systemu Windows 3.1 i nowszych. Druga wersja kafelki okna pionowo lub poziomo, w zależności od wartości parametru *nType.*

### <a name="example"></a>Przykład

Zobacz przykład [dla CMDIFrameWnd::MDICascade](#mdicascade).

## <a name="see-also"></a>Zobacz też

[Przykładowy MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Próbka MFC MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[Próbka MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Klasa CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)
