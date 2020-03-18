---
title: Klasa obiektu CFrameWnd
ms.date: 11/04/2016
f1_keywords:
- CFrameWnd
- AFXWIN/CFrameWnd
- AFXWIN/CFrameWnd::CFrameWnd
- AFXWIN/CFrameWnd::ActivateFrame
- AFXWIN/CFrameWnd::BeginModalState
- AFXWIN/CFrameWnd::Create
- AFXWIN/CFrameWnd::CreateView
- AFXWIN/CFrameWnd::DockControlBar
- AFXWIN/CFrameWnd::EnableDocking
- AFXWIN/CFrameWnd::EndModalState
- AFXWIN/CFrameWnd::FloatControlBar
- AFXWIN/CFrameWnd::GetActiveDocument
- AFXWIN/CFrameWnd::GetActiveFrame
- AFXWIN/CFrameWnd::GetActiveView
- AFXWIN/CFrameWnd::GetControlBar
- AFXWIN/CFrameWnd::GetDockState
- AFXWIN/CFrameWnd::GetMenuBarState
- AFXWIN/CFrameWnd::GetMenuBarVisibility
- AFXWIN/CFrameWnd::GetMessageBar
- AFXWIN/CFrameWnd::GetMessageString
- AFXWIN/CFrameWnd::GetTitle
- AFXWIN/CFrameWnd::InitialUpdateFrame
- AFXWIN/CFrameWnd::InModalState
- AFXWIN/CFrameWnd::IsTracking
- AFXWIN/CFrameWnd::LoadAccelTable
- AFXWIN/CFrameWnd::LoadBarState
- AFXWIN/CFrameWnd::LoadFrame
- AFXWIN/CFrameWnd::NegotiateBorderSpace
- AFXWIN/CFrameWnd::OnBarCheck
- AFXWIN/CFrameWnd::OnContextHelp
- AFXWIN/CFrameWnd::OnSetPreviewMode
- AFXWIN/CFrameWnd::OnUpdateControlBarMenu
- AFXWIN/CFrameWnd::RecalcLayout
- AFXWIN/CFrameWnd::SaveBarState
- AFXWIN/CFrameWnd::SetActivePreviewView
- AFXWIN/CFrameWnd::SetActiveView
- AFXWIN/CFrameWnd::SetDockState
- AFXWIN/CFrameWnd::SetMenuBarState
- AFXWIN/CFrameWnd::SetMenuBarVisibility
- AFXWIN/CFrameWnd::SetMessageText
- AFXWIN/CFrameWnd::SetProgressBarPosition
- AFXWIN/CFrameWnd::SetProgressBarRange
- AFXWIN/CFrameWnd::SetProgressBarState
- AFXWIN/CFrameWnd::SetTaskbarOverlayIcon
- AFXWIN/CFrameWnd::SetTitle
- AFXWIN/CFrameWnd::ShowControlBar
- AFXWIN/CFrameWnd::ShowOwnedWindows
- AFXWIN/CFrameWnd::OnCreateClient
- AFXWIN/CFrameWnd::OnHideMenuBar
- AFXWIN/CFrameWnd::OnShowMenuBar
- AFXWIN/CFrameWnd::m_bAutoMenuEnable
- AFXWIN/CFrameWnd::rectDefault
helpviewer_keywords:
- CFrameWnd [MFC], CFrameWnd
- CFrameWnd [MFC], ActivateFrame
- CFrameWnd [MFC], BeginModalState
- CFrameWnd [MFC], Create
- CFrameWnd [MFC], CreateView
- CFrameWnd [MFC], DockControlBar
- CFrameWnd [MFC], EnableDocking
- CFrameWnd [MFC], EndModalState
- CFrameWnd [MFC], FloatControlBar
- CFrameWnd [MFC], GetActiveDocument
- CFrameWnd [MFC], GetActiveFrame
- CFrameWnd [MFC], GetActiveView
- CFrameWnd [MFC], GetControlBar
- CFrameWnd [MFC], GetDockState
- CFrameWnd [MFC], GetMenuBarState
- CFrameWnd [MFC], GetMenuBarVisibility
- CFrameWnd [MFC], GetMessageBar
- CFrameWnd [MFC], GetMessageString
- CFrameWnd [MFC], GetTitle
- CFrameWnd [MFC], InitialUpdateFrame
- CFrameWnd [MFC], InModalState
- CFrameWnd [MFC], IsTracking
- CFrameWnd [MFC], LoadAccelTable
- CFrameWnd [MFC], LoadBarState
- CFrameWnd [MFC], LoadFrame
- CFrameWnd [MFC], NegotiateBorderSpace
- CFrameWnd [MFC], OnBarCheck
- CFrameWnd [MFC], OnContextHelp
- CFrameWnd [MFC], OnSetPreviewMode
- CFrameWnd [MFC], OnUpdateControlBarMenu
- CFrameWnd [MFC], RecalcLayout
- CFrameWnd [MFC], SaveBarState
- CFrameWnd [MFC], SetActivePreviewView
- CFrameWnd [MFC], SetActiveView
- CFrameWnd [MFC], SetDockState
- CFrameWnd [MFC], SetMenuBarState
- CFrameWnd [MFC], SetMenuBarVisibility
- CFrameWnd [MFC], SetMessageText
- CFrameWnd [MFC], SetProgressBarPosition
- CFrameWnd [MFC], SetProgressBarRange
- CFrameWnd [MFC], SetProgressBarState
- CFrameWnd [MFC], SetTaskbarOverlayIcon
- CFrameWnd [MFC], SetTitle
- CFrameWnd [MFC], ShowControlBar
- CFrameWnd [MFC], ShowOwnedWindows
- CFrameWnd [MFC], OnCreateClient
- CFrameWnd [MFC], OnHideMenuBar
- CFrameWnd [MFC], OnShowMenuBar
- CFrameWnd [MFC], m_bAutoMenuEnable
- CFrameWnd [MFC], rectDefault
ms.assetid: e2220aba-5bf4-4002-b960-fbcafcad01f1
ms.openlocfilehash: d2e043c8c9f4ad86636cd0e9ea7d695826b6c8fb
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418630"
---
# <a name="cframewnd-class"></a>Klasa obiektu CFrameWnd

Oferuje funkcje interfejsu pojedynczego dokumentu (SDI) systemu Windows lub okna podręcznego, a także członków do zarządzania oknem.

## <a name="syntax"></a>Składnia

