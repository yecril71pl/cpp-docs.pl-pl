---
title: Klasa CFrameWnd | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d2dee6c5157858fef2bd26101ac128ff3d53d23
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337385"
---
# <a name="cframewnd-class"></a>Klasa CFrameWnd
Oferuje funkcje Windows interfejsu pojedynczego dokumentu (SDI) nachodzącego lub wyskakującego ramki okna, wraz z elementami członkowskimi do zarządzania oknem.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CFrameWnd : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFrameWnd::CFrameWnd](#cframewnd)|Konstruuje `CFrameWnd` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFrameWnd::ActivateFrame](#activateframe)|Sprawia, że ramka widoczne i dostępne dla użytkownika.|  
|[CFrameWnd::BeginModalState](#beginmodalstate)|Ustawia modalne okno ramek.|  
|[CFrameWnd::Create](#create)|Wywołanie, aby utworzyć i zainicjować okno ramek Windows, które są skojarzone z `CFrameWnd` obiektu.|  
|[CFrameWnd::CreateView](#createview)|Tworzy widok w ramce, która nie pochodzi od `CView`.|  
|[CFrameWnd::DockControlBar](#dockcontrolbar)|Dokowane paska sterowania.|  
|[CFrameWnd::EnableDocking](#enabledocking)|Umożliwia jest zadokowany pasek sterowania.|  
|[CFrameWnd::EndModalState](#endmodalstate)|Kończy się stanu modalnego okna ramki. Umożliwia obsługę systemu windows, wyłączona przez `BeginModalState`.|  
|[CFrameWnd::FloatControlBar](#floatcontrolbar)|Liczby zmiennoprzecinkowe paska sterowania.|  
|[CFrameWnd::GetActiveDocument](#getactivedocument)|Zwraca aktywne `CDocument` obiektu.|  
|[CFrameWnd::GetActiveFrame](#getactiveframe)|Zwraca aktywne `CFrameWnd` obiektu.|  
|[CFrameWnd::GetActiveView](#getactiveview)|Zwraca aktywne `CView` obiektu.|  
|[CFrameWnd::GetControlBar](#getcontrolbar)|Pobiera paska sterowania.|  
|[CFrameWnd::GetDockState](#getdockstate)|Pobiera stan dock okna ramki.|  
|[CFrameWnd::GetMenuBarState](#getmenubarstate)|Pobiera stan wyświetlania menu w bieżącej aplikacji MFC.|  
|[CFrameWnd::GetMenuBarVisibility](#getmenubarvisibility)|Wskazuje, czy domyślne zachowanie menu w bieżącej aplikacji MFC jest ukrytych lub widocznych.|  
|[CFrameWnd::GetMessageBar](#getmessagebar)|Zwraca wskaźnik do stanu paska należących do ramki okna.|  
|[CFrameWnd::GetMessageString](#getmessagestring)|Pobiera wiadomość odpowiadający identyfikator polecenia.|  
|[CFrameWnd::GetTitle](#gettitle)|Pobiera tytuł paska sterowania powiązane.|  
|[CFrameWnd::InitialUpdateFrame](#initialupdateframe)|Powoduje, że `OnInitialUpdate` funkcja elementu członkowskiego należących do wszystkich widoków w oknie ramki, który ma zostać wywołana.|  
|[CFrameWnd::InModalState](#inmodalstate)|Zwraca wartość wskazującą, czy okno ramowe jest w stanie modalnych.|  
|[CFrameWnd::IsTracking](#istracking)|Określa, jeśli obecnie Trwa przenoszenie pasek podziału.|  
|[CFrameWnd::LoadAccelTable](#loadacceltable)|Wywołać można załadować tabeli klawiszy skrótu.|  
|[CFrameWnd::LoadBarState](#loadbarstate)|Wywołanie, aby przywrócić ustawienia paska sterowania.|  
|[CFrameWnd::LoadFrame](#loadframe)|Wywołanie dynamicznego tworzenia okno ramowe z informacji o zasobie.|  
|[CFrameWnd::NegotiateBorderSpace](#negotiateborderspace)|Negocjuje obramowania miejsce w oknie ramki.|  
|[CFrameWnd::OnBarCheck](#onbarcheck)|Wywoływana zawsze wtedy, gdy akcja jest wykonywana na pasku określoną kontrolkę.|  
|[CFrameWnd::OnContextHelp](#oncontexthelp)|Obsługuje SHIFT + F1 Pomoc dla elementów w miejscu.|  
|[CFrameWnd::OnSetPreviewMode](#onsetpreviewmode)|Ustawia aplikacji głównej ramki okna w i poza trybem Podgląd wydruku.|  
|[CFrameWnd::OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|Wywoływane przez platformę, po zaktualizowaniu skojarzonego menu.|  
|[CFrameWnd::RecalcLayout](#recalclayout)|Zmienia położenie pasków sterowania `CFrameWnd` obiektu.|  
|[CFrameWnd::SaveBarState](#savebarstate)|Wywołanie, aby zapisać ustawienia paska sterowania.|  
|[CFrameWnd::SetActivePreviewView](#setactivepreviewview)|Wskazuje określony widok jako widok aktywny podglądu sformatowanego.|  
|[CFrameWnd::SetActiveView](#setactiveview)|Ustawia aktywny `CView` obiektu.|  
|[CFrameWnd::SetDockState](#setdockstate)|Wywołanie, aby zadokować okno ramowe w głównym oknie.|  
|[CFrameWnd::SetMenuBarState](#setmenubarstate)|Ustawia stan wyświetlania menu w bieżącej aplikacji MFC w ukrytych lub wyświetlone.|  
|[CFrameWnd::SetMenuBarVisibility](#setmenubarvisibility)|Ustawia domyślne zachowanie menu w bieżącej aplikacji MFC w ukrytych lub widocznych.|  
|[CFrameWnd::SetMessageText](#setmessagetext)|Ustawia tekst paska stanu standardowych.|  
|[CFrameWnd::SetProgressBarPosition](#setprogressbarposition)|Ustawia bieżącej pozycji paska postępu Windows 7, wyświetlany na pasku zadań.|  
|[CFrameWnd::SetProgressBarRange](#setprogressbarrange)|Określa zakres dla paska postępu Windows 7, wyświetlany na pasku zadań.|  
|[CFrameWnd::SetProgressBarState](#setprogressbarstate)|Ustawia typ i stan wskaźnik postępu, wyświetlany na przycisku na pasku zadań.|  
|[CFrameWnd::SetTaskbarOverlayIcon](#settaskbaroverlayicon)|Przeciążone. Dotyczy nakładki przycisk paska zadań w celu wskazania stanu aplikacji lub powiadomienie do użytkownika.|  
|[CFrameWnd::SetTitle](#settitle)|Ustawia tytuł paska sterowania powiązane.|  
|[CFrameWnd::ShowControlBar](#showcontrolbar)|Wywołanie, aby pokazać pasek sterowania.|  
|[CFrameWnd::ShowOwnedWindows](#showownedwindows)|Przedstawia wszystkie systemy windows, które są elementami podrzędnymi `CFrameWnd` obiektu.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFrameWnd::OnCreateClient](#oncreateclient)|Tworzy okno klienckie ramki.|  
|[CFrameWnd::OnHideMenuBar](#onhidemenubar)|Metoda wywoływana przed menu w bieżącej aplikacji MFC jest ukryty.|  
|[CFrameWnd::OnShowMenuBar](#onshowmenubar)|Wywołuje się, zanim zostanie wyświetlone menu w bieżącej aplikacji MFC.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFrameWnd::m_bAutoMenuEnable](#m_bautomenuenable)|Formanty automatyczne włączanie i wyłączanie funkcji dla elementów menu.|  
|[CFrameWnd::rectDefault](#rectdefault)|Przekazać ten statyczny `CRect` jako parametr podczas tworzenia `CFrameWnd` obiektu, aby umożliwić Windows wybrać początkowy rozmiar i położenie okna.|  
  
## <a name="remarks"></a>Uwagi  
 Aby utworzyć okno ramowe przydatne dla aplikacji, należy wyprowadzić klasę z `CFrameWnd`. Dodaj zmienne do klasy pochodnej w celu przechowywania danych specyficznych dla aplikacji. Implementowanie obsługi wiadomości elementów członkowskich, a także wiadomość, mapowania w klasie pochodnej, aby określić, co się stanie, gdy komunikaty są kierowane do okna.  
  
 Istnieją trzy sposoby, aby utworzyć okno ramowe:  
  
-   Bezpośrednio utworzenia go za pomocą [Utwórz](#create).  
  
-   Bezpośrednio utworzenia go za pomocą [loadframe —](#loadframe).  
  
-   Pośrednio utworzenia go za pomocą szablonu dokumentu.  
  
 Przed wywołaniem albo `Create` lub `LoadFrame`, należy utworzyć obiekt okno ramek na stosie przy użyciu języka C++ **nowe** operatora. Przed wywołaniem `Create`, możesz także zarejestrować klasy okna za pomocą [afxregisterwndclass —](../../mfc/reference/application-information-and-management.md#afxregisterwndclass) funkcja globalna, aby ustawić ikonę i klasa style ramki.  
  
 Użyj `Create` funkcja elementu członkowskiego do przekazania parametrów tworzenia ramki natychmiastowego jako argumenty.  
  
 `LoadFrame` wymaga mniej argumentów niż `Create`i zamiast tego pobiera najbardziej jej wartości domyślnej z zasobów, w tym podpis ramki, ikony, tabeli akceleratora i menu. Dostępne przez `LoadFrame`, te zasoby musi mieć ten sam identyfikator zasobów (na przykład IDR_MAINFRAME).  
  
 Gdy `CFrameWnd` obiekt zawiera widoki i dokumentów, są tworzone bezpośrednio przez platformę, a nie bezpośrednio przez programistę. `CDocTemplate` Obiektu organizuje tworzenia ramki, tworzenie widoków zawierających i połączenie widoków do odpowiedniego dokumentu. Parametry `CDocTemplate` Określ Konstruktor `CRuntimeClass` trzy klasy zaangażowana (dokument, ramki i widoku). A `CRuntimeClass` obiekt jest używany przez platformę do dynamicznego tworzenia nowych ramek, gdy określony przez użytkownika (na przykład przy użyciu polecenia nowy plik lub wiele nowego okna polecenia interfejsu (MDI) dokumentu).  
  
 Pochodne klasy okien ramowych `CFrameWnd` musi być zadeklarowany z DECLARE_DYNCREATE w kolejności dla powyższych mechanizmu RUNTIME_CLASS działała prawidłowo.  
  
 Element `CFrameWnd` zawiera domyślne implementacje do przeprowadzenia następujących funkcji Okno główne w typowej aplikacji dla Windows:  
  
-   A `CFrameWnd` okno ramowe śledzi informacje o aktualnie aktywnego widoku, który jest niezależny od aktywnego okna Windows lub bieżący fokus wprowadzania. Podczas ponownego uaktywniania ramki bieżącym widokiem jest powiadamiany przez wywołanie metody `CView::OnActivateView`.  
  
-   Polecenie komunikatów i wiele typowych komunikatów ramki powiadomień, łącznie z tymi obsługiwane przez `OnSetFocus`, `OnHScroll`, i `OnVScroll` funkcji `CWnd`, są delegowane przez `CFrameWnd` ramki okna, aby wyświetlić aktualnie aktywny.  
  
-   Aktualnie aktywnego widoku (lub aktywnym oknem ramki podrzędnego MDI w przypadku ramki MDI) można określić napis ramki okna. Tę funkcję można wyłączyć przez wyłączenie FWS_ADDTOTITLE bitu stylu ramki okna.  
  
-   A `CFrameWnd` okno ramowe zarządza pozycjonowanie paski sterowania, widoki i inne okna podrzędne wewnątrz obszaru klienckiego okna ramki. Okno ramowe wykonywane jest także czas bezczynności (%) aktualizowanie narzędzi i inne przyciski paska sterowania. A `CFrameWnd` okno ramowe również ma domyślnej implementacji poleceń przełączania włączać i wyłączać narzędzi i pasek stanu.  
  
-   A `CFrameWnd` okno ramowe zarządza na pasku menu głównego. Po wyświetleniu menu podręcznego okno ramowe używa mechanizmu UPDATE_COMMAND_UI, aby określić elementy menu, które powinny być włączone, wyłączone lub zaznaczone. Gdy użytkownik wybierze element menu, okno ramowe aktualizacji na pasku stanu parametrami komunikatu dla tego polecenia.  
  
-   A `CFrameWnd` okno ramowe ma tabeli akceleratora opcjonalne automatycznie konwertująca klawiszy skrótów.  
  
-   A `CFrameWnd` okno ramowe ma identyfikator pomocy opcjonalny zestaw z `LoadFrame` używanego do obsługi pomocy kontekstowej. Okno ramki jest główne koordynatora stany półmodalne, takich jak trybach Podgląd wydruku i pomocy kontekstowej (SHIFT + F1).  
  
-   A `CFrameWnd` okno ramowe zostanie otwarty plik przeciągnięty Menedżerze plików i porzucić w oknie ramek. Jeśli rozszerzenie jest zarejestrowane i powiązane z daną aplikacją, okno ramowe odpowiada na żądanie Otwórz exchange (DDE) dane dynamiczne, który występuje, gdy użytkownik otwiera plik danych w programie Menedżer plików lub `ShellExecute` Windows funkcja jest wywoływana.  
  
-   Jeśli okno ramki jest okna głównego aplikacji (oznacza to, że `CWinThread::m_pMainWnd`), gdy użytkownik zamknie aplikacji, okno ramowe monituje użytkownika o Zapisz wszystkie zmodyfikowane dokumenty (dla `OnClose` i `OnQueryEndSession`).  
  
-   Jeśli okno ramki jest okna głównego aplikacji, okno ramki jest kontekst do uruchamiania WinHelp. Zamyka okno ramowe zostanie zamknięty w Pomocy systemu Windows. Plik EXE, jeśli został uruchomiony pomocy dla tej aplikacji.  
  
 Nie należy używać języka C++ **Usuń** operator można zniszczyć okna ramki. Zamiast nich należy używać słów kluczowych `CWnd::DestroyWindow`. `CFrameWnd` Implementacji `PostNcDestroy` spowoduje usunięcie obiektu języka C++, kiedy niszczony jest okna. Gdy użytkownik zamknie okno ramowe domyślnie `OnClose` wywoła procedurę obsługi `DestroyWindow`.  
  
 Aby uzyskać więcej informacji na temat `CFrameWnd`, zobacz [Windows ramki](../../mfc/frame-windows.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CFrameWnd`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="activateframe"></a>  CFrameWnd::ActivateFrame  
 Wywołaj tę funkcję elementu członkowskiego, aby aktywować i przywraca ramkę okna, tak aby był widoczny i dostępny dla użytkownika.  
  
```  
virtual void ActivateFrame(int nCmdShow = -1);
```  
  
### <a name="parameters"></a>Parametry  
 *nCmdShow*  
 Określa parametr do przekazania do [CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow). Domyślnie ramki jest wyświetlane i poprawnie przywrócona.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego jest zazwyczaj wywoływana po wystąpieniu zdarzenia interfejsu niezwiązanych z użytkownikiem, takie jak DDE, OLE lub inne zdarzenia, które mogą być wyświetlane okno ramowe lub jego zawartość do użytkownika.  
  
 Domyślna implementacja aktywuje ramki i udostępnia go do góry porządku osi Z, a w razie potrzeby wykonuje te same kroki dla aplikacji głównej ramki okna.  
  
 Zastąpienie tej funkcji elementu członkowskiego, aby zmienić sposób ramki jest aktywowana. Na przykład możesz wymusić oknami podrzędnymi MDI, aby zmaksymalizować. Dodaj odpowiednie funkcje, a następnie wywołać wersję klasy podstawowej z jawną *nCmdShow*.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#1](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]  
  
##  <a name="beginmodalstate"></a>  CFrameWnd::BeginModalState  
 Wywołaj tę funkcję elementu członkowskiego, aby utworzyć modalne okno ramki.  
  
```  
virtual void BeginModalState();
```  
  
##  <a name="cframewnd"></a>  CFrameWnd::CFrameWnd  
 Konstruuje `CFrameWnd` obiektu, ale nie tworzy okno ramowe widoczne.  
  
```  
CFrameWnd();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj `Create` można utworzyć okna widoczne.  
  
##  <a name="create"></a>  CFrameWnd::Create  
 Wywołanie, aby utworzyć i zainicjować okno ramek Windows, które są skojarzone z `CFrameWnd` obiektu.  
  
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
 *lpszClassName*  
 Wskazuje ciąg znaków zakończony znakiem null, że nazwy klas Windows. Nazwa klasy może być dowolna nazwa, zarejestrowane w usłudze `AfxRegisterWndClass` funkcja globalna lub `RegisterClass` funkcji Windows. Jeśli ma wartość NULL, używa wstępnie zdefiniowanego domyślnego `CFrameWnd` atrybutów.  
  
 *lpszWindowName*  
 Wskazuje ciąg znaków zakończony znakiem null, który reprezentuje nazwę okna. Używane jako tekst, na pasku tytułu.  
  
 *dwStyle*  
 Określa okna [styl](../../mfc/reference/styles-used-by-mfc.md#window-styles) atrybutów. Obejmują styl FWS_ADDTOTITLE, jeśli chcesz, aby pasek tytułu, aby automatycznie wyświetlać nazwy dokumentu, reprezentowany w oknie.  
  
 *Rect*  
 Określa rozmiar i położenie okna. *RectDefault* zezwala na wartość Windows określić rozmiar i położenie w nowym oknie.  
  
 *pParentWnd*  
 Określa okno nadrzędne tego okna ramki. Ten parametr powinien być NULL dla okien ramowych najwyższego poziomu.  
  
 *lpszMenuName*  
 Określa nazwę zasobu menu, który ma być używany z oknem. Użyj MAKEINTRESOURCE, gdy menu ma identyfikator całkowitoliczbowy zamiast ciągu. Ten parametr może mieć wartości NULL.  
  
 *dwExStyle*  
 Określa okno rozszerzone [styl](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) atrybutów.  
  
 *pContext*  
 Określa wskaźnik [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) struktury. Ten parametr może mieć wartości NULL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli inicjowanie zakończy się; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Konstruowania `CFrameWnd` obiektu w dwóch krokach. Po pierwsze wywołanie konstruktora, który tworzy `CFrameWnd` obiektu, a następnie wywołaj `Create`, który tworzy ramkę okna Windows i dołącza go do `CFrameWnd` obiektu. `Create` Inicjuje nazwy klasy okna i okna, a następnie rejestruje wartości domyślne dla jego styl, nadrzędny i związanych z menu.  
  
 Użyj `LoadFrame` zamiast `Create` załadować okno ramowe z zasobem zamiast określania argumentów.  
  
##  <a name="createview"></a>  CFrameWnd::CreateView  
 Wywołaj `CreateView` do utworzenia widoku w ramce.  
  
```  
CWnd* CreateView(
    CCreateContext* pContext,  
    UINT nID = AFX_IDW_PANE_FIRST);
```  
  
### <a name="parameters"></a>Parametry  
 *pContext*  
 Określa typ widoku i dokumentu.  
  
 *nID*  
 Numer identyfikacyjny widoku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CWnd` obiektu, jeśli operacja się powiedzie; w przeciwnym razie wartość NULL.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji elementu członkowskiego do utworzenia "widoków", które nie są `CView`-pochodnych w ramce. Po wywołaniu `CreateView`, należy ręcznie ustawić widok na aktywny i ustawić, aby była widoczna; te zadania nie są automatycznie wykonywane przez `CreateView`.  
  
##  <a name="dockcontrolbar"></a>  CFrameWnd::DockControlBar  
 Powoduje, że pasek sterowania jest zadokowany do ramki okna.  
  
```  
void DockControlBar(
    CControlBar* pBar,  
    UINT nDockBarID = 0,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pBar*  
 Wskazuje pasek sterowania bez możliwości dokowania.  
  
 *nDockBarID*  
 Określa, które strony okna ramki, należy wziąć pod uwagę dokowania. Może być 0 lub jeden z następujących czynności:  
  
- Zadokuj AFX_IDW_DOCKBAR_TOP do górnej ramki okna.  
  
- Zadokuj AFX_IDW_DOCKBAR_BOTTOM do dolnej części okna ramki.  
  
- Zadokuj AFX_IDW_DOCKBAR_LEFT do lewej strony ramki okna.  
  
- Zadokuj AFX_IDW_DOCKBAR_RIGHT do prawej strony okna ramki.  
  
 Jeśli jest to 0, pasek sterowania może być zadokowane dowolnej stronie włączone dla dokowania w oknie ramki docelowej.  
  
 *lprect —*  
 Określa we współrzędnych ekranu, w którym będzie zadokowany pasek sterowania w nieklienckim obszarze okna ramki docelowej.  
  
### <a name="remarks"></a>Uwagi  
 Będzie zadokowany pasek sterowania do jednej strony okna ramki określony w wywołaniach do obu [CControlBar::EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking) i [CFrameWnd::EnableDocking](#enabledocking). Wybrana po stronie jest określana przez *nDockBarID*.  
  
##  <a name="enabledocking"></a>  CFrameWnd::EnableDocking  
 Wywołaj tę funkcję, aby umożliwić paski sterowania zadokowane w oknie ramowym.  
  
```  
void EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *dwDockStyle*  
 Określa, które strony okna ramki może służyć jako dokowanie witryn dla pasków sterowania. Może być co najmniej jeden z następujących czynności:  
  
- CBRS_ALIGN_TOP umożliwia dokowanie u góry obszaru klienta.  
  
- CBRS_ALIGN_BOTTOM umożliwia zadokowane w dolnej części obszaru klienta.  
  
- CBRS_ALIGN_LEFT umożliwia dokowanie po lewej stronie obszaru klienta.  
  
- CBRS_ALIGN_RIGHT umożliwia dokowanie po prawej stronie obszaru klienta.  
  
- CBRS_ALIGN_ANY umożliwia dokowanie na dowolnej stronie obszaru klienta.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie paski sterowania zostanie zadokowany po stronie okno ramowe w następującej kolejności: Góra, dół, lewo, prawo.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CToolBar::Create](../../mfc/reference/ctoolbar-class.md#create).  
  
##  <a name="endmodalstate"></a>  CFrameWnd::EndModalState  
 Wywołaj tę funkcję elementu członkowskiego zmiany okno ramowe ze modalne niemodalne.  
  
```  
virtual void EndModalState();
```  
  
### <a name="remarks"></a>Uwagi  
 `EndModalState` Umożliwia obsługę systemu windows, wyłączona przez [BeginModalState](#beginmodalstate).  
  
##  <a name="floatcontrolbar"></a>  CFrameWnd::FloatControlBar  
 Wywołaj tę funkcję, aby spowodować, że pasek sterowania nie jest zadokowany do ramki okna.  
  
```  
void FloatControlBar(
    CControlBar* pBar,  
    CPoint point,  
    DWORD dwStyle = CBRS_ALIGN_TOP);
```  
  
### <a name="parameters"></a>Parametry  
 *pBar*  
 Wskazuje na pasku sterowania, aby być przestawione.  
  
 *Punkt*  
 Lokalizacja, w współrzędne ekranu, gdzie zostaną umieszczone lewym górnym rogu paska sterowania.  
  
 *dwStyle*  
 Określa, czy wyrównywanie pasku sterowania w pionie i w jego nowe okno ramek. Może być dowolną z następujących czynności:  
  
- Po wybraniu opcji CBRS_ALIGN_TOP paska sterowania będzie miała orientację w pionie.  
  
- Po wybraniu opcji CBRS_ALIGN_BOTTOM paska sterowania będzie miała orientację w pionie.  
  
- Po wybraniu opcji CBRS_ALIGN_LEFT paska sterowania będzie miała orientację w poziomie.  
  
- Po wybraniu opcji CBRS_ALIGN_RIGHT paska sterowania będzie miała orientację w poziomie.  
  
 Jeśli style są przekazywane, określając orientacji pionowej i pionowy, pasek narzędzi będzie są rozmieszczane w poziomie.  
  
### <a name="remarks"></a>Uwagi  
 Zwykle jest to realizowane przy uruchamianiu aplikacji, gdy program jest przywrócenie ustawień z poprzedniego wykonania.  
  
 Ta funkcja jest wywoływana przez platformę, gdy użytkownik powoduje, że operacja przeciągania poprzez zwolnienie lewego przycisku myszy, przeciągając pasek sterowania za pośrednictwem lokalizacji, która nie jest dostępna dla dokowania.  
  
##  <a name="getactivedocument"></a>  CFrameWnd::GetActiveDocument  
 Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wskaźnik do bieżącego `CDocument` dołączony do bieżącego aktywnego widoku.  
  
```  
virtual CDocument* GetActiveDocument();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do bieżącego [CDocument](../../mfc/reference/cdocument-class.md). Zwraca wartość NULL, jeśli nie bieżącego dokumentu.  
  
##  <a name="getactiveframe"></a>  CFrameWnd::GetActiveFrame  
 Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wskaźnik do aktywnego okna interfejsu wielu dokumentów (MDI) podrzędne okna ramki MDI.  
  
```  
virtual CFrameWnd* GetActiveFrame();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do aktywnego okna podrzędnego MDI. Jeśli aplikacja jest aplikacją SDI lub okno ramek MDI nie ma żadnych dokumentów aktywnych niejawny **to** wskaźnik zostaną zwrócone.  
  
### <a name="remarks"></a>Uwagi  
 Czy nie active MDI child lub aplikacja jest interfejsu pojedynczego dokumentu (SDI) niejawny **to** wskaźnik jest zwracany.  
  
##  <a name="getactiveview"></a>  CFrameWnd::GetActiveView  
 Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wskaźnik do aktywnego widoku (jeśli istnieje), dołączony do okna ramki ( `CFrameWnd`).  
  
```  
CView* GetActiveView() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do bieżącego [CView](../../mfc/reference/cview-class.md). Jeśli nie ma bieżącego widoku, zwraca wartość NULL.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja zwraca wartość NULL, gdy zostanie wywołana dla okna głównej ramki MDI ( `CMDIFrameWnd`). W aplikacji MDI ramce głównej okna MDI nie ma skojarzonych z nim widoku. Zamiast tego każde okno podrzędne poszczególnych ( `CMDIChildWnd`) zawiera jeden lub więcej widoków skojarzonych. Aktywny widok w aplikacji MDI można uzyskać, najpierw wyszukując aktywne okno podrzędne MDI i znajdując aktywny widok dla tego okna podrzędnego. Przez wywołanie funkcji można znaleźć okno podrzędne MDI active `MDIGetActive` lub `GetActiveFrame` jak pokazano w następującym:  
  
 [!code-cpp[NVC_MFCWindowing#2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]  
  
##  <a name="getcontrolbar"></a>  CFrameWnd::GetControlBar  
 Wywołaj `GetControlBar` do uzyskania dostępu do pasek sterowania, który jest skojarzony z identyfikatorem.  
  
```  
CControlBar* GetControlBar(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *nID*  
 Numer identyfikacyjny paska sterowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do pasek sterowania, który jest skojarzony z identyfikatorem.  
  
### <a name="remarks"></a>Uwagi  
 *NID* parametr odnosi się do Unikatowy identyfikator, które są przekazywane do `Create` metoda paska sterowania. Więcej informacji na temat pasków sterowania, można znaleźć w temacie uprawnionych [paski sterowania](../../mfc/control-bars.md).  
  
 `GetControlBar` zwróci pasek sterowania, nawet jeśli jest liczb zmiennoprzecinkowych i dlatego nie jest obecnie ramki okna podrzędnego.  
  
##  <a name="getdockstate"></a>  CFrameWnd::GetDockState  
 Wywołaj tę funkcję elementu członkowskiego, do przechowywania informacji o stanie dotyczących okno ramowe pasków sterowania w `CDockState` obiektu.  
  
```  
void GetDockState(CDockState& state) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *state*  
 Zawiera bieżący stan paski sterowania oknem ramki po powrocie.  
  
### <a name="remarks"></a>Uwagi  
 Następnie można napisać zawartość `CDockState` do magazynu przy użyciu `CDockState::SaveState` lub `Serialize`. Jeśli chcesz później przywrócić paski sterowania do poprzedniego stanu, Załaduj stan z `CDockState::LoadState` lub `Serialize`, następnie wywołać `SetDockState` dotyczą pasków sterowania oknem ramki poprzedniego stanu.  
  
##  <a name="getmenubarstate"></a>  CFrameWnd::GetMenuBarState  
 Pobiera stan wyświetlania menu w bieżącej aplikacji MFC.  
  
```  
virtual DWORD GetMenuBarState();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwracana wartość może mieć następujące wartości:  
  
-   AFX_MBS_VISIBLE (0x01) — jest widoczny.  
  
-   AFX_MBS_HIDDEN (0x02) — menu jest ukryty.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wystąpi błąd czasu wykonywania, ta metoda potwierdzenia w trybie debugowania i zgłasza wyjątek pochodną [CException](../../mfc/reference/cexception-class.md) klasy.  
  
##  <a name="getmenubarvisibility"></a>  CFrameWnd::GetMenuBarVisibility  
 Wskazuje, czy domyślny stan z menu w bieżącej aplikacji MFC jest ukrytych lub widocznych.  
  
```  
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca jedną z następujących wartości:  
  
-   AFX_MBV_KEEPVISIBLE (0x01) — zostanie wyświetlone menu przez cały czas, a także domyślne nie ma fokusu.  
  
-   AFX_MBV_DISPLAYONFOCUS (0x02) — menu jest domyślnie ukryty. Jeśli menu jest ukryty, naciśnij klawisz ALT, aby wyświetlić menu, a następnie uzyskuje fokus. Jeśli zostanie wyświetlone menu, naciśnij klawisz ALT lub klawisz ESC, aby je ukryć.  
  
-   DISPLAYONFOCUS AFX_MBV_ (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04) (bitowe połączenie (lub)) — menu jest domyślnie ukryty. Jeśli menu jest ukryty, naciśnij klawisz F10, aby wyświetlić menu, a następnie uzyskuje fokus. Jeśli zostanie wyświetlone menu, naciśnij klawisz F10, aby przełączać fokus lub Wyłącz menu. Zostanie wyświetlone menu, naciśnij klawisz ALT lub klawisz ESC, aby je ukryć.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wystąpi błąd czasu wykonywania, ta metoda potwierdzenia w trybie debugowania i zgłasza wyjątek pochodną [CException](../../mfc/reference/cexception-class.md) klasy.  
  
##  <a name="getmessagebar"></a>  CFrameWnd::GetMessageBar  
 Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wskaźnik do paska stanu.  
  
```  
virtual CWnd* GetMessageBar();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do paska stanu okna.  
  
##  <a name="getmessagestring"></a>  CFrameWnd::GetMessageString  
 Należy przesłonić tę funkcję, aby zapewnić — niestandardowe ciągi dla identyfikatorów poleceń.  
  
```  
virtual void GetMessageString(
    UINT nID,  
    CString& rMessage) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nID*  
 Identyfikator zasobu wymaganego komunikatu.  
  
 *rMessage*  
 `CString` obiekt, w którym należy umieścić komunikat.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja po prostu ładuje ciągu określonego przez *nID* z pliku zasobów. Ta funkcja jest wywoływana przez platformę, gdy ciąg wiadomości w pasku stanu wymaga aktualizacji.  
  
##  <a name="gettitle"></a>  CFrameWnd::GetTitle  
 Pobiera tytuł obiekt okna.  
  
```  
CString GetTitle() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiekt zawierający tytuł bieżący obiekt okna.  
  
##  <a name="initialupdateframe"></a>  CFrameWnd::InitialUpdateFrame  
 Wywołaj `IntitialUpdateFrame` po utworzeniu nowej ramki za pomocą `Create`.  
  
```  
void InitialUpdateFrame(
    CDocument* pDoc,  
    BOOL bMakeVisible);
```  
  
### <a name="parameters"></a>Parametry  
 *pDoc*  
 Wskazuje dokument, z którym jest skojarzony ramki okna. Może mieć wartości NULL.  
  
 *bMakeVisible*  
 W przypadku opcji TRUE wskazuje, że ramki powinien stają się widoczne i aktywne. W przypadku wartości FAŁSZ, są widoczne nie elementy podrzędne.  
  
### <a name="remarks"></a>Uwagi  
 Powoduje to, że wszystkie widoki w tym oknie ramki, aby otrzymać ich `OnInitialUpdate` wywołania.  
  
 Ponadto jeśli istnieje nie był wcześniej aktywnego widoku, widok głównej ramki okna jest uaktywniona. Podstawowy widok jest widokiem, za pomocą elementu podrzędnego ID AFX_IDW_PANE_FIRST. Na koniec okno ramowe stają się widoczne dla Jeśli *bMakeVisible* jest różna od zera. Jeśli *bMakeVisible* wynosi 0, bieżący fokus i widoczności ramki okna pozostaną niezmienione. Nie jest to konieczne wywołać tę funkcję, korzystając z ramowych implementacji nowy plik i Otwórz plik.  
  
##  <a name="inmodalstate"></a>  CFrameWnd::InModalState  
 Wywołaj tę funkcję elementu członkowskiego, aby sprawdzić, czy okno ramowe modalnym lub niemodalnym.  
  
```  
BOOL InModalState() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli tak, ale w przeciwnym razie 0.  
  
##  <a name="istracking"></a>  CFrameWnd::IsTracking  
 Wywołaj tę funkcję elementu członkowskiego, aby określić, jeśli obecnie Trwa przenoszenie pasek podziału w oknie.  
  
```  
BOOL IsTracking() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli operacja rozdzielacz jest w toku; w przeciwnym razie 0.  
  
##  <a name="loadacceltable"></a>  CFrameWnd::LoadAccelTable  
 Wywołać można załadować tabeli określonym akceleratorze.  
  
```  
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszResourceName*  
 Określa nazwę zasobu akceleratora. Użyj MAKEINTRESOURCE, jeśli zasób jest identyfikowany za pomocą liczby całkowitej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli został pomyślnie załadowany na tabeli akceleratora; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Tylko jedna tabela może zostać załadowany w danym momencie.  
  
 Tabele akceleratora ładowanych z zasobów są zwalniane automatycznie po zakończeniu działania aplikacji.  
  
 Jeśli wywołasz `LoadFrame` można utworzyć okna ramki, struktura ładuje tabeli klawiszy skrótu wraz z menu i ikony zasobów, a kolejne wywołanie tej funkcji elementu członkowskiego jest niepotrzebne.  
  
##  <a name="loadbarstate"></a>  CFrameWnd::LoadBarState  
 Wywołaj tę funkcję, aby przywrócić ustawienia każdego paska sterowania należące do ramki okna.  
  
```  
void LoadBarState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszProfileName*  
 Nazwa sekcji w pliku inicjującym (INI) lub klucza w rejestrze Windows, w którym są przechowywane informacje o stanie.  
  
### <a name="remarks"></a>Uwagi  
 Przywrócono informacje dotyczące widoczności, orientacji pionowej/poziomej, stan dokowania i położenie paska sterowania.  
  
 Chcesz przywrócić ustawienia musi być napisana w rejestrze, przed wywołaniem `LoadBarState`. Wpisywanie informacji do rejestru, wywołując [CWinApp::SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey). Zapisywanie informacji o pliku INI, wywołując [SaveBarState](#savebarstate).  
  
##  <a name="loadframe"></a>  CFrameWnd::LoadFrame  
 Wywołanie dynamicznego tworzenia okno ramowe z informacji o zasobie.  
  
```  
virtual BOOL LoadFrame(
    UINT nIDResource,  
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,  
    CWnd* pParentWnd = NULL,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *nIDResource*  
 Identyfikator skojarzony z oknem ramki zasobów udostępnionych.  
  
 *dwDefaultStyle*  
 Ramki [styl](../../mfc/reference/styles-used-by-mfc.md#window-styles). Obejmują styl FWS_ADDTOTITLE, jeśli chcesz, aby pasek tytułu, aby automatycznie wyświetlać nazwy dokumentu, reprezentowany w oknie.  
  
 *pParentWnd*  
 Wskaźnik do ramki nadrzędnej.  
  
 *pContext*  
 Wskaźnik do [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) struktury. Ten parametr może mieć wartości NULL.  
  
### <a name="remarks"></a>Uwagi  
 Konstruowania `CFrameWnd` obiektu w dwóch krokach. Po pierwsze wywołanie konstruktora, który tworzy `CFrameWnd` obiektu, a następnie wywołaj `LoadFrame`, który ładuje Windows ramki okna i skojarzonych zasobów i dołącza okna ramki `CFrameWnd` obiektu. *NIDResource* parametr określa menu, w tabeli akceleratora, ikona i zasobu ciągu tytułu okna ramki.  
  
 Użyj `Create` funkcja elementu członkowskiego zamiast `LoadFrame` gdy zachodzi potrzeba określenia wszystkich parametrów tworzenia okna ramki.  
  
 Struktura wywołuje `LoadFrame` podczas tworzenia ramki okna przy użyciu obiektu szablonu dokumentu.  
  
 Środowisko wykorzystuje *pContext* argumentu, aby określić obiekty do podłączenia do ramki okna wraz ze wszystkimi zawarte obiekty widoku. Możesz ustawić *pContext* argumentu o wartości NULL podczas wywoływania `LoadFrame`.  
  
##  <a name="m_bautomenuenable"></a>  CFrameWnd::m_bAutoMenuEnable  
 Gdy ten element członkowski danych jest włączone (czyli wartość domyślna), elementy menu, które nie mają obsługi ON_UPDATE_COMMAND_UI lub ON_COMMAND zostanie automatycznie wyłączone po użytkownik ściąga menu.  
  
```  
BOOL m_bAutoMenuEnable;  
```  
  
### <a name="remarks"></a>Uwagi  
 Elementy menu, które mają program obsługi ON_COMMAND, ale żadna procedura obsługi ON_UPDATE_COMMAND_UI zostaną automatycznie włączone.  
  
 Jeśli ten element członkowski danych jest ustawiony, elementy menu są automatycznie włączane w taki sam sposób, że przyciski paska narzędzi są włączone.  
  
> [!NOTE]
> `m_bAutoMenuEnable` nie ma wpływu na elementach menu najwyższego poziomu.  
  
 Ten element członkowski danych ułatwia implementację opcjonalne polecenia na podstawie bieżącego zaznaczenia i ogranicza konieczność pisania procedur obsługi ON_UPDATE_COMMAND_UI włączania i wyłączania elementów menu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]  
  
##  <a name="negotiateborderspace"></a>  CFrameWnd::NegotiateBorderSpace  
 Wywołaj tę funkcję elementu członkowskiego do negocjowania obramowania miejsce w oknie ramowym podczas aktywacji inplace OLE.  
  
```  
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,  
    LPRECT lpRectBorder);
```  
  
### <a name="parameters"></a>Parametry  
 *nBorderCmd*  
 Zawiera jedną z następujących wartości z `enum BorderCmd`:  
  
- `borderGet` = 1  
  
- `borderRequest` = 2  
  
- `borderSet` = 3  
  
 *lpRectBorder*  
 Wskaźnik do [Prostokąt](../../mfc/reference/rect-structure1.md) struktury lub [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu, który określa współrzędne obramowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska jest `CFrameWnd` implementacji negocjacji miejsca obramowania OLE.  
  
##  <a name="onbarcheck"></a>  CFrameWnd::OnBarCheck  
 Wywoływana zawsze wtedy, gdy akcja jest wykonywana na pasku określoną kontrolkę.  
  
```  
afx_msg BOOL OnBarCheck(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *nID*  
 Identyfikator formantu paska są wyświetlane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli istniały paska sterowania; w przeciwnym razie 0.  
  
##  <a name="oncontexthelp"></a>  CFrameWnd::OnContextHelp  
 Obsługuje SHIFT + F1 Pomoc dla elementów w miejscu.  
  
```  
afx_msg void OnContextHelp();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby włączyć pomocy kontekstowej, należy dodać  
  
 [!code-cpp[NVC_MFCDocViewSDI#16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]  
  
 instrukcję, aby Twoje `CFrameWnd` klasy mapy wiadomości, a także dodawanie wpisu tabeli akceleratora, zwykle SHIFT + F1, aby włączyć tę funkcję elementu członkowskiego.  
  
 Jeśli aplikacja jest OLE kontenerem, `OnContextHelp` umieszcza wszystkie elementy w miejscu zawartych w obiekt okna ramki w trybie pomocy. Kursor zmieni się strzałka i znak zapytania, a użytkownik może następnie przesuń wskaźnik myszy i naciśnij przycisk myszy po lewej stronie, aby wybrać okno dialogowe, okna, menu lub przycisku polecenia. Ta funkcja elementu członkowskiego wywołuje funkcję Windows `WinHelp` w kontekście pomocy obiektu pod kursorem.  
  
##  <a name="oncreateclient"></a>  CFrameWnd::OnCreateClient  
 Wywoływane przez platformę podczas wykonywania `OnCreate`.  
  
```  
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,  
    CCreateContext* pContext);
```  
  
### <a name="parameters"></a>Parametry  
 *LPC*  
 Wskaźnik do Windows [CREATESTRUCT](../../mfc/reference/createstruct-structure.md) struktury.  
  
 *pContext*  
 Wskaźnik do [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Nigdy nie wywołują metody tej funkcji.  
  
 Domyślna implementacja tej funkcji tworzy `CView` obiektu na podstawie informacji podanych w *pContext*, jeśli to możliwe.  
  
 Przesłonić tę funkcję, aby zastąpić wartości przekazane w `CCreateContext` obiektu lub zmienić sposób kontrolkach obszaru klienckiego głównego okna ramki są tworzone. `CCreateContext` Można zastąpić elementów członkowskich są opisane w [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) klasy.  
  
> [!NOTE]
>  Nie zastępuj wartości przekazane w `CREATESTRUCT` struktury. Są one tylko w celach informacyjnych. Jeśli chcesz przesłonić prostokąt początkowego okna, na przykład, zastąpić `CWnd` funkcja elementu członkowskiego [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).  
  
##  <a name="onhidemenubar"></a>  CFrameWnd::OnHideMenuBar  
 Ta funkcja jest wywoływana, gdy system jest ukryta na pasku menu w bieżącej aplikacji MFC.  
  
```  
virtual void OnHideMenuBar();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta procedura obsługi zdarzeń włącza aplikację, aby wykonywać akcje niestandardowe w przypadku, gdy system jest ukryta w menu. Nie można zapobiec ukrywane przez menu, ale można na przykład wywołać innych metod do pobrania stylu menu lub stanu.  
  
##  <a name="onsetpreviewmode"></a>  CFrameWnd::OnSetPreviewMode  
 Wywołaj tę funkcję elementu członkowskiego, aby ustawić aplikacji głównej ramki okna w i poza trybem Podgląd wydruku.  
  
```  
virtual void OnSetPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>Parametry  
 *bPreview*  
 Określa, czy należy umieścić aplikację w trybie podglądu wydruku. Należy ustawić wartość TRUE, aby umieścić w podglądzie wydruku, wartość FALSE, aby anulować tryb podglądu.  
  
 *stanu wydajności*  
 Wskaźnik do `CPrintPreviewState` struktury.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja powoduje wyłączenie wszystkich standardowych pasków narzędzi i ukrywa menu głównego i okno główne klienta. To jest przekształcany MDI okna ramowe tymczasowe SDI ramki okna.  
  
 Zastąpienie tej funkcji elementu członkowskiego, aby dostosować wyświetlanie i ukrywanie paskami sterowania i innymi częściami okna ramki podczas generowania podglądu wydruku. Wywołania implementacji klasy podstawowej z w terminie zgodnym z przesłoniętą wersji.  
  
##  <a name="onshowmenubar"></a>  CFrameWnd::OnShowMenuBar  
 Ta funkcja jest wywoływana, gdy system jest wyświetli pasek menu w bieżącej aplikacji MFC.  
  
```  
virtual void OnShowMenuBar();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta procedura obsługi zdarzeń umożliwia aplikacji do wykonania akcji niestandardowych, gdy menu ma być wyświetlany. Nie można zapobiec wyświetlaniu przez menu, ale na przykład, wywołując innych metod do pobrania stylu menu lub stanu.  
  
##  <a name="onupdatecontrolbarmenu"></a>  CFrameWnd::OnUpdateControlBarMenu  
 Wywoływane przez platformę, po zaktualizowaniu skojarzonego menu.  
  
```  
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parametry  
 *pCmdUI*  
 Wskaźnik do [CCmdUI](../../mfc/reference/ccmdui-class.md) obiekt reprezentujący menu, który wygenerował polecenia update. Wywołuje program obsługi aktualizacji [Włącz](../../mfc/reference/ccmdui-class.md#enable) funkcji składowej typu `CCmdUI` obiektu za pomocą *pCmdUI* można zaktualizować interfejsu użytkownika.  
  
##  <a name="recalclayout"></a>  CFrameWnd::RecalcLayout  
 Wywoływane przez platformę, gdy standardowe paski kontrolki są włączane lub wyłączane lub gdy zmieniany jest rozmiar ramki okna.  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bNotify*  
 Określa, czy aktywny element w miejscu dla ramki okna odbiera powiadomienie o zmianie układu. W przypadku opcji TRUE element jest powiadamiany o; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja tej funkcji elementu członkowskiego wywołuje `CWnd` funkcja elementu członkowskiego `RepositionBars` służące do zmiany położenia wszystkich pasków sterowania w ramce, a także okna głównego klienta (zazwyczaj `CView` lub MDICLIENT).  
  
 Zastąpienie tej funkcji elementu członkowskiego, aby kontrolować wygląd i zachowanie pasków sterowania po zmianie układ okna ramki. Na przykład wywołać ją włączyć paski sterowania lub wyłączyć lub dodać inny paska sterowania.  
  
##  <a name="rectdefault"></a>  CFrameWnd::rectDefault  
 Przekazać ten statyczny `CRect` jako parametr podczas tworzenia okna, aby zezwolić na Windows wybrać początkowy rozmiar i położenie okna.  
  
```  
static AFX_DATA const CRect rectDefault;  
```  
  
##  <a name="savebarstate"></a>  CFrameWnd::SaveBarState  
 Wywołaj tę funkcję do przechowywania informacji na temat każdego paska sterowania należące do ramki okna.  
  
```  
void SaveBarState(LPCTSTR lpszProfileName) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lpszProfileName*  
 Nazwa sekcji w pliku inicjującym lub klucza w rejestrze Windows, w którym są przechowywane informacje o stanie.  
  
### <a name="remarks"></a>Uwagi  
 Te informacje mogą być odczytywane z plików inicjowanie przy użyciu [LoadBarState](#loadbarstate). Przechowywane informacje dotyczące widoczności, poziomo i pionowo orientacji dokowania, stan i położenie paska sterowania.  
  
##  <a name="setactivepreviewview"></a>  CFrameWnd::SetActivePreviewView  
 Wskazuje określony widok jako widok aktywny podglądu sformatowanego.  
  
```  
void SetActivePreviewView(CView* pViewNew);
```  
  
### <a name="parameters"></a>Parametry  
 *pViewNew*  
 Wskaźnik do widoku, aby aktywować.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setactiveview"></a>  CFrameWnd::SetActiveView  
 Wywołaj tę funkcję elementu członkowskiego, aby ustawić aktywny widok.  
  
```  
void SetActiveView(
    CView* pViewNew,  
    BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *pViewNew*  
 Określa wskaźnik [CView](../../mfc/reference/cview-class.md) obiekt lub wartość NULL w przypadku aktywnego widoku.  
  
 *bNotify*  
 Określa, czy widok ma być powiadamiany o aktywacji. W przypadku opcji TRUE `OnActivateView` nosi nazwę nowego widoku; Jeśli "false", nie jest.  
  
### <a name="remarks"></a>Uwagi  
 Struktura zostanie automatycznie Wywołaj tę funkcję, gdy użytkownik będzie zmieniał fokus do widoku w obrębie ramki okna. Można jawnie wywołać `SetActiveView` można zmienić fokus na określonym widoku.  
  
##  <a name="setdockstate"></a>  CFrameWnd::SetDockState  
 Wywołaj tę funkcję elementu członkowskiego, aby zastosować informacje o stanie przechowywanych w `CDockState` obiekt do pasków sterowania oknem ramki.  
  
```  
void SetDockState(const CDockState& state);
```  
  
### <a name="parameters"></a>Parametry  
 *state*  
 Mają zastosowanie przechowywany stan do pasków sterowania oknem ramki.  
  
### <a name="remarks"></a>Uwagi  
 Aby przywrócić poprzedni stan pasków sterowania, można załadować przechowywanego stanu za pomocą `CDockState::LoadState` lub `Serialize`, następnie za pomocą `SetDockState` stosować je do pasków sterowania oknem ramki. Poprzedni stan jest przechowywany w `CDockState` obiekt z `GetDockState`  
  
##  <a name="setmenubarstate"></a>  CFrameWnd::SetMenuBarState  
 Ustawia stan wyświetlania menu w bieżącej aplikacji MFC w ukrytych lub wyświetlone.  
  
```  
virtual BOOL SetMenuBarState(DWORD nState);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] *nInformacje*|Określa, czy chcesz wyświetlić lub ukryć menu. *NInformacje* parametr może mieć następujące wartości:<br /><br /> -AFX_MBS_VISIBLE (0x01) - Wyświetla menu, jeśli jest ukryty, ale nie obowiązuje, jeśli jest on widoczny.<br />-AFX_MBS_HIDDEN (0x02) - powoduje ukrycie opcji menu, jeśli jest widoczny, ale nie obowiązuje, jeśli jest on ukryty.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli ta metoda pomyślnie zmieni stan menu; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wystąpi błąd czasu wykonywania, ta metoda potwierdzenia w trybie debugowania i zgłasza wyjątek pochodną [CException](../../mfc/reference/cexception-class.md) klasy.  
  
##  <a name="setmenubarvisibility"></a>  CFrameWnd::SetMenuBarVisibility  
 Ustawia domyślne zachowanie menu w bieżącej aplikacji MFC w ukrytych lub widocznych.  
  
```  
virtual void SetMenuBarVisibility(DWORD nStyle);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] *nStyle*|Określa, czy menu jest domyślnie ukryta, lub jest widoczna i ma fokus. *NStyle* parametr może mieć następujące wartości:<br /><br /> -AFX_MBV_KEEPVISIBLE (0X01) —<br />     W menu wyświetlanym przez cały czas i domyślnie nie ma fokusu.<br />-AFX_MBV_DISPLAYONFOCUS (0X02) —<br />     Menu jest domyślnie ukryty. Jeśli menu jest ukryty, naciśnij klawisz ALT, aby wyświetlić menu, a następnie uzyskuje fokus. Jeśli zostanie wyświetlone menu, naciśnij klawisz ALT lub klawisz ESC, aby ukryć menu.<br />-AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04)<br />     (bitowe połączenie (lub)) — menu jest domyślnie ukryty. Jeśli menu jest ukryty, naciśnij klawisz F10, aby wyświetlić menu, a następnie uzyskuje fokus. Jeśli zostanie wyświetlone menu, naciśnij klawisz F10, aby przełączać fokus lub Wyłącz menu. Zostanie wyświetlone menu, naciśnij klawisz ALT lub klawisz ESC, aby je ukryć.|  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wartość *nStyle* parametr jest nieprawidłowy, ta metoda potwierdzenia w trybie debugowania i zgłasza [CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md) w trybie wydania. W przypadku innych błędów środowiska uruchomieniowego, ta metoda potwierdzenia w trybie debugowania i zgłasza wyjątek pochodzi od [CException](../../mfc/reference/cexception-class.md) klasy.  
  
 Ta metoda ma wpływ na stan menu w aplikacji napisanych dla [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] i nowszych.  
  
##  <a name="setmessagetext"></a>  CFrameWnd::SetMessageText  
 Wywołaj tę funkcję, aby umieścić ciąg w okienku paska stanu, który ma identyfikator równy 0.  
  
```  
void SetMessageText(LPCTSTR lpszText);  
void SetMessageText(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszText*  
 Wskazuje ciąg na pasku stanu.  
  
 *nID*  
 Identyfikator ciągu zasobu ciągu do umieszczenia na pasku stanu.  
  
### <a name="remarks"></a>Uwagi  
 Jest to zazwyczaj skrajnie po lewej stronie i najdłuższy, w okienku paska stanu.  
  
##  <a name="setprogressbarposition"></a>  CFrameWnd::SetProgressBarPosition  
 Ustawia bieżącej pozycji, aż pasek postępu Windows 7, które są wyświetlane na pasku zadań.  
  
```  
void SetProgressBarPosition(int nProgressPos);
```  
  
### <a name="parameters"></a>Parametry  
 *nProgressPos*  
 Określa położenie do ustawienia. Musi być z zakresu ustawione przez `SetProgressBarRange`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setprogressbarrange"></a>  CFrameWnd::SetProgressBarRange  
 Określa zakres dla paska postępu Windows 7, które są wyświetlane na pasku zadań.  
  
```  
void SetProgressBarRange(
    int nRangeMin,  
    int nRangeMax);
```  
  
### <a name="parameters"></a>Parametry  
 *nRangeMin*  
 Minimalnej wartości.  
  
 *nRangeMax*  
 Wartość maksymalna.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setprogressbarstate"></a>  CFrameWnd::SetProgressBarState  
 Ustawia typ i stan wskaźnik postępu, wyświetlany na przycisku na pasku zadań.  
  
```  
void SetProgressBarState(TBPFLAG tbpFlags);
```  
  
### <a name="parameters"></a>Parametry  
 *tbpFlags*  
 Flagi sterujące bieżący stan przycisku postępu. Określ tylko jedną z następujących flag, ponieważ wszystkie stany wykluczają się wzajemnie: TBPF_NOPROGRESS TBPF_INDETERMINATE, TBPF_NORMAL, TBPF_ERROR, TBPF_PAUSED.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="settaskbaroverlayicon"></a>  CFrameWnd::SetTaskbarOverlayIcon  
 Przeciążone. Dotyczy nakładki przycisk na pasku zadań do wskazania stanu aplikacji lub do powiadamiania użytkownika.  
  
```  
BOOL SetTaskbarOverlayIcon(
    UINT nIDResource,  
    LPCTSTR lpcszDescr);

 
BOOL SetTaskbarOverlayIcon(
    HICON hIcon,  
    LPCTSTR lpcszDescr);
```  
  
### <a name="parameters"></a>Parametry  
 *nIDResource*  
 Określa identyfikator zasobu ikony do użycia jako nakładki. Zobacz opis *hIcon* Aby uzyskać szczegółowe informacje.  
  
 *lpcszDescr*  
 Wskaźnik do ciągu, który zawiera tekst alternatywny wersję informacji przekazywanych przez nakładki, na potrzeby ułatwień dostępu.  
  
 *hIcon*  
 Uchwyt ikony do użycia jako nakładki. Powinna to być mała ikona pomiaru 16 x 16 pikseli przy 96 punktów na cal (dpi). Jeśli ikony nakładki jest już stosowany do przycisku na pasku zadań, jest zastępowany danej istniejących nakładki. Ta wartość może mieć wartości NULL. Sposób obsługi wartości NULL, zależy od tego, czy przycisk na pasku zadań reprezentuje jednego okna lub grupy systemu windows. Jest odpowiedzialny za aplikacji wywołującej, aby zwolnić *hIcon* gdy jest już potrzebny.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli to się powiedzie; Wartość FALSE, jeśli wersja systemu operacyjnego jest niższa niż Windows 7, lub jeśli wystąpi błąd, ustawienie ikony.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="settitle"></a>  CFrameWnd::SetTitle  
 Ustawia tytuł obiekt okna.  
  
```  
void SetTitle(LPCTSTR lpszTitle);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszTitle*  
 Wskaźnik na ciąg znaków zawierający tytuł obiekt okna.  
  
##  <a name="showcontrolbar"></a>  CFrameWnd::ShowControlBar  
 Wywołaj tę funkcję elementu członkowskiego, aby pokazać lub ukryć pasek sterowania.  
  
```  
void ShowControlBar(
    CControlBar* pBar,  
    BOOL bShow,  
    BOOL bDelay);
```  
  
### <a name="parameters"></a>Parametry  
 *pBar*  
 Wskaźnik na pasek sterowania, które mają być wyświetlane lub ukryte.  
  
 *bShow*  
 W przypadku opcji TRUE Określa, czy ma być wyświetlana na pasku sterowania. W przypadku wartości FAŁSZ określa pasek sterowania zostanie ukryte.  
  
 *bDelay*  
 W przypadku opcji TRUE, opóźnienie, wyświetlanie paska sterowania. W przypadku wartości FAŁSZ Pokaż kontrolki paska natychmiast.  
  
##  <a name="showownedwindows"></a>  CFrameWnd::ShowOwnedWindows  
 Wywołaj tę funkcję elementu członkowskiego, aby pokazać wszystkie systemy windows, które są elementami podrzędnymi `CFrameWnd` obiektu.  
  
```  
void ShowOwnedWindows(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 *bShow*  
 Określa, czy należących do systemu windows mają zostać pokazane lub ukryte.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Cmdiframewnd — klasa](../../mfc/reference/cmdiframewnd-class.md)   
 [Cmdichildwnd — klasa](../../mfc/reference/cmdichildwnd-class.md)   
 [Cview — klasa](../../mfc/reference/cview-class.md)   
 [Cdoctemplate — klasa](../../mfc/reference/cdoctemplate-class.md)   
 [Struktura CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)
