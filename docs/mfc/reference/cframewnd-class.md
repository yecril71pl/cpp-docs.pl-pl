---
title: Klasa CFrameWnd
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
ms.openlocfilehash: 3bb93420b39be5d6fb9a6691cec8300fdccb0e73
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754978"
---
# <a name="cframewnd-class"></a>Klasa CFrameWnd

Udostępnia funkcje interfejsu pojedynczego dokumentu systemu Windows (SDI) nakładającego się lub okna wyskakujących ramek, wraz z członkami do zarządzania oknem.

## <a name="syntax"></a>Składnia

```
class CFrameWnd : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFrameWnd::CFrameWnd](#cframewnd)|Konstruuje `CFrameWnd` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFrameWnd::ActivateFrame](#activateframe)|Sprawia, że ramka jest widoczna i dostępna dla użytkownika.|
|[CFrameWnd::BeginModalState](#beginmodalstate)|Ustawia okno ramki na modalne.|
|[CFrameWnd::Utwórz](#create)|Wywołanie utworzenia i zainicjowania okna ramki systemu Windows skojarzonego z obiektem. `CFrameWnd`|
|[CFrameWnd::CreateView](#createview)|Tworzy widok w ramce, która `CView`nie jest pochodną .|
|[CFrameWnd::DockControlBar](#dockcontrolbar)|Dokuje pasek sterowania.|
|[CFrameWnd::EnableDocking](#enabledocking)|Umożliwia zadokowanie paska sterowania.|
|[CFrameWnd::EndModalState](#endmodalstate)|Kończy stan modalny okna ramki. Włącza wszystkie okna wyłączone `BeginModalState`przez program .|
|[CFrameWnd::FloatControlBar](#floatcontrolbar)|Unosi pasek sterowania.|
|[CFrameWnd::GetActiveDocument](#getactivedocument)|Zwraca aktywny `CDocument` obiekt.|
|[CFrameWnd::GetActiveFrame](#getactiveframe)|Zwraca aktywny `CFrameWnd` obiekt.|
|[CFrameWnd::GetActiveView](#getactiveview)|Zwraca aktywny `CView` obiekt.|
|[CFrameWnd::GetControlBar](#getcontrolbar)|Pobiera pasek sterowania.|
|[CFrameWnd::GetDockState](#getdockstate)|Pobiera stan dokującej okna ramki.|
|[CFrameWnd::GetMenuBarState](#getmenubarstate)|Pobiera stan wyświetlania menu w bieżącej aplikacji MFC.|
|[CFrameWnd::GetMenuBarWiętność](#getmenubarvisibility)|Wskazuje, czy domyślne zachowanie menu w bieżącej aplikacji MFC jest ukryte lub widoczne.|
|[CFrameWnd::Pasek GetMessage](#getmessagebar)|Zwraca wskaźnik do paska stanu należącego do okna ramki.|
|[CFrameWnd::GetMessageStrowanie](#getmessagestring)|Pobiera wiadomość odpowiadającą identyfikatorowi polecenia.|
|[CFrameWnd::GetTitle](#gettitle)|Pobiera tytuł powiązanego paska sterowania.|
|[CFrameWnd::InitialUpdateFrame](#initialupdateframe)|Powoduje, `OnInitialUpdate` że funkcja elementu członkowskiego należąca do wszystkich widoków w oknie ramki ma być wywoływana.|
|[CFrameWnd::Stan InModal](#inmodalstate)|Zwraca wartość wskazującą, czy okno ramki jest w stanie modalnym.|
|[CFrameWnd::IsTracking](#istracking)|Określa, czy pasek rozdzielacza jest obecnie przenoszony.|
|[CFrameWnd::LoadAccelTable](#loadacceltable)|Wywołanie, aby załadować tabelę akceleratora.|
|[CFrameWnd::LoadBarState](#loadbarstate)|Wywołanie, aby przywrócić ustawienia paska sterowania.|
|[CFrameWnd::LoadFrame](#loadframe)|Wywołanie dynamicznego tworzenia okna ramki na podstawie informacji o zasobach.|
|[CFrameWnd::NegotiateBorderSpace](#negotiateborderspace)|Negocjuje miejsce na granicy w oknie ramki.|
|[CFrameWnd::OnBarCheck](#onbarcheck)|Wywoływana za każdym razem, gdy akcja jest wykonywana na określonym pasku sterowania.|
|[CFrameWnd::OnContextHelp](#oncontexthelp)|Obsługuje Pomoc SHIFT+F1 dla elementów w miejscu.|
|[CFrameWnd::OnSetPreviewMode](#onsetpreviewmode)|Ustawia okno ramki głównej aplikacji w trybie podglądu wydruku i z nich.|
|[CFrameWnd::OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|Wywoływane przez strukturę, gdy skojarzone menu jest aktualizowana.|
|[CFrameWnd::RecalcLayout](#recalclayout)|Zmienia położenie prętów sterujących `CFrameWnd` obiektu.|
|[CFrameWnd::Stan przycisków SaveBar](#savebarstate)|Wywołanie, aby zapisać ustawienia paska sterowania.|
|[CFrameWnd::SetActivePreview](#setactivepreviewview)|Wyznacza określony widok jako aktywny widok dla zaawansowanego podglądu.|
|[CFrameWnd::SetActiveView](#setactiveview)|Ustawia obiekt `CView` aktywny.|
|[CFrameWnd::Stan SetDock](#setdockstate)|Wywołanie dokowania okna ramki w oknie głównym.|
|[CFrameWnd::SetMenuBarState](#setmenubarstate)|Ustawia stan wyświetlania menu w bieżącej aplikacji MFC na ukryte lub wyświetlane.|
|[CFrameWnd::SetMenuBarWiękność](#setmenubarvisibility)|Ustawia domyślne zachowanie menu w bieżącej aplikacji MFC, które ma być ukryte lub widoczne.|
|[CFrameWnd::SetMessageText](#setmessagetext)|Ustawia tekst standardowego paska stanu.|
|[CFrameWnd::SetProgressBarPosition](#setprogressbarposition)|Ustawia bieżącą pozycję paska postępu systemu Windows 7 wyświetlanego na pasku zadań.|
|[CFrameWnd::SetProgressBarRange](#setprogressbarrange)|Ustawia zakres paska postępu systemu Windows 7 wyświetlanego na pasku zadań.|
|[CFrameWnd::Stan zestawu](#setprogressbarstate)|Ustawia typ i stan wskaźnika postępu wyświetlanego na przycisku paska zadań.|
|[CFrameWnd::SetTaskbarOverlayIcon](#settaskbaroverlayicon)|Przeciążone. Stosuje nakładkę do przycisku paska zadań, aby wskazać stan aplikacji lub powiadomienie użytkownika.|
|[CFrameWnd::SetTitle](#settitle)|Ustawia tytuł powiązanego paska sterowania.|
|[CFrameWnd::ShowControlBar](#showcontrolbar)|Wywołanie, aby wyświetlić pasek sterowania.|
|[CFrameWnd::ShowOwnedWindows](#showownedwindows)|Pokazuje wszystkie okna, które `CFrameWnd` są elementami podrzędnymi obiektu.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CFrameWnd::OnCreateClient](#oncreateclient)|Tworzy okno klienta dla ramki.|
|[CFrameWnd::OnHideMenuBar](#onhidemenubar)|Wywoływane przed menu w bieżącej aplikacji MFC jest ukryty.|
|[CFrameWnd::OnShowMenuBar](#onshowmenubar)|Wywoływane przed menu w bieżącej aplikacji MFC jest wyświetlany.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CFrameWnd::m_bAutoMenuEnable](#m_bautomenuenable)|Steruje funkcją automatycznego włączania i wyłączania elementów menu.|
|[CFrameWnd::rectDefault](#rectdefault)|Przekaż ten `CRect` statyczny jako parametr `CFrameWnd` podczas tworzenia obiektu, aby umożliwić systemowi Windows wybranie początkowego rozmiaru i położenia okna.|

## <a name="remarks"></a>Uwagi

Aby utworzyć przydatne okno ramki dla aplikacji, `CFrameWnd`należy wyprowadzić klasę z pliku . Dodaj zmienne członkowskie do klasy pochodnej do przechowywania danych specyficznych dla aplikacji. Zaimplementuj funkcje członkowskie programu message-handler i mapę wiadomości w klasie pochodnej, aby określić, co się dzieje, gdy wiadomości są kierowane do okna.

Istnieją trzy sposoby konstruowania okna ramki:

- Bezpośrednio konstruuj go za pomocą [create](#create).

- Bezpośrednio konstruuj go za pomocą [LoadFrame](#loadframe).

- Pośrednio konstruować go przy użyciu szablonu dokumentu.

Przed wywołaniem `Create` albo `LoadFrame`lub , należy skonstruować obiekt okna ramki na stercie przy użyciu **C++ nowy** operator. Przed `Create`wywołaniem można również zarejestrować klasę okna za pomocą funkcji globalnej [AfxRegisterWndClass,](../../mfc/reference/application-information-and-management.md#afxregisterwndclass) aby ustawić ikonę i style klas dla ramki.

Funkcja `Create` elementu członkowskiego służy do przekazywania parametrów tworzenia ramki jako argumentów natychmiastowych.

`LoadFrame`wymaga mniejszej `Create`liczby argumentów niż program , a zamiast tego pobiera większość wartości domyślnych z zasobów, w tym podpis ramki, ikonę, tabelę akceleratora i menu. Aby dostęp `LoadFrame`do nich był dostępny, wszystkie te zasoby muszą mieć ten sam identyfikator zasobu (na przykład IDR_MAINFRAME).

Gdy `CFrameWnd` obiekt zawiera widoki i dokumenty, są one tworzone pośrednio przez strukturę, a nie bezpośrednio przez programistę. Obiekt `CDocTemplate` organizuje tworzenie ramki, tworzenie zawierających widoków i połączenie widoków z odpowiednim dokumentem. Parametry konstruktora `CDocTemplate` określają `CRuntimeClass` trzy zaangażowane klasy (dokument, ramka i widok). Obiekt `CRuntimeClass` jest używany przez strukturę do dynamicznego tworzenia nowych ramek po określeniu przez użytkownika (na przykład za pomocą polecenia Plik nowy lub polecenia Okno wielu dokumentów (MDI) Window New).

Klasa okna ramki pochodzące z `CFrameWnd` muszą być zadeklarowane z DECLARE_DYNCREATE, aby powyższy mechanizm RUNTIME_CLASS działać poprawnie.

A `CFrameWnd` zawiera domyślne implementacje do wykonywania następujących funkcji okna głównego w typowej aplikacji dla systemu Windows:

- Okno `CFrameWnd` ramki śledzi aktualnie aktywny widok niezależny od aktywnego okna systemu Windows lub bieżącego fokusu wejściowego. Po ponownym uaktywnieniu ramki aktywny `CView::OnActivateView`widok jest powiadamiany przez wywołanie .

- Komunikaty poleceń i wiele typowych komunikatów `OnSetFocus`o `OnHScroll`powiadomieniach o ramce, w tym wiadomości obsługiwane przez program , i `OnVScroll` funkcje `CWnd`, są delegowane przez okno `CFrameWnd` ramki do aktualnie aktywnego widoku.

- Aktualnie aktywny widok (lub aktualnie aktywne okno ramki podrzędnej MDI w przypadku ramki MDI) może określić podpis okna ramki. Tę funkcję można wyłączyć, wyłączając FWS_ADDTOTITLE styl okna ramki.

- Okno `CFrameWnd` ramki zarządza pozycjonowaniem pasków sterowania, widoków i innych okien podrzędnych wewnątrz obszaru klienckiego okna ramki. Okno ramki umożliwia również aktualizację paska narzędzi i innych przycisków paska sterowania w czasie bezczynności. Okno `CFrameWnd` ramki ma również domyślne implementacje poleceń do przełączania na i poza paskiem narzędzi i paskiem stanu.

- Okno `CFrameWnd` ramki zarządza paskiem menu głównego. Po wyświetleniu menu podręcznego okno ramki używa mechanizmu UPDATE_COMMAND_UI do określenia, które elementy menu powinny być włączone, wyłączone lub zaznaczone. Gdy użytkownik wybierze element menu, okno ramki aktualizuje pasek stanu z ciągiem komunikatu dla tego polecenia.

- Okno `CFrameWnd` ramki ma opcjonalną tabelę akceleratora, która automatycznie tłumaczy akceleratory klawiatury.

- Okno `CFrameWnd` ramki ma opcjonalny zestaw `LoadFrame` identyfikatorów pomocy, który jest używany do pomocy kontekstowej. Okno ramki jest głównym koordynatorem stanów półmodalnych, takich jak pomoc kontekstowa (SHIFT + F1) i tryby podglądu wydruku.

- Okno `CFrameWnd` ramki otworzy plik przeciągnięty z Menedżera plików i upuszczony w oknie ramki. Jeśli rozszerzenie pliku jest zarejestrowane i skojarzone z aplikacją, okno ramki odpowiada na żądanie otwartej dynamicznej wymiany danych (DDE), które występuje, gdy użytkownik otworzy plik danych w Menedżerze plików lub gdy wywoływana jest funkcja `ShellExecute` Systemu Windows.

- Jeśli okno ramki jest głównym oknem aplikacji (czyli `CWinThread::m_pMainWnd`), gdy użytkownik zamyka aplikację, okno ramki monituje użytkownika o zapisanie zmodyfikowanych dokumentów (for `OnClose` i `OnQueryEndSession`).

- Jeśli okno ramki jest głównym oknem aplikacji, okno ramki jest kontekstem uruchamiania aplikacji WinHelp. Zamknięcie okna ramki spowoduje zamknięcie winhelp. EXE, jeśli został uruchomiony w celu uzyskania pomocy dla tej aplikacji.

Nie należy używać operatora **usuwania** języka C++, aby zniszczyć okno ramki. Zamiast tego użyj polecenia cmdlet `CWnd::DestroyWindow`. Implementacja `CFrameWnd` `PostNcDestroy` spowoduje usunięcie obiektu C++, gdy okno zostanie zniszczone. Gdy użytkownik zamknie okno ramki, wywoła domyślny `OnClose` program obsługi `DestroyWindow`.

Aby uzyskać `CFrameWnd`więcej informacji na temat , zobacz [Ramka Systemu Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CFrameWnd`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cframewndactivateframe"></a><a name="activateframe"></a>CFrameWnd::ActivateFrame