```
class CFrameWnd : public CWnd
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Obiektu CFrameWnd:: obiektu CFrameWnd](#cframewnd)|Konstruuje obiekt `CFrameWnd`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Obiektu CFrameWnd:: ActivateFrame](#activateframe)|Sprawia, że ramka jest widoczna i dostępna dla użytkownika.|
|[Obiektu CFrameWnd:: BeginModalState](#beginmodalstate)|Ustawia okno ramki na modalne.|
|[Obiektu CFrameWnd:: Create](#create)|Wywołaj, aby utworzyć i zainicjować okno ramki systemu Windows skojarzone z obiektem `CFrameWnd`.|
|[Obiektu CFrameWnd:: isView](#createview)|Tworzy widok w ramce, która nie pochodzi od `CView`.|
|[Obiektu CFrameWnd::D ockControlBar](#dockcontrolbar)|Dockuje pasek sterowania.|
|[Obiektu CFrameWnd:: EnableDocking](#enabledocking)|Umożliwia zadokowanie paska sterowania.|
|[Obiektu CFrameWnd:: EndModalState](#endmodalstate)|Zamyka stan modalny okna ramki. Włącza wszystkie okna wyłączone przez `BeginModalState`.|
|[Obiektu CFrameWnd:: FloatControlBar](#floatcontrolbar)|Przesuwa pasek sterowania.|
|[Obiektu CFrameWnd:: GetActiveDocument](#getactivedocument)|Zwraca aktywny obiekt `CDocument`.|
|[Obiektu CFrameWnd:: GetActiveFrame —](#getactiveframe)|Zwraca aktywny obiekt `CFrameWnd`.|
|[Obiektu CFrameWnd:: GetActiveView](#getactiveview)|Zwraca aktywny obiekt `CView`.|
|[Obiektu CFrameWnd:: GetControlBar](#getcontrolbar)|Pobiera pasek sterowania.|
|[Obiektu CFrameWnd:: GetDockState](#getdockstate)|Pobiera stan dokowania okna ramki.|
|[Obiektu CFrameWnd:: GetMenuBarState](#getmenubarstate)|Pobiera stan wyświetlania menu w bieżącej aplikacji MFC.|
|[Obiektu CFrameWnd:: GetMenuBarVisibility](#getmenubarvisibility)|Wskazuje, czy domyślne zachowanie menu w bieżącej aplikacji MFC jest ukryte lub widoczne.|
|[Obiektu CFrameWnd:: GetMessageBar](#getmessagebar)|Zwraca wskaźnik do paska stanu należącego do okna ramki.|
|[Obiektu CFrameWnd:: GetMessageString](#getmessagestring)|Pobiera komunikat odpowiadający IDENTYFIKATORowi polecenia.|
|[Obiektu CFrameWnd:: getTitle](#gettitle)|Pobiera tytuł powiązanego paska sterowania.|
|[Obiektu CFrameWnd:: InitialUpdateFrame](#initialupdateframe)|Powoduje wywołanie funkcji składowej `OnInitialUpdate` należącej do wszystkich widoków w oknie klatki.|
|[Obiektu CFrameWnd:: InModalState](#inmodalstate)|Zwraca wartość wskazującą, czy okno ramki jest w stanie modalnym.|
|[Obiektu CFrameWnd:: istracking](#istracking)|Określa, czy pasek rozdzielacza jest aktualnie przenoszony.|
|[Obiektu CFrameWnd:: LoadAccelTable](#loadacceltable)|Wywołanie ładowania tabeli akceleratora.|
|[Obiektu CFrameWnd:: LoadBarState](#loadbarstate)|Wywołanie przywracania ustawień paska sterowania.|
|[Obiektu CFrameWnd:: LoadFrame](#loadframe)|Wywołanie dynamicznego tworzenia okna ramki na podstawie informacji o zasobach.|
|[Obiektu CFrameWnd:: NegotiateBorderSpace](#negotiateborderspace)|Negocjuje miejsce obramowania w oknie klatki.|
|[Obiektu CFrameWnd:: OnBarCheck](#onbarcheck)|Wywoływana za każdym razem, gdy akcja jest wykonywana na określonym pasku sterowania.|
|[Obiektu CFrameWnd:: OnContextHelp](#oncontexthelp)|Obsługuje SHIFT + F1 — Pomoc dla elementów w miejscu.|
|[Obiektu CFrameWnd:: OnSetPreviewMode](#onsetpreviewmode)|Ustawia okno główne ramki aplikacji na i z trybu podglądu wydruku.|
|[Obiektu CFrameWnd:: OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|Wywoływane przez platformę, gdy skojarzone menu zostanie zaktualizowane.|
|[Obiektu CFrameWnd:: RecalcLayout](#recalclayout)|Zmienia położenie pasków sterowania obiektu `CFrameWnd`.|
|[Obiektu CFrameWnd:: SaveBarState](#savebarstate)|Wywołanie zapisywania ustawień paska sterowania.|
|[Obiektu CFrameWnd:: SetActivePreviewView](#setactivepreviewview)|Określa, że określony widok ma być aktywnym widokiem dla zaawansowanej wersji zapoznawczej.|
|[Obiektu CFrameWnd:: SetActiveView](#setactiveview)|Ustawia obiekt Active `CView`.|
|[Obiektu CFrameWnd:: SetDockState](#setdockstate)|Wywołaj, aby zadokować okno ramki w oknie głównym.|
|[Obiektu CFrameWnd:: SetMenuBarState](#setmenubarstate)|Ustawia stan wyświetlania menu w bieżącej aplikacji MFC na wartość Hidden lub Display.|
|[Obiektu CFrameWnd:: SetMenuBarVisibility](#setmenubarvisibility)|Ustawia domyślne zachowanie menu w bieżącej aplikacji MFC jako ukryte lub widoczne.|
|[Obiektu CFrameWnd:: SetMessageText](#setmessagetext)|Ustawia tekst standardowego paska stanu.|
|[Obiektu CFrameWnd:: SetProgressBarPosition](#setprogressbarposition)|Ustawia bieżące położenie paska postępu systemu Windows 7 wyświetlanego na pasku zadań.|
|[Obiektu CFrameWnd:: SetProgressBarRange](#setprogressbarrange)|Ustawia zakres dla paska postępu systemu Windows 7 wyświetlanego na pasku zadań.|
|[Obiektu CFrameWnd:: SetProgressBarState](#setprogressbarstate)|Ustawia typ i stan wskaźnika postępu wyświetlanego na przycisku paska zadań.|
|[Obiektu CFrameWnd:: SetTaskbarOverlayIcon](#settaskbaroverlayicon)|Przeciążone. Stosuje nakładkę do przycisku paska zadań, aby wskazać stan aplikacji lub powiadomienie użytkownika.|
|[Obiektu CFrameWnd:: settitle](#settitle)|Ustawia tytuł pokrewnego paska sterowania.|
|[Obiektu CFrameWnd:: ShowControlBar](#showcontrolbar)|Wywołaj, aby wyświetlić pasek sterowania.|
|[Obiektu CFrameWnd:: ShowOwnedWindows](#showownedwindows)|Pokazuje wszystkie okna, które są elementami podrzędnymi obiektu `CFrameWnd`.|

### <a name="protected-methods"></a>Metody chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Obiektu CFrameWnd:: OnCreateClient](#oncreateclient)|Tworzy okno klienta dla ramki.|
|[Obiektu CFrameWnd:: OnHideMenuBar](#onhidemenubar)|Wywoływana przed ukryciem menu w bieżącej aplikacji MFC.|
|[Obiektu CFrameWnd:: OnShowMenuBar](#onshowmenubar)|Wywoływana przed wyświetleniem menu w bieżącej aplikacji MFC.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Obiektu CFrameWnd:: m_bAutoMenuEnable](#m_bautomenuenable)|Kontroluje automatyczne włączanie i wyłączanie funkcji dla elementów menu.|
|[Obiektu CFrameWnd:: rectDefault](#rectdefault)|Przekaż ten `CRect` statyczny jako parametr podczas tworzenia obiektu `CFrameWnd`, aby umożliwić systemowi Windows wybranie początkowego rozmiaru i położenia okna.|

## <a name="remarks"></a>Uwagi

Aby utworzyć użyteczne okno ramowe dla aplikacji, Utwórz klasę z `CFrameWnd`. Dodaj Zmienne Członkowskie do klasy pochodnej, aby przechowywać dane specyficzne dla aplikacji. Implementuj funkcje składowe programu obsługi komunikatów i mapę komunikatów w klasie pochodnej, aby określić, co się dzieje w przypadku kierowania komunikatów do okna.

Istnieją trzy sposoby konstruowania okna ramowego:

- Bezpośrednie konstruowanie za pomocą polecenia [Create](#create).

- Bezpośrednie konstruowanie przy użyciu [LoadFrame](#loadframe).

- Pośrednie konstruowanie przy użyciu szablonu dokumentu.

Przed wywołaniem `Create` lub `LoadFrame`, należy skonstruować obiekt okna ramki na stercie przy użyciu C++ operatora **New** . Przed wywołaniem `Create`można również zarejestrować klasę okna przy użyciu funkcji globalnej [AfxRegisterWndClass —](../../mfc/reference/application-information-and-management.md#afxregisterwndclass) , aby ustawić style ikon i klas dla ramki.

Użyj funkcji składowej `Create`, aby przekazać parametry tworzenia ramki jako natychmiastowe argumenty.

`LoadFrame` wymaga mniej argumentów niż `Create`, a zamiast tego pobiera większość wartości domyślnych z zasobów, w tym podpis ramki, ikonę, tabelę akceleratorów i menu. Aby można było uzyskać dostęp do `LoadFrame`, wszystkie te zasoby muszą mieć ten sam identyfikator zasobu (na przykład IDR_MAINFRAME).

Gdy obiekt `CFrameWnd` zawiera widoki i dokumenty, są one tworzone pośrednio przez platformę, a nie bezpośrednio przez programistę. Obiekt `CDocTemplate` organizuje Tworzenie ramki, Tworzenie widoków zawierających i łączenie widoków z odpowiednim dokumentem. Parametry konstruktora `CDocTemplate` określają `CRuntimeClass` trzech należących do siebie klas (dokumentu, ramki i widoku). Obiekt `CRuntimeClass` jest używany przez platformę do dynamicznego tworzenia nowych ramek, gdy jest określony przez użytkownika (na przykład przy użyciu polecenia New lub New File Interface (MDI) okna.

Klasa okien ramowych pochodna `CFrameWnd` musi być zadeklarowana z DECLARE_DYNCREATE, aby powyższy mechanizm RUNTIME_CLASS działał poprawnie.

`CFrameWnd` zawiera implementacje domyślne do wykonywania następujących funkcji okna głównego w typowej aplikacji dla systemu Windows:

- Okno ramki `CFrameWnd` śledzi aktualnie aktywny widok, który jest niezależny od aktywnego okna systemu Windows lub bieżącego fokusu wprowadzania. Po ponownym uaktywnieniu ramki aktywny widok zostanie powiadomiony przez wywołanie `CView::OnActivateView`.

- Komunikaty poleceń i wiele typowych komunikatów z powiadomieniem o ramce, w tym te obsługiwane przez `OnSetFocus`, `OnHScroll`i `OnVScroll` funkcje `CWnd`są delegowane przez okno ramki `CFrameWnd` do aktualnie aktywnego widoku.

- Aktualnie aktywny widok (lub aktualnie aktywne okno ramki podrzędnej MDI w przypadku ramki MDI) może określić podpis okna ramki. Tę funkcję można wyłączyć, wyłączając FWS_ADDTOTITLE styl stylu okna ramki.

- Okno ramki `CFrameWnd` zarządza pozycjonowaniem pasków sterowania, widoków i innych okien podrzędnych w obszarze klienta okna ramki. Okno ramowe wykonuje także aktualizację paska narzędzi i innych przycisków paska sterowania w czasie bezczynności. Okno ramki `CFrameWnd` ma także domyślne implementacje poleceń służących do przełączania się i wyłączania paska narzędzi i paska stanu.

- Okno ramki `CFrameWnd` zarządza głównym paskiem menu. Po wyświetleniu menu podręcznego okno ramki używa mechanizmu UPDATE_COMMAND_UI, aby określić, które elementy menu mają być włączone, wyłączone lub zaznaczone. Gdy użytkownik wybierze element menu, okno ramki aktualizuje pasek stanu za pomocą ciągu komunikatu dla tego polecenia.

- Okno ramki `CFrameWnd` ma opcjonalną tabelę akceleratorów, która automatycznie tłumaczy akceleratory klawiaturowe.

- Okno ramki `CFrameWnd` ma opcjonalny identyfikator pomocy ustawiony z `LoadFrame`, który jest używany na potrzeby pomocy kontekstowej. Okno ramek to główny koordynator półmodalne Stanów, takich jak pomoc kontekstowa (SHIFT + F1) i tryby drukowania w wersji zapoznawczej.

- W oknie ramka `CFrameWnd` zostanie otwarty plik przeciągnięty z Menedżera plików i usunięty z okna ramki. Jeśli rozszerzenie pliku zostanie zarejestrowane i skojarzone z aplikacją, okno ramki reaguje na otwarte żądanie dynamicznej wymiany danych (DDE), które występuje, gdy użytkownik otworzy plik danych w Menedżerze plików lub po wywołaniu funkcji `ShellExecute` systemu Windows.

- Jeśli okno ramki jest głównym oknem aplikacji (czyli `CWinThread::m_pMainWnd`), gdy użytkownik zamknie aplikację, w oknie ramka zostanie wyświetlony komunikat z prośbą o zapisanie zmodyfikowanych dokumentów (dla `OnClose` i `OnQueryEndSession`).

- Jeśli okno ramki jest głównym oknem aplikacji, okno ramki jest kontekstem do uruchamiania programu WinHelp. Zamknięcie okna ramki spowoduje zamknięcie systemu WINHELP. EXE, jeśli został uruchomiony w celu uzyskania pomocy dla tej aplikacji.

Nie używaj C++ operatora **delete** do niszczenia okna ramki. Zamiast tego użyj polecenia cmdlet `CWnd::DestroyWindow`. `CFrameWnd` implementacja `PostNcDestroy` spowoduje usunięcie C++ obiektu, gdy okno zostanie zniszczone. Gdy użytkownik zamknie okno ramki, domyślna procedura obsługi `OnClose` wywoła `DestroyWindow`.

Aby uzyskać więcej informacji na temat `CFrameWnd`, zobacz [okna ramek](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CFrameWnd`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

