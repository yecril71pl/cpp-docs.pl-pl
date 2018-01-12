---
title: "Cframewnd — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5c27f27b8369aeb5fdb15d37dc196556a5f508d9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cframewnd-class"></a>Cframewnd — klasa
Udostępnia funkcje systemu Windows interfejs pojedynczego dokumentu (SDI) nakłada lub wyskakujących ramkę okna, wraz z elementów członkowskich do zarządzania okna.  
  
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
|[CFrameWnd::BeginModalState](#beginmodalstate)|Ustawia modalne okno ramowe.|  
|[CFrameWnd::Create](#create)|Wywołanie Utwórz i zainicjuj okno ramowe systemu Windows, skojarzone z `CFrameWnd` obiektu.|  
|[CFrameWnd::CreateView](#createview)|Tworzy widok w ramce, który nie pochodzi od `CView`.|  
|[CFrameWnd::DockControlBar](#dockcontrolbar)|Stacje dokujące pasek sterowania.|  
|[CFrameWnd::EnableDocking](#enabledocking)|Umożliwia pasek sterowania możliwości dokowania.|  
|[CFrameWnd::EndModalState](#endmodalstate)|Kończy się stan modalne okno ramowe. Włącza wszystkie okna wyłączone przez `BeginModalState`.|  
|[CFrameWnd::FloatControlBar](#floatcontrolbar)|Wyświetlany pasek sterowania.|  
|[CFrameWnd::GetActiveDocument](#getactivedocument)|Zwraca aktywne **CDocument** obiektu.|  
|[CFrameWnd::GetActiveFrame](#getactiveframe)|Zwraca aktywne `CFrameWnd` obiektu.|  
|[CFrameWnd::GetActiveView](#getactiveview)|Zwraca aktywne `CView` obiektu.|  
|[CFrameWnd::GetControlBar](#getcontrolbar)|Pobiera pasek sterowania.|  
|[CFrameWnd::GetDockState](#getdockstate)|Pobiera stan dokowania ramki okna.|  
|[CFrameWnd::GetMenuBarState](#getmenubarstate)|Pobiera stan wyświetlania menu w bieżącej aplikacji MFC.|  
|[CFrameWnd::GetMenuBarVisibility](#getmenubarvisibility)|Wskazuje, czy domyślne zachowanie menu w bieżącej aplikacji MFC jest ukryty lub widoczne.|  
|[CFrameWnd::GetMessageBar](#getmessagebar)|Zwraca wskaźnik do stanu paska należących do ramki okna.|  
|[CFrameWnd::GetMessageString](#getmessagestring)|Pobiera wiadomość odpowiadający identyfikator polecenia.|  
|[CFrameWnd::GetTitle](#gettitle)|Pobiera tytuł pasek sterowania pokrewne.|  
|[CFrameWnd::InitialUpdateFrame](#initialupdateframe)|Powoduje, że `OnInitialUpdate` funkcji członkowskiej należących do wszystkich widoków ramkę okna do wywołania.|  
|[CFrameWnd::InModalState](#inmodalstate)|Zwraca wartość wskazującą, czy okno ramowe jest w stanie modalne.|  
|[CFrameWnd::IsTracking](#istracking)|Określa, czy pasek podziału obecnie jest przenoszony.|  
|[CFrameWnd::LoadAccelTable](#loadacceltable)|Wywołanie można załadować tabeli akceleratora.|  
|[CFrameWnd::LoadBarState](#loadbarstate)|Wywołanie w celu przywrócenia ustawień pasek sterowania.|  
|[CFrameWnd::LoadFrame](#loadframe)|Wywołanie dynamicznie utworzyć okno ramowe z informacjami o zasobach.|  
|[CFrameWnd::NegotiateBorderSpace](#negotiateborderspace)|Negocjuje miejsca obramowania ramki okna.|  
|[CFrameWnd::OnBarCheck](#onbarcheck)|Wywoływana, gdy akcja jest wykonywana na pasku określonego formantu.|  
|[CFrameWnd::OnContextHelp](#oncontexthelp)|Obsługuje SHIFT + F1 Pomoc dla elementów w miejscu.|  
|[CFrameWnd::OnSetPreviewMode](#onsetpreviewmode)|Ustawia aplikacji główną ramkę okna w i poza trybem Podgląd wydruku.|  
|[CFrameWnd::OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|Wywoływane przez platformę po zaktualizowaniu skojarzonego menu.|  
|[CFrameWnd::RecalcLayout](#recalclayout)|Zmienia położenie pasków sterowania `CFrameWnd` obiektu.|  
|[CFrameWnd::SaveBarState](#savebarstate)|Wywołanie, aby zapisać ustawienia pasek sterowania.|  
|[CFrameWnd::SetActivePreviewView](#setactivepreviewview)|Wskazuje określony widok jako aktywny widok podglądu rozbudowanego.|  
|[CFrameWnd::SetActiveView](#setactiveview)|Ustawia aktywne `CView` obiektu.|  
|[CFrameWnd::SetDockState](#setdockstate)|Wywołanie dock okno ramowe w oknie głównym.|  
|[CFrameWnd::SetMenuBarState](#setmenubarstate)|Ustawia stan wyświetlania menu w bieżącej aplikacji MFC ukryte lub wyświetlane.|  
|[CFrameWnd::SetMenuBarVisibility](#setmenubarvisibility)|Ustawia domyślne zachowanie menu w bieżącej aplikacji MFC w ukrytym lub widoczne.|  
|[CFrameWnd::SetMessageText](#setmessagetext)|Ustawia tekst paska stanu standardowa.|  
|[CFrameWnd::SetProgressBarPosition](#setprogressbarposition)|Ustawia bieżące położenie paska postępu Windows 7 wyświetlane na pasku zadań.|  
|[CFrameWnd::SetProgressBarRange](#setprogressbarrange)|Ustawia zakresu dla systemu Windows 7 pasek postępu wyświetlany na pasku zadań.|  
|[CFrameWnd::SetProgressBarState](#setprogressbarstate)|Ustawia typ i stan wskaźnika postępu wyświetlany na przycisku paska zadań.|  
|[CFrameWnd::SetTaskbarOverlayIcon](#settaskbaroverlayicon)|Przeciążone. Dotyczy nakładki przycisk paska zadań w celu wskazania stanu aplikacji lub powiadomienie do użytkownika.|  
|[CFrameWnd::SetTitle](#settitle)|Ustawia tytuł pasek sterowania pokrewne.|  
|[CFrameWnd::ShowControlBar](#showcontrolbar)|Wywołanie Pokaż pasek sterowania.|  
|[CFrameWnd::ShowOwnedWindows](#showownedwindows)|Przedstawia wszystkie okna, które są elementami podrzędnymi `CFrameWnd` obiektu.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFrameWnd::OnCreateClient](#oncreateclient)|Tworzy okno klienckie ramki.|  
|[CFrameWnd::OnHideMenuBar](#onhidemenubar)|Metoda wywoływana przed menu w bieżącej aplikacji MFC jest ukryty.|  
|[CFrameWnd::OnShowMenuBar](#onshowmenubar)|Metoda wywoływana przed wyświetleniem menu w bieżącej aplikacji MFC.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFrameWnd::m_bAutoMenuEnable](#m_bautomenuenable)|Formanty automatyczne włączanie i wyłączanie funkcji dla elementów menu.|  
|[CFrameWnd::rectDefault](#rectdefault)|Przekazany statycznych `CRect` jako parametru podczas tworzenia `CFrameWnd` obiekt, aby umożliwić w systemie Windows wybierz początkowy rozmiar i położenie okna.|  
  
## <a name="remarks"></a>Uwagi  
 Aby utworzyć okno ramowe przydatne dla aplikacji, pochodzi z klasy `CFrameWnd`. Zmienne Członkowskie dodawać do klasy pochodnej w celu przechowywania danych specyficzne dla aplikacji. Funkcje Członkowskie Implementowanie obsługi wiadomości i wiadomości są mapowane w klasie pochodnej, aby określić, co się dzieje, gdy wiadomości są kierowane do okna.  
  
 Istnieją trzy sposoby tworzenia okno ramowe:  
  
-   Bezpośrednio utworzyć za pomocą [Utwórz](#create).  
  
-   Bezpośrednio utworzyć za pomocą [LoadFrame](#loadframe).  
  
-   Pośrednio utworzenia go za pomocą szablonu dokumentu.  
  
 Przed wywołaniem albo **Utwórz** lub `LoadFrame`, należy tworzyć obiektu okno ramowe na stercie przy użyciu języka C++ **nowe** operatora. Przed wywołaniem **Utwórz**, można również zarejestrować klasy okna z [AfxRegisterWndClass](../../mfc/reference/application-information-and-management.md#afxregisterwndclass) funkcji globalnej do ustawiania ikony, jak i klasy stylów ramki.  
  
 Użyj **Utwórz** funkcji członkowskiej do przekazania parametrów tworzenia ramki natychmiastowego jako argumenty.  
  
 `LoadFrame`wymaga mniejszej liczby argumentów niż **Utwórz**, a zamiast tego pobiera większość jego wartości domyślnej z zasobów, w tym ramki podpis, ikona tabeli akceleratora i menu. Aby mieć dostęp `LoadFrame`, te zasoby muszą mieć ten sam identyfikator zasobów (na przykład **IDR_MAINFRAME**).  
  
 Gdy `CFrameWnd` obiektu zawiera widoki i dokumentów, są tworzone pośrednio przez platformę, a nie bezpośrednio przez programistę. `CDocTemplate` Obiektu organizuje tworzenia ramki, tworzenie widoków zawierających i połączenie widoki dokument. Parametry `CDocTemplate` Określ konstruktora `CRuntimeClass` trzech klas zaangażowana (dokument, ramki i widoku). A `CRuntimeClass` obiekt jest używany przez platformę w celu dynamicznego tworzenia nowych ramek, gdy został określony przez użytkownika (na przykład przy użyciu polecenia nowy plik lub wielu nowe okno polecenia interfejsu (MDI) dokumentu).  
  
 Pochodne klasy okien ramowych `CFrameWnd` musi być zadeklarowany ze `DECLARE_DYNCREATE` w kolejności dla powyższych `RUNTIME_CLASS` mechanizmu działała prawidłowo.  
  
 A `CFrameWnd` zawiera domyślne implementacje do wykonywania następujących funkcji głównego okna w typowej aplikacji dla systemu Windows:  
  
-   A `CFrameWnd` okno ramowe przechowuje informacje o aktualnie aktywny widok, która jest niezależna od aktywnego okna systemu Windows lub bieżący fokus wprowadzania. Podczas ponownego uaktywniania ramki aktywny widok jest powiadamiany przez wywołanie metody `CView::OnActivateView`.  
  
-   Polecenie wiadomości i wielu typowych komunikaty powiadomień dotyczących ramki, w tym obsługiwane przez `OnSetFocus`, `OnHScroll`, i `OnVScroll` funkcje `CWnd`, zostały przekazane przez `CFrameWnd` ramkę okna do aktualnie aktywnego widoku.  
  
-   Widok aktywne (lub aktywne okno ramowe podrzędnych MDI w przypadku ramki MDI) można określić podpis ramkę okna. Tę funkcję można wyłączyć przez wyłączenie **fws_addtotitle —** bit stylu ramki okna.  
  
-   A `CFrameWnd` okno ramowe zarządza pozycjonowanie paski sterowania, widoków i innych okien podrzędnych wewnątrz obszaru klienckiego ramkę okna. Okno ramowe powoduje także czas bezczynności aktualizacja narzędzi i innych przycisków pasek sterowania. A `CFrameWnd` okno ramowe również ma domyślnej implementacji poleceń przełączanie włączane i wyłączane na pasku narzędzi i stanu.  
  
-   A `CFrameWnd` okno ramowe zarządza na pasku menu głównego. Po wyświetleniu menu podręczne okno ramowe używa **UPDATE_COMMAND_UI** mechanizm określający elementy menu, które powinny być włączone, wyłączone lub zaznaczone. Po wybraniu elementu menu Okno ramowe aktualizuje pasek stanu ciąg komunikatu dla tego polecenia.  
  
-   A `CFrameWnd` okno ramowe ma tabeli akceleratora opcjonalne automatycznie konwertująca klawiszy skrótów.  
  
-   A `CFrameWnd` okno ramowe ma identyfikator pomocy opcjonalny zestaw z `LoadFrame` używanego do pomoc kontekstową. Okno ramowe jest głównym programu orchestrator z stany półmodalne, takich jak trybach Podgląd wydruku i pomocy kontekstowej (SHIFT + F1).  
  
-   A `CFrameWnd` okno ramowe zostanie otwarty plik przeciągnięte z Menedżera plików i porzucić na ramkę okna. Jeśli rozszerzenie jest zarejestrowane i skojarzone z aplikacją, okno ramowe odpowiada na żądania Otwórz exchange (DDE) dane dynamiczne, które występuje, gdy użytkownik otwiera plik danych w Menedżerze plików lub **ShellExecute** Funkcja systemu Windows jest wywoływana.  
  
-   Jeśli okno ramowe w głównym oknie aplikacji (czyli `CWinThread::m_pMainWnd`), gdy użytkownik zamyka aplikację, okno ramowe monituje użytkownika o Zapisz wszystkie zmodyfikowane dokumenty (dla `OnClose` i `OnQueryEndSession`).  
  
-   Jeśli okno ramowe w głównym oknie aplikacji, okno ramowe jest uruchomiona WinHelp w kontekście. Zamyka okno ramowe zostanie zamknięty w Pomocy systemu Windows. Wywołanie pliku EXE, jeśli była uruchomiona dla pomocy dla tej aplikacji.  
  
 Nie należy używać języka C++ **usunąć** operatora, aby zniszczyć okno ramowe. Zamiast nich należy używać słów kluczowych `CWnd::DestroyWindow`. `CFrameWnd` Implementacja `PostNcDestroy` spowoduje usunięcie obiektu języka C++, gdy okno zostanie zniszczone. Gdy użytkownik zamyka okno ramowe domyślnie `OnClose` wywoła obsługi `DestroyWindow`.  
  
 Aby uzyskać więcej informacji na temat `CFrameWnd`, zobacz [okien ramowych](../../mfc/frame-windows.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CFrameWnd`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="activateframe"></a>CFrameWnd::ActivateFrame  
 Wywołanie tej funkcji Członkowskich do aktywowania i przywraca ramkę okna tak, aby widoczne i dostępne dla użytkownika.  
  
```  
virtual void ActivateFrame(int nCmdShow = -1);
```  
  
### <a name="parameters"></a>Parametry  
 `nCmdShow`  
 Określa parametr do przekazania do [CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow). Domyślnie ramki jest wyświetlana i poprawnie przywrócona.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego zwykle jest wywoływana po zdarzeniu interfejsu niezwiązanych z użytkownikiem, takie jak DDE, OLE lub inne zdarzenia, które mogą być wyświetlane użytkownikowi okno ramowe lub jego zawartość.  
  
 Domyślna implementacja aktywuje ramki i powoduje przeniesienie jej do góry porządek osi z, a w razie potrzeby wykonuje te same kroki dla aplikacji głównego okna ramowego.  
  
 Przesłonić tę funkcję elementu członkowskiego, aby zmienić sposób ramki jest aktywny. Na przykład można wymusić okien podrzędnych MDI, aby być zmaksymalizowane. Dodaj odpowiednie funkcje, a następnie wywołuje wersji klasy podstawowej z jawnym `nCmdShow`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#1](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]  
  
##  <a name="beginmodalstate"></a>CFrameWnd::BeginModalState  
 Wywołanie tej funkcji elementu członkowskiego, aby utworzyć modalne okno ramki.  
  
```  
virtual void BeginModalState();
```  
  
##  <a name="cframewnd"></a>CFrameWnd::CFrameWnd  
 Konstruuje `CFrameWnd` obiekt, ale nie tworzy okno ramowe widoczne.  
  
```  
CFrameWnd();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie **Utwórz** można utworzyć okna widoczne.  
  
##  <a name="create"></a>CFrameWnd::Create  
 Wywołanie Utwórz i zainicjuj okno ramowe systemu Windows, skojarzone z `CFrameWnd` obiektu.  
  
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
 `lpszClassName`  
 Punkty na ciąg znaków zakończony znakiem null nazwy klasy systemu Windows. Nazwa klasy może być dowolną nazwą zarejestrowany `AfxRegisterWndClass` funkcji globalnej lub **RegisterClass** funkcji systemu Windows. Jeśli **NULL**, będzie używana domyślna wstępnie zdefiniowanych `CFrameWnd` atrybutów.  
  
 `lpszWindowName`  
 Wskazuje ciąg znaków zakończony znakiem null, który reprezentuje nazwę okna. Używane jako tekst paska tytułu.  
  
 `dwStyle`  
 Określa okno [styl](../../mfc/reference/styles-used-by-mfc.md#window-styles) atrybutów. Obejmują **fws_addtotitle —** stylu, jeśli chcesz automatycznie wyświetlana nazwa dokumentu reprezentowane w oknie na pasku tytułu.  
  
 `rect`  
 Określa rozmiar i położenie okna. `rectDefault` Wartość umożliwia systemu Windows określić rozmiar i położenie nowego okna.  
  
 `pParentWnd`  
 Określa okno nadrzędne tego ramki okna. Ten parametr powinien być **NULL** dla okien ramowych najwyższego poziomu.  
  
 *lpszMenuName*  
 Określa nazwę zasobu menu ma być używany z okna. Użyj **MAKEINTRESOURCE** czy menu ma identyfikator całkowitą zamiast ciągu. Ten parametr może być **NULL**.  
  
 `dwExStyle`  
 Określa okno rozszerzony [styl](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) atrybutów.  
  
 `pContext`  
 Określa wskaźnik [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) struktury. Ten parametr może być **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli inicjowanie zakończy się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Utworzyć `CFrameWnd` obiektu w dwóch krokach. Najpierw należy wywołać konstruktora, który konstruuje `CFrameWnd` obiekt, a następnie wywołać **Utwórz**, która tworzy okno ramowe systemu Windows i dołącza go do `CFrameWnd` obiektu. **Utwórz** inicjuje nazwę klasy okna i nazwa okna i rejestruje wartości domyślne dla jego styl, nadrzędny i związanych z menu.  
  
 Użyj `LoadFrame` zamiast **Utwórz** załadować okno ramowe z zasobu zamiast określania argumentów.  
  
##  <a name="createview"></a>CFrameWnd::CreateView  
 Wywołanie `CreateView` tworzenia widoku w ramce.  
  
```  
CWnd* CreateView(
    CCreateContext* pContext,  
    UINT nID = AFX_IDW_PANE_FIRST);
```  
  
### <a name="parameters"></a>Parametry  
 `pContext`  
 Określa typ widoku i zarządzania dokumentami.  
  
 `nID`  
 Identyfikator widoku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CWnd` obiektu w przypadku powodzenia; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji elementu członkowskiego do utworzenia "widoków", które nie są `CView`-uzyskane w ramce. Po wywołaniu `CreateView`, należy ręcznie ustawić widok aktywny i ustaw ją jako widoczny; te zadania nie są automatycznie wykonywane przez `CreateView`.  
  
##  <a name="dockcontrolbar"></a>CFrameWnd::DockControlBar  
 Powoduje, że pasek sterowania możliwości dokowania do ramki okna.  
  
```  
void DockControlBar(
    CControlBar* pBar,  
    UINT nDockBarID = 0,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pBar`  
 Wskazuje pasek sterowania możliwości dokowania.  
  
 `nDockBarID`  
 Określa, które strony ramkę okna do rozważenia dokowania. Może to być 0, lub co najmniej jeden z następujących czynności:  
  
- `AFX_IDW_DOCKBAR_TOP`Zadokuj do górnej ramki okna.  
  
- **AFX_IDW_DOCKBAR_BOTTOM** doku w dolnej części okna ramki.  
  
- `AFX_IDW_DOCKBAR_LEFT`Dokowanie po lewej stronie ramki okna.  
  
- `AFX_IDW_DOCKBAR_RIGHT`Zadokuj z prawej strony ramkę okna.  
  
 W przypadku wartości 0 pasek sterowania może być zadokowany do dowolnej strony włączone dla dokowanie w oknie ramowym docelowego.  
  
 `lpRect`  
 Określa, we współrzędnych ekranu, gdy pasek sterowania zostanie zadokowany w nieklienckim obszarze okna ramowe docelowego.  
  
### <a name="remarks"></a>Uwagi  
 Pasek sterowania zostanie zadokowane do jednej strony okno ramowe określone w wywołaniach zarówno [CControlBar::EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking) i [CFrameWnd::EnableDocking](#enabledocking). Po stronie wybierany jest określany przez `nDockBarID`.  
  
##  <a name="enabledocking"></a>CFrameWnd::EnableDocking  
 Wywołanie tej funkcji, aby włączyć paski sterowania dokującego w oknie ramowym.  
  
```  
void EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDockStyle`  
 Określa, które strony okno ramowe może służyć jako dokowanie witryn pasków sterowania. Można co najmniej jeden z następujących czynności:  
  
- `CBRS_ALIGN_TOP`Umożliwia dokowanie u góry obszaru klienckiego.  
  
- `CBRS_ALIGN_BOTTOM`Umożliwia dokowanie w dolnej części obszaru klienckiego.  
  
- `CBRS_ALIGN_LEFT`Umożliwia dokowania po lewej stronie obszaru klienckiego.  
  
- `CBRS_ALIGN_RIGHT`Umożliwia dokowania po prawej stronie obszaru klienckiego.  
  
- `CBRS_ALIGN_ANY`Umożliwia dokowanie na dowolnej stronie obszaru klienta.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie paski sterowania zostanie zadokowane po stronie okno ramowe w następującej kolejności: Góra, dół, lewo, prawo.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CToolBar::Create](../../mfc/reference/ctoolbar-class.md#create).  
  
##  <a name="endmodalstate"></a>CFrameWnd::EndModalState  
 Wywołanie tej funkcji Członkowskich zmiany okno ramowe ze modalne niemodalne.  
  
```  
virtual void EndModalState();
```  
  
### <a name="remarks"></a>Uwagi  
 `EndModalState`Włącza wszystkie okna wyłączone przez [BeginModalState](#beginmodalstate).  
  
##  <a name="floatcontrolbar"></a>CFrameWnd::FloatControlBar  
 Wywołaj tę funkcję, aby spowodować, że pasek sterowania do nie jest zadokowany do ramki okna.  
  
```  
void FloatControlBar(
    CControlBar* pBar,  
    CPoint point,  
    DWORD dwStyle = CBRS_ALIGN_TOP);
```  
  
### <a name="parameters"></a>Parametry  
 `pBar`  
 Wskazuje pasek sterowania na jest przestawione.  
  
 `point`  
 Lokalizacja, we współrzędnych ekranu, gdzie zostaną umieszczone lewym górnym rogu pasek sterowania.  
  
 `dwStyle`  
 Określa, czy wyrównywanie pasek sterowania w pionie i w jego nowej ramki okna. Może być jeden z następujących czynności:  
  
- `CBRS_ALIGN_TOP`Kieruje użytkowników pasek sterowania w pionie.  
  
- `CBRS_ALIGN_BOTTOM`Kieruje użytkowników pasek sterowania w pionie.  
  
- `CBRS_ALIGN_LEFT`Kieruje użytkowników pasek sterowania w poziomie.  
  
- `CBRS_ALIGN_RIGHT`Kieruje użytkowników pasek sterowania w poziomie.  
  
 Jeśli style są przekazywane, określając orientacji zarówno w poziomie, jak i w pionie, pasek narzędzi zostanie orientacji w poziomie.  
  
### <a name="remarks"></a>Uwagi  
 Zazwyczaj jest to realizowane przy uruchamianiu aplikacji program jest przywrócenia ustawień z poprzedniej wykonywania.  
  
 Ta funkcja jest wywoływana przez platformę, gdy użytkownik powoduje operacji usuwania przez zwolnienie lewego przycisku myszy podczas przeciągania pasek sterowania za pośrednictwem lokalizacji, która nie jest dostępna dla dokowania.  
  
##  <a name="getactivedocument"></a>CFrameWnd::GetActiveDocument  
 Wywołanie tej funkcji Członkowskich uzyskać wskaźnik do bieżącego **CDocument** dołączony do bieżącego aktywnego widoku.  
  
```  
virtual CDocument* GetActiveDocument();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do bieżącego [CDocument](../../mfc/reference/cdocument-class.md). W przypadku nie bieżącego dokumentu, zwraca **NULL**.  
  
##  <a name="getactiveframe"></a>CFrameWnd::GetActiveFrame  
 Wywołanie tej funkcji Członkowskich uzyskać wskaźnik do aktywnych wiele okna podrzędnego MDI ramki okna dokumentu interfejsu (MDI).  
  
```  
virtual CFrameWnd* GetActiveFrame();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do aktywnego okna podrzędnego MDI. Jeśli aplikacja to aplikacja SDI lub MDI ramki okna nie mają żadnych dokumentów aktywnych niejawne **to** wskaźnika zostaną zwrócone.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli jest nie aktywny formularz podrzędny MDI lub aplikacja jest interfejs pojedynczego dokumentu (SDI) niejawne **to** zwracany jest wskaźnik.  
  
##  <a name="getactiveview"></a>CFrameWnd::GetActiveView  
 Wywołanie funkcji członkowskiej na wskaźnik do aktywnego widoku (jeśli istnieją) dołączona do okno ramowe uzyskany ( `CFrameWnd`).  
  
```  
CView* GetActiveView() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do bieżącego [CView](../../mfc/reference/cview-class.md). Jeśli nie ma bieżącego widoku, zwraca **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja zwraca **NULL** wywołanego dla MDI głównego okna ramowego ( `CMDIFrameWnd`). W aplikacji MDI główną ramkę okna MDI nie ma skojarzonego widoku. Zamiast tego każde okno podrzędne poszczególnych ( `CMDIChildWnd`) zawiera co najmniej jeden widok skojarzony. Aktywnego widoku w aplikacji MDI można uzyskać przez najpierw znajdowanie aktywnego okna podrzędnego MDI i znajdując aktywny widok dla tego okna podrzędnego. Okno podrzędne MDI active można znaleźć przez wywołanie funkcji `MDIGetActive` lub **GetActiveFrame** jak pokazano poniżej:  
  
 [!code-cpp[NVC_MFCWindowing#2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]  
  
##  <a name="getcontrolbar"></a>CFrameWnd::GetControlBar  
 Wywołanie `GetControlBar` uzyskanie dostępu do pasek sterowania, który jest skojarzony z identyfikatorem.  
  
```  
CControlBar* GetControlBar(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Numer identyfikacyjny pasek sterowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do pasek sterowania, który jest skojarzony z identyfikatorem.  
  
### <a name="remarks"></a>Uwagi  
 `nID` Parametr odwołuje się do unikatowego identyfikatora przekazany do **Utwórz** metody pasek sterowania. Więcej informacji o paski sterowania, można znaleźć w temacie prawo [paski sterowania](../../mfc/control-bars.md).  
  
 `GetControlBar`zwróci pasek sterowania, nawet jeśli jest przestawne i w związku z tym nie jest obecnie ramki okna podrzędnego.  
  
##  <a name="getdockstate"></a>CFrameWnd::GetDockState  
 Wywołanie tej funkcji Członkowskich do przechowywania informacji o paski sterowania okno ramowe w stanie `CDockState` obiektu.  
  
```  
void GetDockState(CDockState& state) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `state`  
 Zawiera bieżący stan paski sterowania okno ramowe po powrocie.  
  
### <a name="remarks"></a>Uwagi  
 Następnie można zapisać zawartość `CDockState` do magazynu za pomocą `CDockState::SaveState` lub `Serialize`. Jeśli chcesz później przywrócić paski sterowania do poprzedniego stanu, Załaduj stan z `CDockState::LoadState` lub `Serialize`, następnie wywołaj `SetDockState` dotyczyć paski sterowania okno ramowe poprzedniego stanu.  
  
##  <a name="getmenubarstate"></a>CFrameWnd::GetMenuBarState  
 Pobiera stan wyświetlania menu w bieżącej aplikacji MFC.  
  
```  
virtual DWORD GetMenuBarState();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość zwracana może mieć następujące wartości:  
  
-   AFX_MBS_VISIBLE (0x01) - menu jest widoczny.  
  
-   AFX_MBS_HIDDEN (0x02) - menu jest ukryty.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wystąpi błąd wykonania, ta metoda potwierdzeń w trybie debugowania i zgłasza wyjątek pochodzi od [cexception —](../../mfc/reference/cexception-class.md) klasy.  
  
##  <a name="getmenubarvisibility"></a>CFrameWnd::GetMenuBarVisibility  
 Wskazuje, czy domyślny stan z menu w bieżącej aplikacji MFC jest ukryty lub widoczne.  
  
```  
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca jedną z następujących wartości:  
  
-   AFX_MBV_KEEPVISIBLE (0x01) - menu jest wyświetlany w ogóle razy, a także domyślne nie ma fokusu.  
  
-   AFX_MBV_DISPLAYONFOCUS (0x02) — domyślnie ukryty menu. Jeśli menu jest ukryty, naciśnij klawisz ALT, aby wyświetlić menu i uzyskuje fokus. Jeśli zostanie wyświetlone menu, naciśnij klawisz ALT lub ESC, aby je ukryć.  
  
-   DISPLAYONFOCUS AFX_MBV_ (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04) (bitowe połączenie (lub)) — domyślnie ukryty menu. Jeśli menu jest ukryty, naciśnij klawisz F10, aby wyświetlić menu i uzyskuje fokus. Jeśli zostanie wyświetlone menu, naciśnij klawisz F10, aby przełączyć fokus lub Wyłącz menu. Menu jest wyświetlany, dopóki naciśnij klawisz ALT lub ESC, aby je ukryć.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wystąpi błąd wykonania, ta metoda potwierdzeń w trybie debugowania i zgłasza wyjątek pochodzi od [cexception —](../../mfc/reference/cexception-class.md) klasy.  
  
##  <a name="getmessagebar"></a>CFrameWnd::GetMessageBar  
 Wywołanie tej funkcji Członkowskich otrzymywać wskaźnik do paska stanu.  
  
```  
virtual CWnd* GetMessageBar();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do paska stanu okna.  
  
##  <a name="getmessagestring"></a>CFrameWnd::GetMessageString  
 Zastąp tę funkcję, aby podać niestandardowy ciąg dla identyfikatorów poleceń.  
  
```  
virtual void GetMessageString(
    UINT nID,  
    CString& rMessage) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Identyfikator zasobu wymaganego komunikatu.  
  
 `rMessage`  
 `CString`obiekt, do której ma zostać umieszczony komunikat.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja po prostu ładuje ciągu określonego przez `nID` z pliku zasobów. Ta funkcja jest wywoływana przez platformę, gdy ciąg wiadomości w pasku stanu konieczna jest aktualizacja.  
  
##  <a name="gettitle"></a>CFrameWnd::GetTitle  
 Pobiera tytuł obiektu okna.  
  
```  
CString GetTitle() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) obiekt zawierający bieżący tytuł obiektu okna.  
  
##  <a name="initialupdateframe"></a>CFrameWnd::InitialUpdateFrame  
 Wywołanie **IntitialUpdateFrame** po utworzeniu nowej ramki z **Utwórz**.  
  
```  
void InitialUpdateFrame(
    CDocument* pDoc,  
    BOOL bMakeVisible);
```  
  
### <a name="parameters"></a>Parametry  
 `pDoc`  
 Punkty do dokumentu, z którą jest skojarzone ramkę okna. Może być **NULL**.  
  
 `bMakeVisible`  
 Jeśli **TRUE**, wskazuje, czy ramki powinien być widoczny i aktywne. Jeśli **FALSE**, są widoczne nie elementy podrzędne.  
  
### <a name="remarks"></a>Uwagi  
 Powoduje to, że wszystkie widoki w danym przedziale ramki do odbierania ich `OnInitialUpdate` wywołania.  
  
 Ponadto jeśli nie ma wcześniej aktywny widok, główny widok okno ramowe jest uaktywniona. Podstawowy widok jest widokiem o identyfikatorze podrzędnych **AFX_IDW_PANE_FIRST**. Ponadto okno ramowe stają się widoczne czy `bMakeVisible` jest różna od zera. Jeśli `bMakeVisible` wynosi 0, fokusie i wyświetlany stan okno ramowe pozostaną niezmienione. Nie jest konieczne do wywołania tej funkcji, korzystając z programu framework implementacja nowy plik i Otwórz plik.  
  
##  <a name="inmodalstate"></a>CFrameWnd::InModalState  
 Wywołanie tej funkcji Członkowskich, aby sprawdzić, czy okno ramowe jest modalne i niemodalne.  
  
```  
BOOL InModalState() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli tak; w przeciwnym razie 0.  
  
##  <a name="istracking"></a>CFrameWnd::IsTracking  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, czy pasek podziału w oknie obecnie jest przenoszony.  
  
```  
BOOL IsTracking() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli operacja rozdzielacz jest w toku; w przeciwnym razie 0.  
  
##  <a name="loadacceltable"></a>CFrameWnd::LoadAccelTable  
 Wywołanie tabeli akceleratora określonego obciążenia.  
  
```  
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszResourceName`  
 Określa nazwę zasobu akceleratora. Użyj **MAKEINTRESOURCE** w razie znalezienia zasobu z liczby całkowitej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli został pomyślnie załadowany na tabeli akceleratora; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jednocześnie może być załadowany tylko jedna tabela.  
  
 Tabele akceleratora ładowanych z zasobów są zwalniane automatycznie po zakończeniu działania aplikacji.  
  
 Jeśli należy wywołać `LoadFrame` Aby utworzyć okno ramowe, platformę ładuje tabeli akceleratora wraz z menu i ikony zasobów i kolejne wywołanie tej funkcji członkowskiej jest niepotrzebne.  
  
##  <a name="loadbarstate"></a>CFrameWnd::LoadBarState  
 Wywołanie tej funkcji, aby przywrócić ustawienia każdego pasek sterowania własnością ramkę okna.  
  
```  
void LoadBarState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszProfileName`  
 Nazwa sekcji w pliku inicjującego (INI) lub klucza rejestru systemu Windows, w którym są przechowywane informacje o stanie.  
  
### <a name="remarks"></a>Uwagi  
 Informacje przywrócone obejmuje widoczność, orientacji poziomej/pionowy stan dokowania i pozycji pasek sterowania.  
  
 Aby przywrócić ustawienia musi być przystosowana do rejestru przed wywołaniem `LoadBarState`. Wpisywanie informacji do rejestru przez wywołanie metody [CWinApp::SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey). Zapisać informacji do pliku INI, wywołując [SaveBarState](#savebarstate).  
  
##  <a name="loadframe"></a>CFrameWnd::LoadFrame  
 Wywołanie dynamicznie utworzyć okno ramowe z informacjami o zasobach.  
  
```  
virtual BOOL LoadFrame(
    UINT nIDResource,  
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,  
    CWnd* pParentWnd = NULL,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDResource`  
 Identyfikator skojarzony z okno ramowe zasobów udostępnionych.  
  
 *dwDefaultStyle*  
 Ramki [styl](../../mfc/reference/styles-used-by-mfc.md#window-styles). Obejmują **fws_addtotitle —** stylu, jeśli chcesz automatycznie wyświetlana nazwa dokumentu reprezentowane w oknie na pasku tytułu.  
  
 `pParentWnd`  
 Wskaźnik do elementu nadrzędnego ramki.  
  
 `pContext`  
 Wskaźnik do [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) struktury. Ten parametr może być **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Utworzyć `CFrameWnd` obiektu w dwóch krokach. Najpierw należy wywołać konstruktora, który konstruuje `CFrameWnd` obiekt, a następnie wywołać `LoadFrame`, który ładuje okno ramowe systemu Windows i powiązanych zasobów i dołącza ramkę okna do `CFrameWnd` obiektu. `nIDResource` Parametr określa menu, w tabeli akceleratora ikonę i zasobu ciągu tytułu ramki okna.  
  
 Użyj **Utwórz** funkcji członkowskiej zamiast `LoadFrame` Jeśli chcesz określić wszystkich ramkę okna Tworzenie parametrów.  
  
 Wywołania framework `LoadFrame` po tworzy okno ramowe przy użyciu obiektu szablonu dokumentu.  
  
 Używa w ramach `pContext` argumentu, aby określić obiekty do podłączenia do okno ramowe wraz ze wszystkimi zawarte obiekty widoku. Można ustawić `pContext` argument **NULL** podczas wywoływania `LoadFrame`.  
  
##  <a name="m_bautomenuenable"></a>CFrameWnd::m_bAutoMenuEnable  
 Gdy ten element członkowski danych jest włączona (która jest wartością domyślną), elementy menu, które nie mają `ON_UPDATE_COMMAND_UI` lub `ON_COMMAND` obsługi zostanie automatycznie wyłączone, gdy użytkownik tworzy dół menu.  
  
```  
BOOL m_bAutoMenuEnable;  
```  
  
### <a name="remarks"></a>Uwagi  
 Elementy menu, które mają `ON_COMMAND` obsługi, lecz nie `ON_UPDATE_COMMAND_UI` obsługi zostaną automatycznie włączone.  
  
 Gdy ten element członkowski danych jest ustawiona, elementy menu są włączane automatycznie w taki sam sposób, że włączono przycisków paska narzędzi.  
  
> [!NOTE]
> `m_bAutoMenuEnable`nie ma wpływu na elementy menu najwyższego poziomu.  
  
 Ten element członkowski danych ułatwia implementację opcjonalne poleceń w oparciu o bieżące zaznaczenie i ogranicza potrzebę zapisu `ON_UPDATE_COMMAND_UI` obsługi Włączanie i wyłączanie elementów menu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]  
  
##  <a name="negotiateborderspace"></a>CFrameWnd::NegotiateBorderSpace  
 Wywołanie tej funkcji Członkowskich negocjowania obramowania miejsca w oknie ramowym podczas aktywacji inplace OLE.  
  
```  
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,  
    LPRECT lpRectBorder);
```  
  
### <a name="parameters"></a>Parametry  
 *nBorderCmd*  
 Zawiera jedną z następujących wartości z **wyliczenia BorderCmd**:  
  
- **borderGet** = 1  
  
- **borderRequest** = 2  
  
- **borderSet** = 3  
  
 `lpRectBorder`  
 Wskaźnik do [RECT](../../mfc/reference/rect-structure1.md) struktury lub [CRect](../../atl-mfc-shared/reference/crect-class.md) obiekt określający współrzędne obramowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jest to funkcja członkowska **cframewnd —** implementacji OLE obramowania miejsca negocjacji.  
  
##  <a name="onbarcheck"></a>CFrameWnd::OnBarCheck  
 Wywoływana, gdy akcja jest wykonywana na pasku określonego formantu.  
  
```  
afx_msg BOOL OnBarCheck(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Identyfikator formantu paska jest pokazywany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli istniał pasek sterowania; w przeciwnym razie 0.  
  
##  <a name="oncontexthelp"></a>CFrameWnd::OnContextHelp  
 Obsługuje SHIFT + F1 Pomoc dla elementów w miejscu.  
  
```  
afx_msg void OnContextHelp();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby włączyć Pomoc kontekstowa, należy dodać  
  
 [!code-cpp[NVC_MFCDocViewSDI#16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]  
  
 oświadczenie do użytkownika `CFrameWnd` klasy mapy komunikatów, a także dodawanie wpisu tabeli akceleratora, zwykle SHIFT + F1, aby włączyć tę funkcję elementu członkowskiego.  
  
 Jeśli aplikacja jest OLE kontenera, `OnContextHelp` umieszcza wszystkie elementy w miejscu zawartych w obiekcie ramki okna w trybie pomocy. Kursor zmieni się strzałka i znak zapytania, a użytkownik może następnie przesuń wskaźnik myszy i naciśnij klawisz lewego przycisku myszy wybierz okno dialogowe, okna, menu lub przycisku polecenia. Ta funkcja członkowska wywołuje funkcję Windows `WinHelp` pomocy w kontekście obiektu pod kursorem.  
  
##  <a name="oncreateclient"></a>CFrameWnd::OnCreateClient  
 Wywoływane przez platformę, podczas wykonywania `OnCreate`.  
  
```  
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,  
    CCreateContext* pContext);
```  
  
### <a name="parameters"></a>Parametry  
 `lpcs`  
 Wskaźnik do systemu Windows [CREATESTRUCT](../../mfc/reference/createstruct-structure.md) struktury.  
  
 `pContext`  
 Wskaźnik do [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Nigdy nie wywołują tę funkcję.  
  
 Domyślna implementacja tej funkcji tworzy `CView` obiektu na podstawie informacji dostępnych w `pContext`, jeśli to możliwe.  
  
 Przesłonić tę funkcję, aby zastąpić wartości przekazano `CCreateContext` obiektu lub zmiany są tworzone w obszarze klienta główne okno ramowe formantów. `CCreateContext` Można zastąpić elementów członkowskich są opisane w [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) klasy.  
  
> [!NOTE]
>  Zastępuje wartości przekazane `CREATESTRUCT` struktury. Są one tylko w celach informacyjnych. Jeśli chcesz przesłonić prostokąt początkowej okna, na przykład zastąpić `CWnd` funkcji członkowskiej [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).  
  
##  <a name="onhidemenubar"></a>CFrameWnd::OnHideMenuBar  
 Ta funkcja jest wywoływana, gdy system jest ukryta na pasku menu w bieżącej aplikacji MFC.  
  
```  
virtual void OnHideMenuBar();
```  
  
### <a name="remarks"></a>Uwagi  
 Ten program obsługi zdarzeń umożliwia aplikacji do wykonania akcji niestandardowej, gdy system jest ukryta menu. Nie można zapobiec ukrywane przez menu, ale można na przykład wywołać innych metod, aby pobrać stan lub styl menu.  
  
##  <a name="onsetpreviewmode"></a>CFrameWnd::OnSetPreviewMode  
 Wywołanie tej funkcji członkowskich można ustawić aplikacji główną ramkę okna w i poza trybem Podgląd wydruku.  
  
```  
virtual void OnSetPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>Parametry  
 *bPreview*  
 Określa, czy aplikacja zostanie umieszczona w trybie podglądu wydruku. Ustaw **TRUE** można umieścić w podglądzie wydruku **FALSE** anulować tryb podglądu.  
  
 `pState`  
 Wskaźnik do **CPrintPreviewState** struktury.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja wyłącza wszystkie standardowe paski narzędzi i ukrywa okno główne klienta i menu głównego. Okna ramowe MDI to zmieni się w tymczasowej SDI ramka okna.  
  
 Należy przesłonić tę funkcję elementu członkowskiego, aby dostosować wyświetlanie i ukrywanie pasków sterowania i innymi częściami okno ramowe podczas podglądu wydruku. Wywołanie implementacji klasy podstawowej z wewnątrz zastąpiona wersja.  
  
##  <a name="onshowmenubar"></a>CFrameWnd::OnShowMenuBar  
 Ta funkcja jest wywoływana, gdy system będzie wyświetli na pasku menu w bieżącej aplikacji MFC.  
  
```  
virtual void OnShowMenuBar();
```  
  
### <a name="remarks"></a>Uwagi  
 Ten program obsługi zdarzeń umożliwia aplikacji do wykonania akcji niestandardowej, gdy menu ma być wyświetlany. Nie można zapobiec wyświetlaniu przez menu, ale można na przykład wywołać innych metod, aby pobrać stan lub styl menu.  
  
##  <a name="onupdatecontrolbarmenu"></a>CFrameWnd::OnUpdateControlBarMenu  
 Wywoływane przez platformę po zaktualizowaniu skojarzonego menu.  
  
```  
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parametry  
 `pCmdUI`  
 Wskaźnik do [CCmdUI](../../mfc/reference/ccmdui-class.md) obiekt reprezentujący menu generowane polecenia update. Wywołuje program obsługi aktualizacji [włączyć](../../mfc/reference/ccmdui-class.md#enable) funkcji członkowskiej klasy `CCmdUI` obiektu za pomocą `pCmdUI` można zaktualizować interfejsu użytkownika.  
  
##  <a name="recalclayout"></a>CFrameWnd::RecalcLayout  
 Wywoływane przez platformę, gdy standardowe paski kontrolki są włączane lub wyłączane lub gdy zmieniany jest rozmiar ramki okna.  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bNotify`  
 Określa, czy aktywny element w miejscu dla okno ramowe otrzymuje powiadomienia o zmianie układu. Jeśli **TRUE**, element jest notyfikowana; w przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje domyślną implementację funkcji członkowskiej `CWnd` funkcji członkowskiej `RepositionBars` dotyczyć wszystkich pasków sterowania w ramce, a także okna głównego klienta (zazwyczaj `CView` lub **MDICLIENT**) .  
  
 Przesłonić tę funkcję elementu członkowskiego do kontrolowania wygląd i zachowanie pasków sterowania po zmianie układ okna ramki. Na przykład wywołać ją włączyć paski sterowania lub wyłączyć lub Dodaj inny pasek sterowania.  
  
##  <a name="rectdefault"></a>CFrameWnd::rectDefault  
 Przekazany statycznych `CRect` jako parametru podczas tworzenia okno, aby umożliwić w systemie Windows wybierz początkowy rozmiar i położenie okna.  
  
```  
static AFX_DATA const CRect rectDefault;  
```  
  
##  <a name="savebarstate"></a>CFrameWnd::SaveBarState  
 Wywołanie tej funkcji do przechowywania informacji na temat każdego pasek sterowania własnością ramkę okna.  
  
```  
void SaveBarState(LPCTSTR lpszProfileName) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpszProfileName`  
 Nazwa sekcji w pliku inicjującego lub klucz w rejestrze systemu Windows, w którym są przechowywane informacje o stanie.  
  
### <a name="remarks"></a>Uwagi  
 Te informacje mogą być odczytywane z plików inicjowania przy użyciu [LoadBarState](#loadbarstate). Informacje przechowywane obejmuje widoczność, orientacja poziomo/pionowo dokowanie stanu i położenie paska formantu.  
  
##  <a name="setactivepreviewview"></a>CFrameWnd::SetActivePreviewView  
 Wskazuje określony widok jako aktywny widok podglądu rozbudowanego.  
  
```  
void SetActivePreviewView(CView* pViewNew);
```  
  
### <a name="parameters"></a>Parametry  
 `pViewNew`  
 Wskaźnik do widoku, aby aktywować.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setactiveview"></a>CFrameWnd::SetActiveView  
 Wywołanie tej funkcji członkowskich można ustawić aktywnego widoku.  
  
```  
void SetActiveView(
    CView* pViewNew,  
    BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *pViewNew*  
 Określa wskaźnik [CView](../../mfc/reference/cview-class.md) obiekt, lub **NULL** dla aktywnego widoku.  
  
 `bNotify`  
 Określa, czy widok ma być powiadamiany o aktywacji. Jeśli **TRUE**, `OnActivateView` nosi nazwę dla nowego widoku, jeśli **FALSE**, nie jest.  
  
### <a name="remarks"></a>Uwagi  
 Platforma wywoła tej funkcji automatycznie, gdy użytkownik będzie zmieniał fokus na widok do ramki okna. Można jawnie wywołać `SetActiveView` można zmienić fokus na określony widok.  
  
##  <a name="setdockstate"></a>CFrameWnd::SetDockState  
 Wywołanie tej funkcji Członkowskich dotyczyć stanu informacji przechowywanych w `CDockState` obiekt paski sterowania ramkę okna.  
  
```  
void SetDockState(const CDockState& state);
```  
  
### <a name="parameters"></a>Parametry  
 `state`  
 Przechowywany stan należy dotyczą paski sterowania ramkę okna.  
  
### <a name="remarks"></a>Uwagi  
 Aby przywrócić poprzedni stan paski sterowania, można załadować przechowywany stan z `CDockState::LoadState` lub `Serialize`, następnie użyć `SetDockState` dotyczyć paski sterowania ramkę okna. Poprzedni stan jest przechowywany w `CDockState` obiekt z`GetDockState`  
  
##  <a name="setmenubarstate"></a>CFrameWnd::SetMenuBarState  
 Ustawia stan wyświetlania menu w bieżącej aplikacji MFC ukryte lub wyświetlane.  
  
```  
virtual BOOL SetMenuBarState(DWORD nState);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`nState`|Określa, czy należy wyświetlić lub ukryć menu. `nState` Parametr może mieć następujące wartości:<br /><br /> -AFX_MBS_VISIBLE (0x01) - Wyświetla menu, jeśli jest ukryty, ale nie ma efektu, jeśli nie jest widoczna.<br />-AFX_MBS_HIDDEN (0x02) - ukrywa menu, jeśli jest widoczna, ale nie ma efektu, jeśli jest on ukryty.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli ta metoda pomyślnie zmieni stan menu; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wystąpi błąd wykonania, ta metoda potwierdzeń w trybie debugowania i zgłasza wyjątek pochodzi od [cexception —](../../mfc/reference/cexception-class.md) klasy.  
  
##  <a name="setmenubarvisibility"></a>CFrameWnd::SetMenuBarVisibility  
 Ustawia domyślne zachowanie menu w bieżącej aplikacji MFC w ukrytym lub widoczne.  
  
```  
virtual void SetMenuBarVisibility(DWORD nStyle);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`nStyle`|Określa, czy menu jest domyślnie ukryty, lub nie jest widoczna i ma fokus. `nStyle` Parametr może mieć następujące wartości:<br /><br /> -AFX_MBV_KEEPVISIBLE (0X01)<br />     W menu jest wyświetlane przez cały czas i domyślnie nie ma fokusu.<br />-AFX_MBV_DISPLAYONFOCUS (0X02)-<br />     Domyślnie ukryty menu. Jeśli menu jest ukryty, naciśnij klawisz ALT, aby wyświetlić menu i uzyskuje fokus. Jeśli zostanie wyświetlone menu, naciśnij klawisz ALT lub ESC, aby ukryć menu.<br />-AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0X04)<br />     (bitowe połączenie (lub)) — domyślnie ukryty menu. Jeśli menu jest ukryty, naciśnij klawisz F10, aby wyświetlić menu i uzyskuje fokus. Jeśli zostanie wyświetlone menu, naciśnij klawisz F10, aby przełączyć fokus lub Wyłącz menu. Menu jest wyświetlany, dopóki naciśnij klawisz ALT lub ESC, aby je ukryć.|  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wartość `nStyle` parametr jest nieprawidłowy, ta metoda potwierdzeń w trybie debugowania i zgłasza [CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md) w trybie wersji. W przypadku innych błędów czasu wykonywania tej metody potwierdzeń w trybie debugowania i zgłasza wyjątek pochodzi od [cexception —](../../mfc/reference/cexception-class.md) klasy.  
  
 Ta metoda ma wpływ na stan menu w aplikacji napisanych dla [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] i nowszych.  
  
##  <a name="setmessagetext"></a>CFrameWnd::SetMessageText  
 Wywołanie tej funkcji, aby umieścić ciąg w okienku paska stanu, który ma identyfikator równy 0.  
  
```  
void SetMessageText(LPCTSTR lpszText);  
void SetMessageText(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszText`  
 Wskazuje ciąg, który można umieścić na pasku stanu.  
  
 `nID`  
 Ciąg Identyfikatora zasobu ciągu na pasku stanu.  
  
### <a name="remarks"></a>Uwagi  
 Jest to zazwyczaj w okienku po lewej stronie, a najdłuższym, na pasku stanu.  
  
##  <a name="setprogressbarposition"></a>CFrameWnd::SetProgressBarPosition  
 Ustawia bieżące położenie paska postępu systemu Windows 7, wyświetlane na pasku zadań.  
  
```  
void SetProgressBarPosition(int nProgressPos);
```  
  
### <a name="parameters"></a>Parametry  
 `nProgressPos`  
 Określa położenie do ustawienia. Musi być w zakresie ustawione przez `SetProgressBarRange`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setprogressbarrange"></a>CFrameWnd::SetProgressBarRange  
 Ustawia zakresu dla systemu Windows 7 pasek postępu wyświetlane na pasku zadań.  
  
```  
void SetProgressBarRange(
    int nRangeMin,  
    int nRangeMax);
```  
  
### <a name="parameters"></a>Parametry  
 `nRangeMin`  
 Minimalnej wartości.  
  
 `nRangeMax`  
 Wartość maksymalna.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setprogressbarstate"></a>CFrameWnd::SetProgressBarState  
 Ustawia typ i stan wskaźnika postępu wyświetlany na przycisku paska zadań.  
  
```  
void SetProgressBarState(TBPFLAG tbpFlags);
```  
  
### <a name="parameters"></a>Parametry  
 `tbpFlags`  
 Flagi sterujące bieżący stan przycisku postępu. Określ tylko jedną z następujących flag, ponieważ wszystkie stany wzajemnie się wykluczają: TBPF_NOPROGRESS, TBPF_INDETERMINATE, TBPF_NORMAL, TBPF_ERROR, TBPF_PAUSED.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="settaskbaroverlayicon"></a>CFrameWnd::SetTaskbarOverlayIcon  
 Przeciążone. Stosuje nakładki do paska zadań wskazują stan aplikacji lub powiadamia użytkownika.  
  
```  
BOOL SetTaskbarOverlayIcon(
    UINT nIDResource,  
    LPCTSTR lpcszDescr);

 
BOOL SetTaskbarOverlayIcon(
    HICON hIcon,  
    LPCTSTR lpcszDescr);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDResource`  
 Określa identyfikator zasobu ikony do użycia jako nakładki. Zobacz opis `hIcon` szczegółowe informacje.  
  
 `lpcszDescr`  
 Wskaźnik do ciąg, który zawiera wersję tekst alternatywny informacji przekazywanych w nakładce, aby ułatwić dostęp.  
  
 `hIcon`  
 Dojście do użycia jako nakładkę ikony. Powinno to być mała ikona, pomiaru 16 x 16 pikseli na 96 punktów na cal (dpi). Jeśli ikona nakładki został już zastosowany na pasku zadań, zostanie zastąpiony danej nakładki istniejących. Ta wartość może być `NULL`. Jak `NULL` obsługi wartość zależy od tego, czy przycisk paska zadań reprezentuje jednego okna lub grupy systemu windows. Jest odpowiedzialny za aplikacja wywołująca zwolnienia `hIcon` po jest już potrzebne.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`w przypadku powodzenia; `FALSE` Jeśli wersja systemu operacyjnego jest starsza niż Windows 7 lub jeśli wystąpi błąd ustawiania ikony.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="settitle"></a>CFrameWnd::SetTitle  
 Ustawia tytuł okna obiektu.  
  
```  
void SetTitle(LPCTSTR lpszTitle);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszTitle`  
 Wskaźnik na ciąg znaków zawierający tytuł obiektu okna.  
  
##  <a name="showcontrolbar"></a>CFrameWnd::ShowControlBar  
 Wywołanie tej funkcji Członkowskich, aby pokazać lub ukryć pasek sterowania.  
  
```  
void ShowControlBar(
    CControlBar* pBar,  
    BOOL bShow,  
    BOOL bDelay);
```  
  
### <a name="parameters"></a>Parametry  
 `pBar`  
 Wskaźnik do pasek sterowania mają być pokazywane lub ukryte.  
  
 `bShow`  
 Jeśli **TRUE**, określa, że ma być wyświetlany pasek sterowania. Jeśli **FALSE**, że pasek sterowania ma być ukryty.  
  
 *bDelay*  
 Jeśli **TRUE**, opóźnienie przedstawiający pasek sterowania. Jeśli **FALSE**, Pokaż formantu paska natychmiast.  
  
##  <a name="showownedwindows"></a>CFrameWnd::ShowOwnedWindows  
 Wywołanie tej funkcji Członkowskich, aby wyświetlić wszystkie okna, które są elementami podrzędnymi `CFrameWnd` obiektu.  
  
```  
void ShowOwnedWindows(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 `bShow`  
 Określa, czy należących do systemu windows mają być pokazywane lub ukryte.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Cmdiframewnd — klasa](../../mfc/reference/cmdiframewnd-class.md)   
 [Cmdichildwnd — klasa](../../mfc/reference/cmdichildwnd-class.md)   
 [Cview — klasa](../../mfc/reference/cview-class.md)   
 [Cdoctemplate — klasa](../../mfc/reference/cdoctemplate-class.md)   
 [Struktura CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)