Wywołanie tej funkcji elementu członkowskiego, aby uaktywnić i przywrócić okno ramki, tak aby było widoczne i dostępne dla użytkownika.

```
virtual void ActivateFrame(int nCmdShow = -1);
```

### <a name="parameters"></a>Parametry

*nCmdShow*<br/>
Określa parametr, który ma być przekazywaniem do [CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow). Domyślnie ramka jest wyświetlana i poprawnie przywracana.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest zwykle wywoływana po zdarzeniu interfejsu innego niż interfejs użytkownika, takim jak DDE, OLE lub inne zdarzenie, które może wyświetlać użytkownikowi okno ramki lub jego zawartość.

Domyślna implementacja aktywuje ramkę i przenosi ją na szczyt kolejności Z i, jeśli to konieczne, wykonuje te same kroki dla okna głównej ramki aplikacji.

Zastąpojąć tę funkcję elementu członkowskiego, aby zmienić sposób aktywacji ramki. Na przykład można wymusić okna podrzędne MDI, które mają być zmaksymalizowane. Dodaj odpowiednią funkcjonalność, a następnie wywołaj wersję klasy podstawowej z jawnym *nCmdShow*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#1](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]

## <a name="cframewndbeginmodalstate"></a><a name="beginmodalstate"></a>CFrameWnd::BeginModalState