##  <a name="activateframe"></a>Obiektu CFrameWnd:: ActivateFrame

Wywołaj tę funkcję elementu członkowskiego, aby uaktywnić i przywrócić okno ramki, aby było ono widoczne i dostępne dla użytkownika.

```
virtual void ActivateFrame(int nCmdShow = -1);
```

### <a name="parameters"></a>Parametry

*nCmdShow*<br/>
Określa parametr do przekazania do [CWnd:: funkcja ShowWindow](../../mfc/reference/cwnd-class.md#showwindow). Domyślnie ramka jest wyświetlana i prawidłowo przywracana.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest zwykle wywoływana po zdarzeniu interfejsu użytkownika, takim jak DDE, OLE lub inne zdarzenie, które może wyświetlić okno ramki lub jego zawartość dla użytkownika.

Domyślna implementacja aktywuje ramkę i przenosi ją na górę z kolejnością Z i, w razie potrzeby, wykonuje te same kroki dla głównego okna ramki aplikacji.

Przesłoń tę funkcję elementu członkowskiego, aby zmienić sposób uaktywniania ramki. Można na przykład wymusić zmaksymalizowanie okien podrzędnych MDI. Dodaj odpowiednie funkcje, a następnie Wywołaj wersję klasy bazowej z jawnym *nCmdShow*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#1](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]

##  <a name="beginmodalstate"></a>Obiektu CFrameWnd:: BeginModalState

Wywołaj tę funkcję elementu członkowskiego, aby uczynić ramką modalną okna.

```
virtual void BeginModalState();
```

##  <a name="cframewnd"></a>Obiektu CFrameWnd:: obiektu CFrameWnd

Konstruuje obiekt `CFrameWnd`, ale nie tworzy okna widocznej ramki.

```
CFrameWnd();
```

### <a name="remarks"></a>Uwagi

Wywołaj `Create`, aby utworzyć widoczne okno.

##  <a name="create"></a>Obiektu CFrameWnd:: Create

Wywołaj, aby utworzyć i zainicjować okno ramki systemu Windows skojarzone z obiektem `CFrameWnd`.

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    LPCTSTR lpszWindowName,
    DWORD dwStyle = WS_OVERLAPPEDWINDOW,
    const RECT& rect = rectDefault,
    CWnd* pParentWnd = NULL,
    LPCTSTR lpszMenuName = NULL,
    DWORD dwExStyle = 0,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parametry

*lpszClassName*<br/>
Wskazuje ciąg znaków zakończony znakiem null, który nazywa klasę systemu Windows. Nazwa klasy może być dowolną nazwą zarejestrowanej za pomocą funkcji globalnej `AfxRegisterWndClass` lub funkcji `RegisterClass` systemu Windows. Jeśli wartość jest równa NULL, program używa wstępnie zdefiniowanych atrybutów `CFrameWnd` domyślnych.

*lpszWindowName*<br/>
Wskazuje ciąg znaków zakończony znakiem null, który reprezentuje nazwę okna. Używany jako tekst paska tytułu.

*dwStyle*<br/>
Określa atrybuty [stylu](../../mfc/reference/styles-used-by-mfc.md#window-styles) okna. Dołącz styl FWS_ADDTOTITLE, jeśli chcesz, aby pasek tytułu automatycznie wyświetlał nazwę dokumentu reprezentowanego w oknie.

*cinania*<br/>
Określa rozmiar i położenie okna. Wartość *rectDefault* umożliwia systemowi Windows określenie rozmiaru i pozycji nowego okna.

*pParentWnd*<br/>
Określa okno nadrzędne tego okna ramki. Ten parametr powinien mieć wartość NULL w przypadku okien ramowych najwyższego poziomu.

*lpszMenuName*<br/>
Określa nazwę zasobu menu, który ma być używany z oknem. Użyj MAKEINTRESOURCE, jeśli menu ma identyfikator w postaci liczby całkowitej zamiast ciągu. Ten parametr może mieć wartość NULL.

*dwExStyle*<br/>
Określa atrybuty rozszerzonego [stylu](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) okna.

*pContext*<br/>
Określa wskaźnik do struktury [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) . Ten parametr może mieć wartość NULL.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli Inicjalizacja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Utwórz obiekt `CFrameWnd` w dwóch krokach. Najpierw Wywołaj konstruktora, który konstruuje obiekt `CFrameWnd`, a następnie Wywołaj `Create`, który tworzy okno ramki systemu Windows i dołącza go do obiektu `CFrameWnd`. `Create` inicjuje nazwę klasy okna i nazwę okna i rejestruje wartości domyślne dla jego stylu, elementu nadrzędnego i menu skojarzone.

Użyj `LoadFrame`, a nie `Create` do załadowania okna ramki z zasobu, zamiast określania jego argumentów.

##  <a name="createview"></a>Obiektu CFrameWnd:: isView

Wywołaj `CreateView`, aby utworzyć widok w ramce.

```
CWnd* CreateView(
    CCreateContext* pContext,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Określa typ widoku i dokumentu.

*nID*<br/>
Numer IDENTYFIKACYJNy widoku.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu `CWnd`, jeśli się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Użyj tej funkcji elementu członkowskiego, aby utworzyć "widoki", które nie są `CView`w obrębie ramki. Po wywołaniu `CreateView`należy ręcznie ustawić widok jako aktywny i ustawić go jako widoczny; te zadania nie są automatycznie wykonywane przez `CreateView`.

##  <a name="dockcontrolbar"></a>Obiektu CFrameWnd::D ockControlBar

Powoduje zadokowanie paska sterowania do okna ramki.

```
void DockControlBar(
    CControlBar* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
Wskazuje pasek sterowania, który ma zostać zadokowany.

*nDockBarID*<br/>
Określa, które boki okna ramki należy wziąć pod uwagę w przypadku dokowania. Może to być 0 lub jeden lub więcej z następujących elementów:

- AFX_IDW_DOCKBAR_TOP Zadokuj w górnej części okna ramki.

- AFX_IDW_DOCKBAR_BOTTOM Zadokuj do dolnej krawędzi okna ramki.

- AFX_IDW_DOCKBAR_LEFT zadokowane po lewej stronie okna ramki.

- AFX_IDW_DOCKBAR_RIGHT Zadokuj po prawej stronie okna ramki.

W przypadku wartości 0 pasek sterowania może być zadokowany do dowolnej strony z włączoną funkcją dokowania w oknie Ramka docelowa.

*lpRect*<br/>
Określa współrzędne ekranu, w których pasek sterowania będzie zadokowany w nieklienckim obszarze okna ramki docelowej.

### <a name="remarks"></a>Uwagi

Pasek sterowania zostanie zadokowany do jednej z boków okna ramki określonego w wywołaniach do obu [CControlBar:: EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking) i [obiektu CFrameWnd:: EnableDocking](#enabledocking). Wybrana strona jest określana przez *nDockBarID*.

##  <a name="enabledocking"></a>Obiektu CFrameWnd:: EnableDocking

Wywołaj tę funkcję, aby włączyć paski kontrolne było dokować w oknie ramki.

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parametry

*dwDockStyle*<br/>
Określa, które boki okna ramki mogą być służące jako dokowania Lokacje dla pasków sterowania. Może to być jeden lub więcej z następujących elementów:

- CBRS_ALIGN_TOP umożliwia dokowanie w górnej części obszaru klienckiego.

- CBRS_ALIGN_BOTTOM umożliwia dokowanie w dolnej części obszaru klienckiego.

- CBRS_ALIGN_LEFT umożliwia dokowanie po lewej stronie obszaru klienckiego.

- CBRS_ALIGN_RIGHT umożliwia dokowanie po prawej stronie obszaru klienckiego.

- CBRS_ALIGN_ANY umożliwia dokowanie na każdej stronie obszaru klienckiego.

### <a name="remarks"></a>Uwagi

Domyślnie paski sterowania będą zadokowane po stronie okna ramki w następującej kolejności: Góra, dół, lewo, prawo.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CToolBar:: Create](../../mfc/reference/ctoolbar-class.md#create).

##  <a name="endmodalstate"></a>Obiektu CFrameWnd:: EndModalState

Wywołaj tę funkcję elementu członkowskiego, aby zmienić okno ramki z modalne na niemodalne.

```
virtual void EndModalState();
```

### <a name="remarks"></a>Uwagi

`EndModalState` włącza wszystkie okna wyłączone przez [BeginModalState](#beginmodalstate).

##  <a name="floatcontrolbar"></a>Obiektu CFrameWnd:: FloatControlBar

Wywołaj tę funkcję, aby uniemożliwić przedokowanie paska sterowania do okna ramki.

```
void FloatControlBar(
    CControlBar* pBar,
    CPoint point,
    DWORD dwStyle = CBRS_ALIGN_TOP);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
Wskazuje pasek sterowania do przesunięcia.

*moment*<br/>
Lokalizacja w obszarze Współrzędne ekranu, w której zostanie umieszczony lewy górny róg paska sterowania.

*dwStyle*<br/>
Określa, czy pasek kontroli ma być wyrównany w poziomie, czy w pionie w nowym oknie ramki. Może to być jeden z następujących:

- CBRS_ALIGN_TOP orientuje pasek sterowania w pionie.

- CBRS_ALIGN_BOTTOM orientuje pasek sterowania w pionie.

- CBRS_ALIGN_LEFT orientuje pasek sterowania w poziomie.

- CBRS_ALIGN_RIGHT orientuje pasek sterowania w poziomie.

Jeśli style są przenoszone, określając orientację poziomą i pionową, pasek narzędzi zostanie zorientowany w poziomie.

### <a name="remarks"></a>Uwagi

Zwykle odbywa się to podczas uruchamiania aplikacji, gdy program przywraca ustawienia z poprzedniego wykonania.

Ta funkcja jest wywoływana przez platformę, gdy użytkownik powoduje operację usuwania, zwalniając lewy przycisk myszy, przeciągając pasek sterowania na lokalizację, która nie jest dostępna do dokowania.

##  <a name="getactivedocument"></a>Obiektu CFrameWnd:: GetActiveDocument

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wskaźnik do bieżącego `CDocument` dołączonego do bieżącego aktywnego widoku.

```
virtual CDocument* GetActiveDocument();
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do bieżącego [CDocumentu](../../mfc/reference/cdocument-class.md). Jeśli nie ma bieżącego dokumentu, zwraca wartość NULL.

##  <a name="getactiveframe"></a>Obiektu CFrameWnd:: GetActiveFrame —

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wskaźnik do okna podrzędnego aktywnego interfejsu wielu dokumentów (MDI) okna ramki MDI.

```
virtual CFrameWnd* GetActiveFrame();
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do aktywnego okna podrzędnego MDI. Jeśli aplikacja jest aplikacją SDI lub okno ramki MDI nie ma aktywnego dokumentu, **ten** wskaźnik zostanie zwrócony.

### <a name="remarks"></a>Uwagi

Jeśli nie ma aktywnego elementu podrzędnego MDI lub aplikacja jest interfejsem pojedynczego dokumentu (SDI), zwracany jest **ten** wskaźnik.

##  <a name="getactiveview"></a>Obiektu CFrameWnd:: GetActiveView

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wskaźnik do aktywnego widoku (jeśli istnieje) dołączony do okna ramowego (`CFrameWnd`).

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do bieżącego [CViewu](../../mfc/reference/cview-class.md). Jeśli nie ma bieżącego widoku, zwraca wartość NULL.

### <a name="remarks"></a>Uwagi

Ta funkcja zwraca wartość NULL, gdy jest wywoływana dla głównego okna ramki MDI (`CMDIFrameWnd`). W aplikacji MDI w oknie głównym ramki MDI nie jest skojarzony widok. Zamiast tego każde pojedyncze okno podrzędne (`CMDIChildWnd`) zawiera co najmniej jeden skojarzony widok. Aktywny widok w aplikacji MDI można uzyskać przez znalezienie aktywnego okna podrzędnego MDI, a następnie znalezienie aktywnego widoku dla tego okna podrzędnego. Aktywne okno elementu podrzędnego MDI można znaleźć, wywołując funkcję `MDIGetActive` lub `GetActiveFrame`, jak pokazano w następujących elementach:

[!code-cpp[NVC_MFCWindowing#2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]

##  <a name="getcontrolbar"></a>Obiektu CFrameWnd:: GetControlBar

Wywołaj `GetControlBar`, aby uzyskać dostęp do paska sterowania skojarzonego z IDENTYFIKATORem.

```
CControlBar* GetControlBar(UINT nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Numer IDENTYFIKACYJNy paska sterowania.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do paska sterowania, który jest skojarzony z IDENTYFIKATORem.

### <a name="remarks"></a>Uwagi

Parametr *NID* odwołuje się do unikatowego identyfikatora przesłanego do metody `Create` na pasku sterowania. Aby uzyskać więcej informacji na temat pasków sterowania, zapoznaj się z tematem zatytułowanym [Paski kontroli](../../mfc/control-bars.md).

`GetControlBar` zwróci pasek sterowania nawet wtedy, gdy jest przepływany i w ten sposób nie jest obecnie oknem podrzędnym ramki.

##  <a name="getdockstate"></a>Obiektu CFrameWnd:: GetDockState

Wywołaj tę funkcję elementu członkowskiego, aby przechowywać informacje o stanie na pasku sterowania okna ramki w obiekcie `CDockState`.

```
void GetDockState(CDockState& state) const;
```

### <a name="parameters"></a>Parametry

*Państwu*<br/>
Zawiera bieżący stan pasków sterowania okna ramki po powrocie.

### <a name="remarks"></a>Uwagi

Następnie można napisać zawartość `CDockState` do magazynu przy użyciu `CDockState::SaveState` lub `Serialize`. Aby później przywrócić paski kontroli do poprzedniego stanu, Załaduj stan z `CDockState::LoadState` lub `Serialize`, a następnie Wywołaj `SetDockState`, aby zastosować poprzedni stan do pasków sterowania okna ramki.

##  <a name="getmenubarstate"></a>Obiektu CFrameWnd:: GetMenuBarState

Pobiera stan wyświetlania menu w bieżącej aplikacji MFC.

```
virtual DWORD GetMenuBarState();
```

### <a name="return-value"></a>Wartość zwrócona

Wartość zwracana może mieć następujące wartości:

- AFX_MBS_VISIBLE (0x01) — menu jest widoczne.

- AFX_MBS_HIDDEN (0x02) — menu jest ukryte.

### <a name="remarks"></a>Uwagi

Jeśli wystąpi błąd środowiska uruchomieniowego, ta metoda zostanie potwierdzona w trybie debugowania i wywołuje wyjątek pochodzący z klasy [CException](../../mfc/reference/cexception-class.md) .

##  <a name="getmenubarvisibility"></a>Obiektu CFrameWnd:: GetMenuBarVisibility

Wskazuje, czy domyślny stan menu w bieżącej aplikacji MFC jest ukryty czy widoczny.

```
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```

### <a name="return-value"></a>Wartość zwrócona

Ta metoda zwraca jedną z następujących wartości:

- AFX_MBV_KEEPVISIBLE (0x01) — menu jest wyświetlane przez cały czas i domyślnie nie ma fokusu.

- AFX_MBV_DISPLAYONFOCUS (0x02) — menu jest domyślnie ukryte. Jeśli menu jest ukryte, naciśnij klawisz ALT, aby wyświetlić menu i nadać fokus. Jeśli menu jest wyświetlane, naciśnij klawisz ALT lub ESC, aby je ukryć.

- AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04) (kombinacja bitowa (lub)) — menu jest domyślnie ukryte. Jeśli menu jest ukryte, naciśnij klawisz F10, aby wyświetlić menu i nadać mu fokus. Jeśli menu jest wyświetlane, naciśnij klawisz F10, aby przełączyć fokus na lub wyłączyć menu. Menu jest wyświetlane do momentu naciśnięcia klawisza ALT lub ESC, aby je ukryć.

### <a name="remarks"></a>Uwagi

Jeśli wystąpi błąd środowiska uruchomieniowego, ta metoda zostanie potwierdzona w trybie debugowania i wywołuje wyjątek pochodzący z klasy [CException](../../mfc/reference/cexception-class.md) .

##  <a name="getmessagebar"></a>Obiektu CFrameWnd:: GetMessageBar

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wskaźnik do paska stanu.

```
virtual CWnd* GetMessageBar();
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do okna pasek stanu.

##  <a name="getmessagestring"></a>Obiektu CFrameWnd:: GetMessageString

Zastąp tę funkcję, aby zapewnić niestandardowe ciągi dla identyfikatorów poleceń.

```
virtual void GetMessageString(
    UINT nID,
    CString& rMessage) const;
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identyfikator zasobu wymaganego komunikatu.

*rMessage*<br/>
`CString` obiekt, w którym ma zostać umieszczony komunikat.

### <a name="remarks"></a>Uwagi

Domyślna implementacja po prostu ładuje ciąg określony przez *NID* z pliku zasobów. Ta funkcja jest wywoływana przez platformę, gdy ciąg wiadomości w pasku stanu wymaga aktualizacji.

##  <a name="gettitle"></a>Obiektu CFrameWnd:: getTitle

Pobiera tytuł obiektu okna.

```
CString GetTitle() const;
```

### <a name="return-value"></a>Wartość zwrócona

Obiekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierający bieżący tytuł obiektu window.

##  <a name="initialupdateframe"></a>Obiektu CFrameWnd:: InitialUpdateFrame

Wywołaj `IntitialUpdateFrame` po utworzeniu nowej ramki z `Create`.

```
void InitialUpdateFrame(
    CDocument* pDoc,
    BOOL bMakeVisible);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Wskazuje dokument, do którego jest skojarzone okno ramki. Może mieć wartość NULL.

*bMakeVisible*<br/>
Jeśli wartość jest równa TRUE, wskazuje, że ramka powinna być widoczna i aktywna. W przypadku wartości FALSE żadne elementy podrzędne nie są widoczne.

### <a name="remarks"></a>Uwagi

Powoduje to, że wszystkie widoki w tym oknie ramki mogą odbierać `OnInitialUpdate` wywołania.

Ponadto, jeśli nie był wcześniej aktywny widok, podstawowy widok okna ramki zostanie uaktywniony. Widok podstawowy to widok z IDENTYFIKATORem podrzędnym AFX_IDW_PANE_FIRST. Na koniec okno ramki jest widoczne, jeśli *bMakeVisible* jest różna od zera. Jeśli *bMakeVisible* ma wartość 0, bieżący fokus i stan widoczny okna ramki pozostaną bez zmian. Nie jest konieczne Wywołaj tę funkcję w przypadku korzystania z implementacji pliku New i Open pliku przez platformę.

##  <a name="inmodalstate"></a>Obiektu CFrameWnd:: InModalState

Wywołaj tę funkcję elementu członkowskiego, aby sprawdzić, czy okno ramki jest modalne lub niemodalne.

```
BOOL InModalState() const;
```

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli tak; w przeciwnym razie 0.

##  <a name="istracking"></a>Obiektu CFrameWnd:: istracking

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy pasek rozdzielacza w oknie jest aktualnie przenoszony.

```
BOOL IsTracking() const;
```

### <a name="return-value"></a>Wartość zwrócona

Różne od zera, jeśli operacja rozdzielacza jest w toku; w przeciwnym razie 0.

##  <a name="loadacceltable"></a>Obiektu CFrameWnd:: LoadAccelTable

Wywołaj, aby załadować określoną tabelę akceleratora.

```
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Identyfikuje nazwę zasobu akceleratora. Użyj MAKEINTRESOURCE, jeśli zasób jest identyfikowany za pomocą identyfikatora Integer.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli tabela akceleratorów została pomyślnie załadowana; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

W danym momencie można ładować tylko jedną tabelę.

Tabele akceleratorów ładowane z zasobów są zwalniane automatycznie po zakończeniu działania aplikacji.

Jeśli wywołasz `LoadFrame` do utworzenia okna ramki, struktura ładuje tabelę akceleratora wraz z menu i zasobami ikon, a kolejne wywołanie tej funkcji składowej jest niepotrzebne.

##  <a name="loadbarstate"></a>Obiektu CFrameWnd:: LoadBarState

Wywołaj tę funkcję, aby przywrócić ustawienia każdego paska sterowania należącego do okna ramki.

```
void LoadBarState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
Nazwa sekcji w pliku inicjującym lub klucz w rejestrze systemu Windows, w którym są przechowywane informacje o stanie.

### <a name="remarks"></a>Uwagi

Przywrócone informacje obejmują widoczność, orientację poziomą/pionową, stan dokowania i położenie paska sterowania.

Ustawienia, które mają zostać przywrócone, muszą być zapisywane w rejestrze przed wywołaniem `LoadBarState`. Zapisz informacje w rejestrze, wywołując [CWinApp:: SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey). Zapisz informacje w pliku INI, wywołując [SaveBarState](#savebarstate).

##  <a name="loadframe"></a>Obiektu CFrameWnd:: LoadFrame

Wywołanie dynamicznego tworzenia okna ramki na podstawie informacji o zasobach.

```
virtual BOOL LoadFrame(
    UINT nIDResource,
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,
    CWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parametry

*nIDResource*<br/>
Identyfikator zasobów udostępnionych skojarzonych z oknem ramki.

*dwDefaultStyle*<br/>
[Styl](../../mfc/reference/styles-used-by-mfc.md#window-styles)ramki. Dołącz styl FWS_ADDTOTITLE, jeśli chcesz, aby pasek tytułu automatycznie wyświetlał nazwę dokumentu reprezentowanego w oknie.

*pParentWnd*<br/>
Wskaźnik do elementu nadrzędnego ramki.

*pContext*<br/>
Wskaźnik do struktury [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) . Ten parametr może mieć wartość NULL.

### <a name="remarks"></a>Uwagi

Utwórz obiekt `CFrameWnd` w dwóch krokach. Najpierw Wywołaj konstruktora, który konstruuje obiekt `CFrameWnd`, a następnie Wywołaj `LoadFrame`, co spowoduje załadowanie okna ramki systemu Windows i skojarzonych zasobów i dołączenie okna ramka do obiektu `CFrameWnd`. Parametr *nIDResource* określa menu, tabelę akceleratorów, ikonę i zasób ciągu tytułu okna ramki.

Użyj `Create` funkcji członkowskiej, a nie `LoadFrame`, gdy chcesz określić wszystkie parametry tworzenia okna ramki.

Struktura wywołuje `LoadFrame`, gdy tworzy okno ramki przy użyciu obiektu szablonu dokumentu.

Struktura używa argumentu *pContext* , aby określić obiekty, które mają być połączone z oknem ramki, w tym wszystkie zawarte w nim obiekty widoku. Argument *pContext* można ustawić na wartość null podczas wywoływania `LoadFrame`.

##  <a name="m_bautomenuenable"></a>Obiektu CFrameWnd:: m_bAutoMenuEnable

Gdy ten element członkowski danych jest włączony (co jest ustawieniem domyślnym), elementy menu, które nie mają programu obsługi ON_UPDATE_COMMAND_UI lub ON_COMMAND, zostaną automatycznie wyłączone, gdy użytkownik pobierze menu.

```
BOOL m_bAutoMenuEnable;
```

### <a name="remarks"></a>Uwagi

Elementy menu, które mają procedurę obsługi ON_COMMAND, ale żadna procedura obsługi ON_UPDATE_COMMAND_UI nie zostanie automatycznie włączona.

Gdy ten element członkowski danych jest ustawiony, elementy menu są włączane automatycznie w taki sam sposób, w jaki przyciski paska narzędzi są włączone.

> [!NOTE]
> `m_bAutoMenuEnable` nie ma wpływu na elementy menu najwyższego poziomu.

Ten element członkowski danych upraszcza implementację opcjonalnych poleceń opartych na bieżącym zaznaczeniu i zmniejsza konieczność pisania ON_UPDATE_COMMAND_UI obsługi w celu włączania i wyłączania elementów menu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]

##  <a name="negotiateborderspace"></a>Obiektu CFrameWnd:: NegotiateBorderSpace

Wywołaj tę funkcję elementu członkowskiego, aby wynegocjować miejsce w obramowaniu w oknie ramki podczas aktywacji w miejscu OLE.

```
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,
    LPRECT lpRectBorder);
```

### <a name="parameters"></a>Parametry

*nBorderCmd*<br/>
Zawiera jedną z następujących wartości z `enum BorderCmd`:

- `borderGet` = 1

- `borderRequest` = 2

- `borderSet` = 3

*lpRectBorder*<br/>
Wskaźnik do struktury [Rect](/windows/win32/api/windef/ns-windef-rect) lub obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , który określa współrzędne obramowania.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska to `CFrameWnd` implementacja negocjacji przestrzeni obramowania OLE.

##  <a name="onbarcheck"></a>Obiektu CFrameWnd:: OnBarCheck

Wywoływana za każdym razem, gdy akcja jest wykonywana na określonym pasku sterowania.

```
afx_msg BOOL OnBarCheck(UINT nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identyfikator wyświetlanego paska sterowania.

### <a name="return-value"></a>Wartość zwrócona

Różne od zera, jeśli pasek sterowania istniał. w przeciwnym razie 0.

##  <a name="oncontexthelp"></a>Obiektu CFrameWnd:: OnContextHelp

Obsługuje SHIFT + F1 — Pomoc dla elementów w miejscu.

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>Uwagi

Aby włączyć pomoc kontekstową, należy dodać

[!code-cpp[NVC_MFCDocViewSDI#16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]

Instrukcja do mapy komunikatów klasy `CFrameWnd` i dodawania wpisu akceleratora-tabeli, zazwyczaj SHIFT + F1, aby włączyć tę funkcję elementu członkowskiego.

Jeśli aplikacja jest kontenerem OLE, `OnContextHelp` umieszcza wszystkie elementy w miejscu zawarte w obiekcie okna ramki w trybie pomoc. Kursor zmieni się w strzałkę i znak zapytania, a użytkownik będzie mógł przenieść wskaźnik myszy i nacisnąć lewy przycisk myszy, aby zaznaczyć okno dialogowe, okno, menu lub przycisk polecenia. Ta funkcja członkowska wywołuje funkcję systemu Windows `WinHelp` z kontekstem pomocy dla obiektu pod kursorem.

##  <a name="oncreateclient"></a>Obiektu CFrameWnd:: OnCreateClient

Wywoływane przez platformę podczas wykonywania `OnCreate`.

```
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Parametry

*lpcs*<br/>
Wskaźnik do [struktury systemu Windows](/windows/win32/api/winuser/ns-winuser-createstructw) .

*pContext*<br/>
Wskaźnik do struktury [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) .

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Nigdy nie wywołuj tej funkcji.

Domyślna implementacja tej funkcji tworzy obiekt `CView` na podstawie informacji podanych w *pContext*, jeśli jest to możliwe.

Przesłoń tę funkcję, aby przesłonić wartości przesłane w obiekcie `CCreateContext` lub zmienić sposób tworzenia formantów w głównym obszarze klienta okna ramek. Elementy `CCreateContext`, które można przesłonić, są opisane w klasie [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) .

> [!NOTE]
>  Nie zamieniaj wartości przekazaną w strukturze `CREATESTRUCT`. Są one przeznaczone tylko do celów informacyjnych. Jeśli chcesz przesłonić początkowy prostokąt okna, na przykład Przesłoń `CWnd` funkcji składowej [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).

##  <a name="onhidemenubar"></a>Obiektu CFrameWnd:: OnHideMenuBar

Ta funkcja jest wywoływana, gdy system zamierza ukryć pasek menu w bieżącej aplikacji MFC.

```
virtual void OnHideMenuBar();
```

### <a name="remarks"></a>Uwagi

Ta procedura obsługi zdarzeń umożliwia aplikacji wykonywanie akcji niestandardowych, gdy system ukryje menu. Nie można zapobiec ukrywaniu menu, ale można na przykład wywoływać inne metody w celu pobrania stylu menu lub stanu.

##  <a name="onsetpreviewmode"></a>Obiektu CFrameWnd:: OnSetPreviewMode

Wywołaj tę funkcję elementu członkowskiego, aby ustawić okno głównej ramki aplikacji do i z trybu podglądu wydruku.

```
virtual void OnSetPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>Parametry

*bPreview*<br/>
Określa, czy aplikacja ma być umieszczona w trybie podglądu wydruku. Ustaw wartość TRUE, aby umieścić w podglądzie wydruku, FAŁSZ, aby anulować tryb podglądu.

*pState*<br/>
Wskaźnik do struktury `CPrintPreviewState`.

### <a name="remarks"></a>Uwagi

Domyślna implementacja powoduje wyłączenie wszystkich standardowych pasków narzędzi i ukrycie menu głównego i głównego okna klienta. Spowoduje to zamianę okien ramek MDI w tymczasowe okna szkieletu SDI.

Przesłoń tę funkcję elementu członkowskiego, aby dostosować ukrywanie i wyświetlanie pasków sterowania i innych części okna ramki podczas podglądu wydruku. Wywołaj implementację klasy bazowej z poziomu przesłoniętej wersji.

##  <a name="onshowmenubar"></a>Obiektu CFrameWnd:: OnShowMenuBar

Ta funkcja jest wywoływana, gdy system ma wyświetlić pasek menu w bieżącej aplikacji MFC.

```
virtual void OnShowMenuBar();
```

### <a name="remarks"></a>Uwagi

Ta procedura obsługi zdarzeń umożliwia aplikacji wykonywanie akcji niestandardowych, gdy menu ma zostać wyświetlone. Nie można uniemożliwić wyświetlania menu, ale można na przykład wywołać inne metody, aby pobrać styl menu lub stan.

##  <a name="onupdatecontrolbarmenu"></a>Obiektu CFrameWnd:: OnUpdateControlBarMenu

Wywoływane przez platformę, gdy skojarzone menu zostanie zaktualizowane.

```
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do obiektu [CCmdUI](../../mfc/reference/ccmdui-class.md) reprezentujący menu, które wygenerowało polecenie aktualizacji. Procedura obsługi aktualizacji wywołuje funkcję [włączania](../../mfc/reference/ccmdui-class.md#enable) elementu członkowskiego obiektu `CCmdUI` za pomocą *pCmdUI* , aby zaktualizować interfejs użytkownika.

##  <a name="recalclayout"></a>Obiektu CFrameWnd:: RecalcLayout

Wywoływane przez platformę, gdy standardowe paski kontrolki są włączane lub wyłączane lub gdy zmieniany jest rozmiar okna ramki.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parametry

*bNotify*<br/>
Określa, czy aktywny element w miejscu okna ramki otrzymuje powiadomienie o zmianie układu. Jeśli wartość jest równa TRUE, element zostanie powiadomiony; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji składowej wywołuje `CWnd` funkcji składowej `RepositionBars` do zmiany położenia wszystkich pasków sterowania w ramce, jak również w głównym oknie klienta (zazwyczaj jest to `CView` lub MDICLIENT).

Przesłoń tę funkcję elementu członkowskiego, aby kontrolować wygląd i zachowanie pasków sterowania po zmianie układu okna ramki. Na przykład Wywołaj je po włączeniu lub wyłączeniu pasków sterowania lub Dodaj inny pasek sterowania.

##  <a name="rectdefault"></a>Obiektu CFrameWnd:: rectDefault

Przekaż ten `CRect` statyczny jako parametr podczas tworzenia okna, aby zezwolić systemowi Windows na wybranie początkowego rozmiaru i położenia okna.

```
static AFX_DATA const CRect rectDefault;
```

##  <a name="savebarstate"></a>Obiektu CFrameWnd:: SaveBarState

Wywołaj tę funkcję, aby przechowywać informacje o każdym pasku sterowania należącym do okna ramki.

```
void SaveBarState(LPCTSTR lpszProfileName) const;
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
Nazwa sekcji w pliku inicjującym lub klucz w rejestrze systemu Windows, w którym są przechowywane informacje o stanie.

### <a name="remarks"></a>Uwagi

Te informacje można odczytać z pliku inicjującego za pomocą [LoadBarState](#loadbarstate). Informacje przechowywane obejmują widoczność, orientację poziomą/pionową, stan dokowania i położenie paska sterowania.

##  <a name="setactivepreviewview"></a>Obiektu CFrameWnd:: SetActivePreviewView

Określa, że określony widok ma być aktywnym widokiem dla zaawansowanej wersji zapoznawczej.

```
void SetActivePreviewView(CView* pViewNew);
```

### <a name="parameters"></a>Parametry

*pViewNew*<br/>
Wskaźnik do widoku, który ma zostać aktywowany.

### <a name="remarks"></a>Uwagi

##  <a name="setactiveview"></a>Obiektu CFrameWnd:: SetActiveView

Wywołaj tę funkcję elementu członkowskiego, aby ustawić aktywny widok.

```
void SetActiveView(
    CView* pViewNew,
    BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parametry

*pViewNew*<br/>
Określa wskaźnik do obiektu [CView](../../mfc/reference/cview-class.md) lub wartość null dla braku aktywnego widoku.

*bNotify*<br/>
Określa, czy widok ma być powiadamiany o aktywacji. W przypadku wartości TRUE `OnActivateView` jest wywoływana dla nowego widoku; Jeśli wartość jest równa FALSE, nie jest.

### <a name="remarks"></a>Uwagi

Platforma wywoła tę funkcję automatycznie, gdy użytkownik zmieni fokus w widoku w oknie ramki. Można jawnie wywołać `SetActiveView`, aby zmienić fokus do określonego widoku.

##  <a name="setdockstate"></a>Obiektu CFrameWnd:: SetDockState

Wywołaj tę funkcję elementu członkowskiego, aby zastosować informacje o stanie przechowywane w obiekcie `CDockState` do pasków sterowania okna ramki.

```
void SetDockState(const CDockState& state);
```

### <a name="parameters"></a>Parametry

*Państwu*<br/>
Zastosuj stan przechowywany do pasków sterowania okna ramki.

### <a name="remarks"></a>Uwagi

Aby przywrócić poprzedni stan pasków sterowania, można załadować zapisany stan z `CDockState::LoadState` lub `Serialize`, a następnie użyć `SetDockState`, aby zastosować go do pasków sterowania okna ramki. Poprzedni stan jest przechowywany w obiekcie `CDockState` z `GetDockState`

##  <a name="setmenubarstate"></a>Obiektu CFrameWnd:: SetMenuBarState

Ustawia stan wyświetlania menu w bieżącej aplikacji MFC na wartość Hidden lub Display.

```
virtual BOOL SetMenuBarState(DWORD nState);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*nInformacje*|podczas Określa, czy menu ma być wyświetlane, czy ukryte. Parametr *nInformacje* może mieć następujące wartości:<br /><br />-AFX_MBS_VISIBLE (0x01) — wyświetla menu, jeśli jest ukryte, ale nie działa, jeśli jest widoczne.<br />-AFX_MBS_HIDDEN (0x02) — ukrywa menu, jeśli jest widoczne, ale nie działa, jeśli jest ukryte.|

### <a name="return-value"></a>Wartość zwrócona

PRAWDA, jeśli ta metoda pomyślnie zmienia stan menu; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli wystąpi błąd środowiska uruchomieniowego, ta metoda zostanie potwierdzona w trybie debugowania i wywołuje wyjątek pochodzący z klasy [CException](../../mfc/reference/cexception-class.md) .

##  <a name="setmenubarvisibility"></a>Obiektu CFrameWnd:: SetMenuBarVisibility

Ustawia domyślne zachowanie menu w bieżącej aplikacji MFC jako ukryte lub widoczne.

```
virtual void SetMenuBarVisibility(DWORD nStyle);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*nStyle*|podczas Określa, czy menu jest domyślnie ukryte, czy jest widoczne i ma fokus. Parametr *nStyle* może mieć następujące wartości:<br /><br />-AFX_MBV_KEEPVISIBLE (0x01) —<br />     Menu jest wyświetlane przez cały czas i domyślnie nie ma fokusu.<br />-AFX_MBV_DISPLAYONFOCUS (0x02) —<br />     Menu jest domyślnie ukryte. Jeśli menu jest ukryte, naciśnij klawisz ALT, aby wyświetlić menu i nadać fokus. Jeśli menu jest wyświetlane, naciśnij klawisz ALT lub ESC, aby ukryć menu.<br />-AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04)<br />     (kombinacja bitowa (lub)) — menu jest domyślnie ukryte. Jeśli menu jest ukryte, naciśnij klawisz F10, aby wyświetlić menu i nadać mu fokus. Jeśli menu jest wyświetlane, naciśnij klawisz F10, aby przełączyć fokus na lub wyłączyć menu. Menu jest wyświetlane do momentu naciśnięcia klawisza ALT lub ESC, aby je ukryć.|

### <a name="remarks"></a>Uwagi

Jeśli wartość parametru *nStyle* jest nieprawidłowa, ta metoda potwierdza tryb debugowania i wywołuje [CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md) w trybie wydania. W przypadku innych błędów środowiska uruchomieniowego ta metoda potwierdza tryb debugowania i wywołuje wyjątek pochodzący z klasy [CException](../../mfc/reference/cexception-class.md) .

Ta metoda ma wpływ na stan menu w aplikacjach utworzonych dla systemu Windows Vista i nowszych.

##  <a name="setmessagetext"></a>Obiektu CFrameWnd:: SetMessageText

Wywołaj tę funkcję, aby umieścić ciąg w okienku Pasek stanu o IDENTYFIKATORze 0.

```
void SetMessageText(LPCTSTR lpszText);
void SetMessageText(UINT nID);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Wskazuje ciąg, który ma zostać umieszczony na pasku stanu.

*nID*<br/>
Identyfikator zasobu ciągu, który ma zostać umieszczony na pasku stanu.

### <a name="remarks"></a>Uwagi

Jest to zazwyczaj skrajne lewe i najdłuższe okienko paska stanu.

##  <a name="setprogressbarposition"></a>Obiektu CFrameWnd:: SetProgressBarPosition

Ustawia bieżącą pozycję paska postępu systemu Windows 7 wyświetlanego na pasku zadań.

```
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>Parametry

*nProgressPos*<br/>
Określa pozycję do ustawienia. Musi znajdować się w zakresie ustawionym przez `SetProgressBarRange`.

### <a name="remarks"></a>Uwagi

##  <a name="setprogressbarrange"></a>Obiektu CFrameWnd:: SetProgressBarRange

Ustawia zakres dla paska postępu systemu Windows 7 wyświetlanego na pasku zadań.

```
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>Parametry

*nRangeMin*<br/>
Minimalna wartość.

*nRangeMax*<br/>
Maksymalna wartość.

### <a name="remarks"></a>Uwagi

##  <a name="setprogressbarstate"></a>Obiektu CFrameWnd:: SetProgressBarState

Ustawia typ i stan wskaźnika postępu wyświetlanego na przycisku paska zadań.

```
void SetProgressBarState(TBPFLAG tbpFlags);
```

### <a name="parameters"></a>Parametry

*tbpFlags*<br/>
Flagi kontrolujące bieżący stan przycisku postępu. Określ tylko jedną z następujących flag, ponieważ wszystkie Stany wykluczają się wzajemnie: TBPF_NOPROGRESS, TBPF_INDETERMINATE, TBPF_NORMAL, TBPF_ERROR, TBPF_PAUSED.

### <a name="remarks"></a>Uwagi

##  <a name="settaskbaroverlayicon"></a>Obiektu CFrameWnd:: SetTaskbarOverlayIcon

Przeciążone. Stosuje nakładkę do przycisku paska zadań w celu wskazania stanu aplikacji lub powiadomienia użytkownika.

```
BOOL SetTaskbarOverlayIcon(
    UINT nIDResource,
    LPCTSTR lpcszDescr);

BOOL SetTaskbarOverlayIcon(
    HICON hIcon,
    LPCTSTR lpcszDescr);
```

### <a name="parameters"></a>Parametry

*nIDResource*<br/>
Określa identyfikator zasobu ikony, który ma być używany jako nakładka. Aby uzyskać szczegółowe informacje, zobacz opis elementu *HICON* .

*lpcszDescr*<br/>
Wskaźnik do ciągu, który zawiera tekst alternatywny dla informacji przekazywanych przez nakładkę w celu ułatwienia dostępu.

*hIcon*<br/>
Uchwyt ikony, która ma być używana jako nakładka. Powinna to być mała ikona, mierząca 16 96 pikseli na cal (dpi). Jeśli ikona nakładki została już zastosowana do przycisku paska zadań, istniejąca nakładka zostanie zastąpiona. Ta wartość może być RÓWNa NULL. Sposób obsługi wartości NULL zależy od tego, czy przycisk paska zadań reprezentuje pojedyncze okno, czy grupę okien. Aplikacja wywołująca jest odpowiedzialna za bezpłatną *HICON* , gdy nie jest już potrzebne.

### <a name="return-value"></a>Wartość zwrócona

Wartość TRUE, jeśli powodzenie; Wartość FALSE, jeśli wersja systemu operacyjnego jest starsza niż Windows 7 lub jeśli wystąpi błąd podczas ustawiania ikony.

### <a name="remarks"></a>Uwagi

##  <a name="settitle"></a>Obiektu CFrameWnd:: settitle

Ustawia tytuł obiektu okna.

```
void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>Parametry

*lpszTitle*<br/>
Wskaźnik do ciągu znaków zawierającego tytuł obiektu okna.

##  <a name="showcontrolbar"></a>Obiektu CFrameWnd:: ShowControlBar

Wywołaj tę funkcję elementu członkowskiego, aby pokazać lub ukryć pasek sterowania.

```
void ShowControlBar(
    CControlBar* pBar,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
Wskaźnik na pasek sterowania, który ma być wyświetlany lub ukryty.

*bShow*<br/>
Jeśli wartość jest równa TRUE, określa, że pasek sterowania ma być pokazywany. W przypadku wartości FALSE określa, że pasek sterowania ma być ukryty.

*bDelay*<br/>
Jeśli wartość jest równa TRUE, opóźnienie wyświetla pasek sterowania. W przypadku wartości FALSE Pokaż pasek sterowania natychmiast.

##  <a name="showownedwindows"></a>Obiektu CFrameWnd:: ShowOwnedWindows

Wywołaj tę funkcję elementu członkowskiego, aby pokazać wszystkie okna, które są elementami podrzędnymi obiektu `CFrameWnd`.

```
void ShowOwnedWindows(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
Określa, czy należące do systemu Windows mają być pokazywane czy ukryte.

## <a name="see-also"></a>Zobacz też

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Klasa CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)<br/>
[Klasa CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)<br/>
[Klasa CView](../../mfc/reference/cview-class.md)<br/>
[Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Struktura CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)