Wywołanie tej funkcji elementu członkowskiego, aby modal okna ramki.

```
virtual void BeginModalState();
```

## <a name="cframewndcframewnd"></a><a name="cframewnd"></a>CFrameWnd::CFrameWnd

Konstruuje `CFrameWnd` obiekt, ale nie tworzy okna widocznej ramki.

```
CFrameWnd();
```

### <a name="remarks"></a>Uwagi

Wywołanie, `Create` aby utworzyć widoczne okno.

## <a name="cframewndcreate"></a><a name="create"></a>CFrameWnd::Utwórz

Wywołanie utworzenia i zainicjowania okna ramki systemu Windows skojarzonego z obiektem. `CFrameWnd`

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

*lpszClassName (nazwa klasy)*<br/>
Wskazuje ciąg znaków zakończony z wartością null, który nazywa klasę systemu Windows. Nazwa klasy może być dowolną `AfxRegisterWndClass` nazwą zarejestrowaną `RegisterClass` za pomocą funkcji globalnej lub funkcji systemu Windows. Jeśli null, używa wstępnie zdefiniowanych `CFrameWnd` atrybutów domyślnych.

*lpszWindowName*<br/>
Wskazuje ciąg znaków zakończony z wartością null, który reprezentuje nazwę okna. Używany jako tekst paska tytułu.

*Dwstyle*<br/>
Określa atrybuty [stylu](../../mfc/reference/styles-used-by-mfc.md#window-styles) okna. Jeśli pasek tytułu ma automatycznie wyświetlać nazwę dokumentu reprezentowanego w oknie, należy uwzględnić styl FWS_ADDTOTITLE.

*Rect*<br/>
Określa rozmiar i położenie okna. Wartość *rectDefault* umożliwia systemowi Windows określenie rozmiaru i położenia nowego okna.

*pParentWnd*<br/>
Określa okno nadrzędne tego okna ramki. Ten parametr powinien być null dla okien ramki najwyższego poziomu.

*lpszMenuName*<br/>
Identyfikuje nazwę zasobu menu, który ma być używany z oknem. Użyj MAKEINTRESOURCE, jeśli menu ma identyfikator liczby całkowitej zamiast ciągu. Ten parametr może mieć wartość NULL.

*Dwexstyle*<br/>
Określa atrybuty [stylu](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) rozszerzonego okna.

*Pcontext*<br/>
Określa wskaźnik do struktury [CCreateContext.](../../mfc/reference/ccreatecontext-structure.md) Ten parametr może mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli inicjowanie zakończy się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Konstruuj `CFrameWnd` obiekt w dwóch krokach. Najpierw wywołać konstruktora, który `CFrameWnd` konstruuje `Create`obiekt, a następnie wywołać , który `CFrameWnd` tworzy okno ramki systemu Windows i dołącza go do obiektu. `Create`inicjuje nazwę klasy okna i nazwę okna i rejestruje wartości domyślne dla jego stylu, nadrzędnego i skojarzonego menu.

Użyj, `LoadFrame` `Create` a nie załadować okno ramki z zasobu zamiast określania jego argumentów.

## <a name="cframewndcreateview"></a><a name="createview"></a>CFrameWnd::CreateView

Wywołanie, `CreateView` aby utworzyć widok w ramce.

```
CWnd* CreateView(
    CCreateContext* pContext,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>Parametry

*Pcontext*<br/>
Określa typ widoku i dokumentu.

*Nid*<br/>
Numer identyfikatora widoku.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CWnd` obiektu, jeśli zakończy się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego służy do `CView`tworzenia "widoków", które nie są pochodne w ramce. Po `CreateView`wywołaniu należy ręcznie ustawić widok na aktywny i ustawić go jako widoczny; te zadania nie są `CreateView`wykonywane automatycznie przez plik .

## <a name="cframewnddockcontrolbar"></a><a name="dockcontrolbar"></a>CFrameWnd::DockControlBar

Powoduje, że pasek sterowania ma być zadokowany do okna ramki.

```cpp
void DockControlBar(
    CControlBar* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
Wskazuje pasek sterowania, który ma być zadokowany.

*nDockBarID (Identyfikator nDockBarID)*<br/>
Określa, które boki okna ramy należy wziąć pod uwagę do dokowania. Może to być 0 lub co najmniej jedna z następujących czynności:

- AFX_IDW_DOCKBAR_TOP Dock do górnej strony okna ramki.

- AFX_IDW_DOCKBAR_BOTTOM Dock do dolnej części okna ramy.

- AFX_IDW_DOCKBAR_LEFT Dock po lewej stronie okna ramki.

- AFX_IDW_DOCKBAR_RIGHT Dock po prawej stronie okna ramki.

Jeśli 0, pasek sterowania można zadokować do dowolnej strony włączone do dokowania w oknie ramki docelowej.

*Lprect*<br/>
Określa we współrzędnych ekranu, gdzie pasek sterowania będzie zadokowany w obszarze nonclient okna ramki docelowej.

### <a name="remarks"></a>Uwagi

Pasek sterowania zostanie zadokowany do jednej z boków okna ramki określonych w wywołaniach zarówno [CControlBar::EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking) i [CFrameWnd::EnableDocking](#enabledocking). Wybrana strona jest określana przez *nDockBarID*.

## <a name="cframewndenabledocking"></a><a name="enabledocking"></a>CFrameWnd::EnableDocking

Wywołanie tej funkcji, aby włączyć dokowane paski sterowania w oknie ramki.

```cpp
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parametry

*styl dwDockStyle*<br/>
Określa, które strony okna ramki mogą służyć jako miejsca dokowania dla prętów sterujących. Może to być co najmniej jeden z następujących:

- CBRS_ALIGN_TOP Umożliwia dokowanie w górnej części obszaru klienta.

- CBRS_ALIGN_BOTTOM Umożliwia dokowanie w dolnej części obszaru klienta.

- CBRS_ALIGN_LEFT Umożliwia dokowanie po lewej stronie obszaru klienta.

- CBRS_ALIGN_RIGHT Umożliwia dokowanie po prawej stronie obszaru klienta.

- CBRS_ALIGN_ANY Umożliwia dokowanie po dowolnej stronie obszaru klienta.

### <a name="remarks"></a>Uwagi

Domyślnie paski sterowania będą zadokowane z boku okna ramki w następującej kolejności: góra, dół, lewa, prawa.

### <a name="example"></a>Przykład

  Zobacz przykład [CToolBar::Create](../../mfc/reference/ctoolbar-class.md#create).

## <a name="cframewndendmodalstate"></a><a name="endmodalstate"></a>CFrameWnd::EndModalState

Wywołanie tej funkcji elementu członkowskiego, aby zmienić okno ramki z modalnego na trybowe.

```
virtual void EndModalState();
```

### <a name="remarks"></a>Uwagi

`EndModalState`włącza wszystkie okna wyłączone przez [BeginModalState](#beginmodalstate).

## <a name="cframewndfloatcontrolbar"></a><a name="floatcontrolbar"></a>CFrameWnd::FloatControlBar

Wywołanie tej funkcji, aby spowodować, że pasek sterowania nie być zadokowany do okna ramki.

```cpp
void FloatControlBar(
    CControlBar* pBar,
    CPoint point,
    DWORD dwStyle = CBRS_ALIGN_TOP);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
Wskazuje na pasek sterowania, który ma być unoszony.

*Punkt*<br/>
Lokalizacja we współrzędnych ekranu, gdzie w lewym górnym rogu paska sterowania zostanie umieszczony.

*Dwstyle*<br/>
Określa, czy pasek sterowania ma być wyrównywać poziomo czy pionowo w nowym oknie ramki. Może to być dowolna z następujących czynności:

- CBRS_ALIGN_TOP Orientuje pasek sterowania w pionie.

- CBRS_ALIGN_BOTTOM Orientuje pasek sterowania w pionie.

- CBRS_ALIGN_LEFT Orientacja na pasku sterowania w poziomie.

- CBRS_ALIGN_RIGHT Orientacja na pasku sterowania w poziomie.

Jeśli style są przekazywane, określając orientację poziomą i pionową, pasek narzędzi będzie ustawiony w poziomie.

### <a name="remarks"></a>Uwagi

Zazwyczaj odbywa się to podczas uruchamiania aplikacji, gdy program przywraca ustawienia z poprzedniego wykonania.

Ta funkcja jest wywoływana przez platformę, gdy użytkownik powoduje operację upuszczania przez zwolnienie lewego przycisku myszy podczas przeciągania paska sterowania nad lokalizacją, która nie jest dostępna do dokowania.

## <a name="cframewndgetactivedocument"></a><a name="getactivedocument"></a>CFrameWnd::GetActiveDocument

Wywołanie tej funkcji elementu członkowskiego, `CDocument` aby uzyskać wskaźnik do bieżącego dołączonego do bieżącego widoku aktywnego.

```
virtual CDocument* GetActiveDocument();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do bieżącego [CDocument](../../mfc/reference/cdocument-class.md). Jeśli nie ma bieżącego dokumentu, zwraca wartość NULL.

## <a name="cframewndgetactiveframe"></a><a name="getactiveframe"></a>CFrameWnd::GetActiveFrame

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać wskaźnik do aktywnego okna podrzędnego interfejsu wielu dokumentów (MDI) okna ramki MDI.

```
virtual CFrameWnd* GetActiveFrame();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do aktywnego okna podrzędnego MDI. Jeśli aplikacja jest aplikacją SDI lub okno ramki MDI nie ma aktywnego dokumentu, zostanie zwrócony niejawny **ten** wskaźnik.

### <a name="remarks"></a>Uwagi

Jeśli nie ma aktywnego podrzędnego MDI lub aplikacja jest interfejsem pojedynczego dokumentu (SDI), zwracany jest niejawny **ten** wskaźnik.

## <a name="cframewndgetactiveview"></a><a name="getactiveview"></a>CFrameWnd::GetActiveView

Wywołanie tej funkcji elementu członkowskiego w celu uzyskania wskaźnika do aktywnego `CFrameWnd`widoku (jeśli istnieje) dołączonego do okna ramki ( ).

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do bieżącego [widoku CView](../../mfc/reference/cview-class.md). Jeśli nie ma bieżącego widoku, zwraca wartość NULL.

### <a name="remarks"></a>Uwagi

Ta funkcja zwraca wartość NULL po wywołaniu `CMDIFrameWnd`okna ramki głównej MDI ( ). W aplikacji MDI okno ramki głównej MDI nie ma widoku skojarzonego z nim. Zamiast tego każde okno `CMDIChildWnd`podrzędne ( ) ma jeden lub więcej skojarzonych widoków. Aktywny widok w aplikacji MDI można uzyskać, najpierw znajdując aktywne okno podrzędne MDI, a następnie znajdując aktywny widok dla tego okna podrzędnego. Aktywne okno podrzędne MDI można znaleźć, wywołując funkcję `MDIGetActive` lub `GetActiveFrame` jak pokazano w następujących czynnościach:

[!code-cpp[NVC_MFCWindowing#2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]

## <a name="cframewndgetcontrolbar"></a><a name="getcontrolbar"></a>CFrameWnd::GetControlBar

Wywołanie, `GetControlBar` aby uzyskać dostęp do paska sterowania, który jest skojarzony z identyfikatorem.

```
CControlBar* GetControlBar(UINT nID);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Numer identyfikatora paska sterowania.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do paska sterowania, który jest skojarzony z identyfikatorem.

### <a name="remarks"></a>Uwagi

Parametr *nID* odnosi się do unikatowego `Create` identyfikatora przekazanego do metody paska sterowania. Więcej informacji na temat prętów sterujących można znaleźć w temacie zatytułowanym [Paski sterowania](../../mfc/control-bars.md).

`GetControlBar`zwróci pasek sterowania, nawet jeśli jest on przestawny i w związku z tym nie jest obecnie podrzędnym oknem ramki.

## <a name="cframewndgetdockstate"></a><a name="getdockstate"></a>CFrameWnd::GetDockState

Wywołanie tej funkcji elementu członkowskiego do przechowywania informacji o `CDockState` stanie o paskach sterowania okna ramki w obiekcie.

```cpp
void GetDockState(CDockState& state) const;
```

### <a name="parameters"></a>Parametry

*Państwa*<br/>
Zawiera bieżący stan pasków sterujących okna ramki po powrocie.

### <a name="remarks"></a>Uwagi

Następnie można zapisać zawartość `CDockState` do `CDockState::SaveState` magazynu `Serialize`za pomocą lub . Jeśli później chcesz przywrócić paski sterowania do poprzedniego stanu, `CDockState::LoadState` `Serialize`załaduj stan z lub , a następnie wywołaj, `SetDockState` aby zastosować poprzedni stan do pasków sterujących okna ramki.

## <a name="cframewndgetmenubarstate"></a><a name="getmenubarstate"></a>CFrameWnd::GetMenuBarState

Pobiera stan wyświetlania menu w bieżącej aplikacji MFC.

```
virtual DWORD GetMenuBarState();
```

### <a name="return-value"></a>Wartość zwracana

Zwracana wartość może mieć następujące wartości:

- AFX_MBS_VISIBLE (0x01) - Menu jest widoczne.

- AFX_MBS_HIDDEN (0x02) - Menu jest ukryte.

### <a name="remarks"></a>Uwagi

Jeśli wystąpi błąd środowiska uruchomieniowego, ta metoda potwierdza w trybie debugowania i wywołuje wyjątek pochodzący z [CException](../../mfc/reference/cexception-class.md) klasy.

## <a name="cframewndgetmenubarvisibility"></a><a name="getmenubarvisibility"></a>CFrameWnd::GetMenuBarWiętność

Wskazuje, czy domyślny stan menu w bieżącej aplikacji MFC jest ukryty lub widoczny.

```
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```

### <a name="return-value"></a>Wartość zwracana

Ta metoda zwraca jedną z następujących wartości:

- AFX_MBV_KEEPVISIBLE (0x01) — menu jest wyświetlane przez cały czas i domyślnie nie ma fokusu.

- AFX_MBV_DISPLAYONFOCUS (0x02) — menu jest domyślnie ukryte. Jeśli menu jest ukryte, naciśnij klawisz ALT, aby wyświetlić menu i nadać mu fokus. Jeśli menu jest wyświetlane, naciśnij klawisz ALT lub ESC, aby go ukryć.

- AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04) (kombinacja bitowa (OR)) — menu jest domyślnie ukryte. Jeśli menu jest ukryte, naciśnij klawisz F10, aby wyświetlić menu i nadać mu fokus. Jeśli menu jest wyświetlane, naciśnij klawisz F10, aby włączyć fokus lub wyłączyć menu. Menu jest wyświetlane do momentu naciśnięcia klawisza ALT lub ESC, aby go ukryć.

### <a name="remarks"></a>Uwagi

Jeśli wystąpi błąd środowiska uruchomieniowego, ta metoda potwierdza w trybie debugowania i wywołuje wyjątek pochodzący z [CException](../../mfc/reference/cexception-class.md) klasy.

## <a name="cframewndgetmessagebar"></a><a name="getmessagebar"></a>CFrameWnd::Pasek GetMessage

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać wskaźnik do paska stanu.

```
virtual CWnd* GetMessageBar();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okna paska stanu.

## <a name="cframewndgetmessagestring"></a><a name="getmessagestring"></a>CFrameWnd::GetMessageStrowanie

Zastąd w tej funkcji należy podać niestandardowe ciągi dla identyfikatorów poleceń.

```
virtual void GetMessageString(
    UINT nID,
    CString& rMessage) const;
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Identyfikator zasobu żądanej wiadomości.

*rMessage*<br/>
`CString`obiekt, do którego ma być umieszczana wiadomość.

### <a name="remarks"></a>Uwagi

Domyślna implementacja po prostu ładuje ciąg określony przez *nID* z pliku zasobu. Ta funkcja jest wywoływana przez platformę, gdy ciąg komunikatów na pasku stanu wymaga aktualizacji.

## <a name="cframewndgettitle"></a><a name="gettitle"></a>CFrameWnd::GetTitle

Pobiera tytuł obiektu okna.

```
CString GetTitle() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) zawierający bieżący tytuł obiektu okna.

## <a name="cframewndinitialupdateframe"></a><a name="initialupdateframe"></a>CFrameWnd::InitialUpdateFrame

Zadzwoń `IntitialUpdateFrame` po utworzeniu nowej `Create`ramki z .

```cpp
void InitialUpdateFrame(
    CDocument* pDoc,
    BOOL bMakeVisible);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Wskazuje dokument, z którym jest skojarzone okno ramki. Może mieć wartość NULL.

*bMakevisible (Widoczne)*<br/>
Jeśli true, wskazuje, że ramka powinna stać się widoczna i aktywna. Jeśli FALSE, nie elementy podrzędne są widoczne.

### <a name="remarks"></a>Uwagi

Powoduje to, że wszystkie widoki `OnInitialUpdate` w tym oknie ramki do odbierania ich wywołań.

Ponadto jeśli wcześniej nie był aktywny widok, widok podstawowy okna ramki jest aktywny. Widok podstawowy jest widokiem o identyfikatorze podrzędnym AFX_IDW_PANE_FIRST. Na koniec okno ramki jest widoczne, jeśli *bMakeVisible* jest niezerowy. Jeśli *bMakeVisible* wynosi 0, bieżący fokus i widoczny stan okna ramki pozostaną niezmienione. Nie jest konieczne wywołanie tej funkcji podczas korzystania z implementacji struktury File New i File Open.

## <a name="cframewndinmodalstate"></a><a name="inmodalstate"></a>CFrameWnd::Stan InModal

Wywołanie tej funkcji elementu członkowskiego, aby sprawdzić, czy okno ramki jest modalne lub trybowe.

```
BOOL InModalState() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli tak; w przeciwnym razie 0.

## <a name="cframewndistracking"></a><a name="istracking"></a>CFrameWnd::IsTracking

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy pasek rozdzielacza w oknie jest obecnie przenoszony.

```
BOOL IsTracking() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli operacja rozdzielacza jest w toku; w przeciwnym razie 0.

## <a name="cframewndloadacceltable"></a><a name="loadacceltable"></a>CFrameWnd::LoadAccelTable

Wywołanie załadowania określonej tabeli akceleratora.

```
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Identyfikuje nazwę zasobu akceleratora. Użyj MAKEINTRESOURCE, jeśli zasób jest identyfikowany z identyfikatorem liczby całkowitej.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli tabela akceleratora została pomyślnie załadowana; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wraz można załadować tylko jedną tabelę.

Tabele akceleratora ładowane z zasobów są zwalniane automatycznie po zakończeniu aplikacji.

Jeśli wywołasz, `LoadFrame` aby utworzyć okno ramki, struktura ładuje tabelę akceleratora wraz z zasobów menu i ikony, a kolejne wywołanie tej funkcji elementu członkowskiego jest niepotrzebne.

## <a name="cframewndloadbarstate"></a><a name="loadbarstate"></a>CFrameWnd::LoadBarState

Wywołanie tej funkcji, aby przywrócić ustawienia każdego paska sterowania należącego do okna ramki.

```cpp
void LoadBarState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
Nazwa sekcji w pliku inicjowania (INI) lub klucza w rejestrze systemu Windows, w którym przechowywane są informacje o stanie.

### <a name="remarks"></a>Uwagi

Przywrócone informacje obejmują widoczność, orientację poziomą/pionową, stan dokowania i położenie paska sterowania.

Ustawienia, które chcesz przywrócić, muszą zostać zapisane `LoadBarState`w rejestrze przed wywołaniem . Zapisz informacje w rejestrze, wywołując [CWinApp::SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey). Zapisz informacje w pliku INI, wywołując [savebarstate](#savebarstate).

## <a name="cframewndloadframe"></a><a name="loadframe"></a>CFrameWnd::LoadFrame

Wywołanie dynamicznego tworzenia okna ramki na podstawie informacji o zasobach.

```
virtual BOOL LoadFrame(
    UINT nIDResource,
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,
    CWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parametry

*nIDSerwród*<br/>
Identyfikator zasobów udostępnionych skojarzonych z oknem ramki.

*dwDefaultStyle*<br/>
Styl [ramki](../../mfc/reference/styles-used-by-mfc.md#window-styles). Jeśli pasek tytułu ma automatycznie wyświetlać nazwę dokumentu reprezentowanego w oknie, należy uwzględnić styl FWS_ADDTOTITLE.

*pParentWnd*<br/>
Wskaźnik do ramki nadrzędnej.

*Pcontext*<br/>
Wskaźnik do [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) struktury. Ten parametr może mieć wartość NULL.

### <a name="remarks"></a>Uwagi

Konstruuj `CFrameWnd` obiekt w dwóch krokach. Najpierw wywołać konstruktora, który `CFrameWnd` konstruuje `LoadFrame`obiekt, a następnie wywołać , który ładuje okno ramki systemu Windows i skojarzonych zasobów i dołącza okno ramki do `CFrameWnd` obiektu. Parametr *nIDResource* określa menu, tabelę akceleratora, ikonę i zasób ciągu tytułu okna ramki.

Użyj `Create` funkcji elementu `LoadFrame` członkowskiego, a nie wtedy, gdy chcesz określić wszystkie parametry tworzenia okna ramki.

Struktura wywołuje, `LoadFrame` gdy tworzy okno ramki przy użyciu obiektu szablonu dokumentu.

Struktura używa argumentu *pContext,* aby określić obiekty, które mają być połączone z oknem ramki, w tym wszelkie obiekty widoku zamkniętego. Można ustawić argument *pContext* na NULL `LoadFrame`podczas wywoływania .

## <a name="cframewndm_bautomenuenable"></a><a name="m_bautomenuenable"></a>CFrameWnd::m_bAutoMenuEnable

Gdy ten element członkowski danych jest włączony (co jest ustawieniem domyślnym), elementy menu, które nie mają ON_UPDATE_COMMAND_UI lub ON_COMMAND programy obsługi, zostaną automatycznie wyłączone, gdy użytkownik pociągnie w dół menu.

```
BOOL m_bAutoMenuEnable;
```

### <a name="remarks"></a>Uwagi

Elementy menu, które mają ON_COMMAND program obsługi, ale nie ON_UPDATE_COMMAND_UI program obsługi zostanie automatycznie włączony.

Po ustawieniu tego elementu członkowskiego danych elementy menu są automatycznie włączane w taki sam sposób, w jaki są włączone przyciski paska narzędzi.

> [!NOTE]
> `m_bAutoMenuEnable`nie ma wpływu na elementy menu najwyższego poziomu.

Ten element członkowski danych upraszcza implementację opcjonalnych poleceń na podstawie bieżącego wyboru i zmniejsza konieczność zapisywania ON_UPDATE_COMMAND_UI programów obsługi w celu włączania i wyłączania elementów menu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]

## <a name="cframewndnegotiateborderspace"></a><a name="negotiateborderspace"></a>CFrameWnd::NegotiateBorderSpace

Wywołanie tej funkcji elementu członkowskiego do negocjowania miejsca obramowania w oknie ramki podczas ole inplace aktywacji.

```
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,
    LPRECT lpRectBorder);
```

### <a name="parameters"></a>Parametry

*nBorderCmd (właśc.*<br/>
Zawiera jedną z następujących `enum BorderCmd`wartości z :

- `borderGet`= 1

- `borderRequest`= 2

- `borderSet`= 3

*lpRectBorder*<br/>
Wskaźnik do struktury [RECT](/windows/win32/api/windef/ns-windef-rect) lub [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu, który określa współrzędne obramowania.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu `CFrameWnd` członkowskiego jest implementacją negocjacji przestrzeni granicznej OLE.

## <a name="cframewndonbarcheck"></a><a name="onbarcheck"></a>CFrameWnd::OnBarCheck

Wywoływana za każdym razem, gdy akcja jest wykonywana na określonym pasku sterowania.

```
afx_msg BOOL OnBarCheck(UINT nID);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Identyfikator wyświetlanego paska sterowania.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli istniał pasek sterowania; w przeciwnym razie 0.

## <a name="cframewndoncontexthelp"></a><a name="oncontexthelp"></a>CFrameWnd::OnContextHelp

Obsługuje Pomoc SHIFT+F1 dla elementów w miejscu.

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>Uwagi

Aby włączyć pomoc kontekstową, należy dodać

[!code-cpp[NVC_MFCDocViewSDI#16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]

instrukcja `CFrameWnd` do mapy komunikatów klasy, a także dodać wpis tabeli akceleratora, zazwyczaj SHIFT + F1, aby włączyć tę funkcję elementu członkowskiego.

Jeśli aplikacja jest kontenerem `OnContextHelp` OLE, przełącza wszystkie elementy w miejscu zawarte w obiekcie okna ramki w trybie Pomocy. Kursor zmienia się w strzałkę i znak zapytania, a użytkownik może następnie przesunąć wskaźnik myszy i nacisnąć lewy przycisk myszy, aby zaznaczyć okno dialogowe, okno, menu lub przycisk polecenia. Ta funkcja elementu członkowskiego `WinHelp` wywołuje funkcję systemu Windows z kontekstem Pomocy obiektu pod kursorem.

## <a name="cframewndoncreateclient"></a><a name="oncreateclient"></a>CFrameWnd::OnCreateClient

Wywoływane przez ramy podczas `OnCreate`wykonywania .

```
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Parametry

*szt.*<br/>
Wskaźnik do struktury [tworzenia struktury](/windows/win32/api/winuser/ns-winuser-createstructw) systemu Windows.

*Pcontext*<br/>
Wskaźnik do [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) struktury.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Nigdy nie nazywaj tej funkcji.

Domyślna implementacja tej `CView` funkcji tworzy obiekt na podstawie informacji podanych w *pContext*, jeśli to możliwe.

Zastąd w tej funkcji należy `CCreateContext` zastąpić wartości przekazywane w obiekcie lub zmienić sposób tworzenia formantów w głównym obszarze klienta okna ramki. Elementy `CCreateContext` członkowskie, które można zastąpić są opisane w [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) klasy.

> [!NOTE]
> Nie należy zastępować `CREATESTRUCT` wartości przekazanych w strukturze. Służą wyłącznie do użytku informacyjnego. Jeśli chcesz zastąpić początkowy prostokąt okna, na przykład zastąpomij `CWnd` funkcję elementu członkowskiego [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).

## <a name="cframewndonhidemenubar"></a><a name="onhidemenubar"></a>CFrameWnd::OnHideMenuBar

Ta funkcja jest wywoływana, gdy system ma zamiar ukryć pasek menu w bieżącej aplikacji MFC.

```
virtual void OnHideMenuBar();
```

### <a name="remarks"></a>Uwagi

Ten program obsługi zdarzeń umożliwia aplikacji wykonywanie akcji niestandardowych, gdy system ma zamiar ukryć menu. Nie można zapobiec ukryciu menu, ale można na przykład wywołać inne metody, aby pobrać styl menu lub stan.

## <a name="cframewndonsetpreviewmode"></a><a name="onsetpreviewmode"></a>CFrameWnd::OnSetPreviewMode

Wywołanie tej funkcji elementu członkowskiego, aby ustawić okno ramki głównej aplikacji do trybu podglądu wydruku i z nich.

```
virtual void OnSetPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>Parametry

*bPreview*<br/>
Określa, czy aplikacja ma być umieszczana w trybie podglądu wydruku. Ustaw wartość TRUE, aby umieścić w podglądzie wydruku, FALSE, aby anulować tryb podglądu.

*pPaństwo*<br/>
Wskaźnik do `CPrintPreviewState` struktury.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wyłącza wszystkie standardowe paski narzędzi i ukrywa menu główne i okno klienta głównego. Spowoduje to przekształcie okna ramek MDI w tymczasowe okna ramki SDI.

Zastąpokaj tę funkcję elementu członkowskiego, aby dostosować ukrywanie i pokazywanie pasków sterujących i innych części okna ramki podczas podglądu wydruku. Wywołanie implementacji klasy podstawowej z poziomu wersji zastąpione.

## <a name="cframewndonshowmenubar"></a><a name="onshowmenubar"></a>CFrameWnd::OnShowMenuBar

Ta funkcja jest wywoływana, gdy system ma zamiar wyświetlić pasek menu w bieżącej aplikacji MFC.

```
virtual void OnShowMenuBar();
```

### <a name="remarks"></a>Uwagi

Ten program obsługi zdarzeń umożliwia aplikacji wykonywanie akcji niestandardowych, gdy menu ma być wyświetlany. Nie można zapobiec wyświetlaniu menu, ale można na przykład wywołać inne metody, aby pobrać styl menu lub stan.

## <a name="cframewndonupdatecontrolbarmenu"></a><a name="onupdatecontrolbarmenu"></a>CFrameWnd::OnUpdateControlBarMenu

Wywoływane przez strukturę, gdy skojarzone menu jest aktualizowana.

```
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do obiektu [CCmdUI](../../mfc/reference/ccmdui-class.md) reprezentujący menu, które wygenerowało polecenie aktualizacji. Program obsługi aktualizacji wywołuje włącz `CCmdUI` funkcję [elementu](../../mfc/reference/ccmdui-class.md#enable) członkowskiego obiektu za pośrednictwem *pCmdUI,* aby zaktualizować interfejs użytkownika.

## <a name="cframewndrecalclayout"></a><a name="recalclayout"></a>CFrameWnd::RecalcLayout

Wywoływana przez strukturę, gdy standardowe paski sterowania są włączane lub wyłączane lub gdy zmienia się rozmiar okna ramki.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parametry

*bNotuj*<br/>
Określa, czy aktywny element w miejscu dla okna ramki otrzymuje powiadomienie o zmianie układu. Jeśli true, element jest powiadamiany; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji `CWnd` elementu `RepositionBars` członkowskiego wywołuje funkcję elementu członkowskiego, aby zmienić położenie wszystkich `CView` pasków sterowania w ramce, a także w głównym oknie klienta (zwykle a lub MDICLIENT).

Zastąpokaj tę funkcję elementu członkowskiego, aby kontrolować wygląd i zachowanie pasków sterowania po zmianie układu okna ramki. Na przykład wywołać go po włączeniu lub wyłączeniu prętów sterujących lub dodać inny pasek sterowania.

## <a name="cframewndrectdefault"></a><a name="rectdefault"></a>CFrameWnd::rectDefault

Przekaż ten `CRect` statyczny jako parametr podczas tworzenia okna, aby umożliwić systemowi Windows wybranie początkowego rozmiaru i położenia okna.

```
static AFX_DATA const CRect rectDefault;
```

## <a name="cframewndsavebarstate"></a><a name="savebarstate"></a>CFrameWnd::Stan przycisków SaveBar

Wywołanie tej funkcji do przechowywania informacji o każdym pasku sterowania należącym do okna ramki.

```cpp
void SaveBarState(LPCTSTR lpszProfileName) const;
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
Nazwa sekcji w pliku inicjowania lub klucza w rejestrze systemu Windows, w którym przechowywane są informacje o stanie.

### <a name="remarks"></a>Uwagi

Te informacje można odczytać z pliku inicjowania za pomocą [LoadBarState](#loadbarstate). Przechowywane informacje obejmują widoczność, orientację poziomą/pionową, stan dokowania i położenie paska sterowania.

## <a name="cframewndsetactivepreviewview"></a><a name="setactivepreviewview"></a>CFrameWnd::SetActivePreview

Wyznacza określony widok jako aktywny widok dla zaawansowanego podglądu.

```cpp
void SetActivePreviewView(CView* pViewNew);
```

### <a name="parameters"></a>Parametry

*pViewNowy*<br/>
Wskaźnik do widoku, który ma zostać aktywowany.

### <a name="remarks"></a>Uwagi

## <a name="cframewndsetactiveview"></a><a name="setactiveview"></a>CFrameWnd::SetActiveView

Wywołanie tej funkcji elementu członkowskiego, aby ustawić widok aktywny.

```cpp
void SetActiveView(
    CView* pViewNew,
    BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parametry

*pViewNowy*<br/>
Określa wskaźnik do obiektu [CView](../../mfc/reference/cview-class.md) lub NULL dla braku aktywnego widoku.

*bNotuj*<br/>
Określa, czy widok ma być powiadamiany o aktywacji. Jeśli TRUE, `OnActivateView` jest wywoływana dla nowego widoku; jeśli FALSE, to nie jest.

### <a name="remarks"></a>Uwagi

Struktura wywoła tę funkcję automatycznie, gdy użytkownik zmieni fokus na widok w oknie ramki. Można jawnie `SetActiveView` wywołać, aby zmienić fokus do określonego widoku.

## <a name="cframewndsetdockstate"></a><a name="setdockstate"></a>CFrameWnd::Stan SetDock

Wywołanie tej funkcji elementu członkowskiego, `CDockState` aby zastosować informacje o stanie przechowywane w obiekcie do pasków sterowania okna ramki.

```cpp
void SetDockState(const CDockState& state);
```

### <a name="parameters"></a>Parametry

*Państwa*<br/>
Zastosuj stan przechowywany do pasków sterujących okna ramki.

### <a name="remarks"></a>Uwagi

Aby przywrócić poprzedni stan prętów sterujących, można `CDockState::LoadState` załadować stan przechowywany z lub `Serialize`, a następnie użyć, `SetDockState` aby zastosować go do pasków sterujących okna ramki. Poprzedni stan jest przechowywany `CDockState` w obiekcie`GetDockState`

## <a name="cframewndsetmenubarstate"></a><a name="setmenubarstate"></a>CFrameWnd::SetMenuBarState

Ustawia stan wyświetlania menu w bieżącej aplikacji MFC na ukryte lub wyświetlane.

```
virtual BOOL SetMenuBarState(DWORD nState);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*nPaństwo*|[w] Określa, czy menu ma być wyświetlane, czy ukrywane. Parametr *nState* może mieć następujące wartości:<br /><br />- AFX_MBS_VISIBLE (0x01) - Wyświetla menu, jeśli jest ukryte, ale nie ma wpływu, jeśli jest widoczne.<br />- AFX_MBS_HIDDEN (0x02) - Ukrywa menu, jeśli jest widoczne, ale nie ma wpływu, jeśli jest ukryty.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda pomyślnie zmienia stan menu; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli wystąpi błąd środowiska uruchomieniowego, ta metoda potwierdza w trybie debugowania i wywołuje wyjątek pochodzący z [CException](../../mfc/reference/cexception-class.md) klasy.

## <a name="cframewndsetmenubarvisibility"></a><a name="setmenubarvisibility"></a>CFrameWnd::SetMenuBarWiękność

Ustawia domyślne zachowanie menu w bieżącej aplikacji MFC, które ma być ukryte lub widoczne.

```
virtual void SetMenuBarVisibility(DWORD nStyle);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*styl nStyle*|[w] Określa, czy menu jest domyślnie ukryte, czy jest widoczne i ma fokus. Parametr *nStyle* może mieć następujące wartości:<br /><br />- AFX_MBV_KEEPVISIBLE (0x01) -<br />     Menu jest wyświetlane przez cały czas i domyślnie nie ma fokusu.<br />- AFX_MBV_DISPLAYONFOCUS (0x02) -<br />     Menu jest domyślnie ukryte. Jeśli menu jest ukryte, naciśnij klawisz ALT, aby wyświetlić menu i nadać mu fokus. Jeśli menu jest wyświetlane, naciśnij klawisz ALT lub ESC, aby ukryć menu.<br />- AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04)<br />     (kombinacja bitowa (OR)) — menu jest domyślnie ukryte. Jeśli menu jest ukryte, naciśnij klawisz F10, aby wyświetlić menu i nadać mu fokus. Jeśli menu jest wyświetlane, naciśnij klawisz F10, aby włączyć fokus lub wyłączyć menu. Menu jest wyświetlane do momentu naciśnięcia klawisza ALT lub ESC, aby go ukryć.|

### <a name="remarks"></a>Uwagi

Jeśli wartość parametru *nStyle* jest nieprawidłowa, ta metoda potwierdza w trybie debugowania i podnosi [CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md) w trybie wydania. W przypadku innych błędów środowiska uruchomieniowego ta metoda potwierdza w trybie debugowania i wywołuje wyjątek pochodzący z [CException](../../mfc/reference/cexception-class.md) klasy.

Ta metoda wpływa na stan menu w aplikacjach napisanych dla systemu Windows Vista i nowszych.

## <a name="cframewndsetmessagetext"></a><a name="setmessagetext"></a>CFrameWnd::SetMessageText

Wywołanie tej funkcji, aby umieścić ciąg w okienku paska stanu, który ma identyfikator 0.

```cpp
void SetMessageText(LPCTSTR lpszText);
void SetMessageText(UINT nID);
```

### <a name="parameters"></a>Parametry

*lpszText (tekst)*<br/>
Wskazuje ciąg, który ma zostać umieszczony na pasku stanu.

*Nid*<br/>
Identyfikator zasobu ciągu ciągu, który ma zostać umieszczony na pasku stanu.

### <a name="remarks"></a>Uwagi

Jest to zazwyczaj lewe i najdłuższe okienko paska stanu.

## <a name="cframewndsetprogressbarposition"></a><a name="setprogressbarposition"></a>CFrameWnd::SetProgressBarPosition

Ustawia bieżącą pozycję paska postępu systemu Windows 7 wyświetlanego na pasku zadań.

```cpp
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>Parametry

*nProgressPos*<br/>
Określa położenie do ustawionego. Musi mieszczeć się `SetProgressBarRange`w zakresie określonym przez .

### <a name="remarks"></a>Uwagi

## <a name="cframewndsetprogressbarrange"></a><a name="setprogressbarrange"></a>CFrameWnd::SetProgressBarRange

Ustawia zakres paska postępu systemu Windows 7 wyświetlanego na pasku zadań.

```cpp
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>Parametry

*nRangeMin (nRangeMin)*<br/>
Minimalna wartość.

*nRangeMax (Polski)*<br/>
Maksymalna wartość.

### <a name="remarks"></a>Uwagi

## <a name="cframewndsetprogressbarstate"></a><a name="setprogressbarstate"></a>CFrameWnd::Stan zestawu

Ustawia typ i stan wskaźnika postępu wyświetlanego na przycisku paska zadań.

```cpp
void SetProgressBarState(TBPFLAG tbpFlags);
```

### <a name="parameters"></a>Parametry

*tbpFlags*<br/>
Flagi, które kontrolują bieżący stan przycisku postępu. Określ tylko jedną z następujących flag, ponieważ wszystkie stany wzajemnie się wykluczają: TBPF_NOPROGRESS, TBPF_INDETERMINATE, TBPF_NORMAL, TBPF_ERROR, TBPF_PAUSED.

### <a name="remarks"></a>Uwagi

## <a name="cframewndsettaskbaroverlayicon"></a><a name="settaskbaroverlayicon"></a>CFrameWnd::SetTaskbarOverlayIcon

Przeciążone. Stosuje nakładkę do przycisku paska zadań, aby wskazać stan aplikacji lub powiadomić użytkownika.

```
BOOL SetTaskbarOverlayIcon(
    UINT nIDResource,
    LPCTSTR lpcszDescr);

BOOL SetTaskbarOverlayIcon(
    HICON hIcon,
    LPCTSTR lpcszDescr);
```

### <a name="parameters"></a>Parametry

*nIDSerwród*<br/>
Określa identyfikator zasobu ikony, która ma być używana jako nakładka. Szczegółowe informacje można znaleźć w *opisie hIcon.*

*lpcszDescr (właśc.*<br/>
Wskaźnik do ciągu, który zawiera alternatywną wersję tekstu informacji przekazywanych przez nakładkę, w celach ułatwień dostępu.

*hIcon (własówce)*<br/>
Uchwyt ikony do użycia jako nakładki. Powinna to być mała ikona, mierzącya 16x16 pikseli przy 96 punktach na cal (dpi). Jeśli ikona nakładki jest już zastosowana do przycisku paska zadań, ta istniejąca nakładka zostanie zastąpiona. Ta wartość może być null. Sposób obsługi wartości NULL zależy od tego, czy przycisk paska zadań reprezentuje pojedyncze okno, czy grupę okien. Jest to odpowiedzialność aplikacji wywołującej do uwolnienia *hIcon,* gdy nie jest już potrzebne.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli się powiedzie; FALSE, jeśli wersja systemu operacyjnego jest mniejsza niż Windows 7 lub jeśli wystąpi błąd ustawienie ikony.

### <a name="remarks"></a>Uwagi

## <a name="cframewndsettitle"></a><a name="settitle"></a>CFrameWnd::SetTitle

Ustawia tytuł obiektu okna.

```cpp
void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>Parametry

*lpszTitle (lpszTitle)*<br/>
Wskaźnik do ciągu znaków zawierającego tytuł obiektu okna.

## <a name="cframewndshowcontrolbar"></a><a name="showcontrolbar"></a>CFrameWnd::ShowControlBar

Wywołanie tej funkcji elementu członkowskiego, aby pokazać lub ukryć pasek sterowania.

```cpp
void ShowControlBar(
    CControlBar* pBar,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
Wskaźnik do paska sterowania, który ma być wyświetlany lub ukryty.

*bPokaż*<br/>
Jeśli true, określa, że pasek sterowania ma być wyświetlany. Jeśli FALSE, określa, że pasek sterowania ma być ukryty.

*bDelay (własówce)*<br/>
Jeśli wartość TRUE, opóźnienie wyświetlania paska sterowania. Jeśli FAŁD, natychmiast pokaż pasek sterowania.

## <a name="cframewndshowownedwindows"></a><a name="showownedwindows"></a>CFrameWnd::ShowOwnedWindows

Wywołanie tej funkcji elementu członkowskiego, aby `CFrameWnd` wyświetlić wszystkie okna, które są elementami podrzędnymi obiektu.

```cpp
void ShowOwnedWindows(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bPokaż*<br/>
Określa, czy posiadane okna mają być wyświetlane, czy ukryte.

## <a name="see-also"></a>Zobacz też

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Klasa CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)<br/>
[Klasa CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)<br/>
[Klasa CView](../../mfc/reference/cview-class.md)<br/>
[Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Struktura CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)
