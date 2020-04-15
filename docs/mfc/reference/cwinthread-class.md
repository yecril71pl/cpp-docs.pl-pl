---
title: Klasa CWinThread
ms.date: 11/04/2016
f1_keywords:
- CWinThread
- AFXWIN/CWinThread
- AFXWIN/CWinThread::CWinThread
- AFXWIN/CWinThread::CreateThread
- AFXWIN/CWinThread::ExitInstance
- AFXWIN/CWinThread::GetMainWnd
- AFXWIN/CWinThread::GetThreadPriority
- AFXWIN/CWinThread::InitInstance
- AFXWIN/CWinThread::IsIdleMessage
- AFXWIN/CWinThread::OnIdle
- AFXWIN/CWinThread::PostThreadMessage
- AFXWIN/CWinThread::PreTranslateMessage
- AFXWIN/CWinThread::ProcessMessageFilter
- AFXWIN/CWinThread::ProcessWndProcException
- AFXWIN/CWinThread::PumpMessage
- AFXWIN/CWinThread::ResumeThread
- AFXWIN/CWinThread::Run
- AFXWIN/CWinThread::SetThreadPriority
- AFXWIN/CWinThread::SuspendThread
- AFXWIN/CWinThread::m_bAutoDelete
- AFXWIN/CWinThread::m_hThread
- AFXWIN/CWinThread::m_nThreadID
- AFXWIN/CWinThread::m_pActiveWnd
- AFXWIN/CWinThread::m_pMainWnd
helpviewer_keywords:
- CWinThread [MFC], CWinThread
- CWinThread [MFC], CreateThread
- CWinThread [MFC], ExitInstance
- CWinThread [MFC], GetMainWnd
- CWinThread [MFC], GetThreadPriority
- CWinThread [MFC], InitInstance
- CWinThread [MFC], IsIdleMessage
- CWinThread [MFC], OnIdle
- CWinThread [MFC], PostThreadMessage
- CWinThread [MFC], PreTranslateMessage
- CWinThread [MFC], ProcessMessageFilter
- CWinThread [MFC], ProcessWndProcException
- CWinThread [MFC], PumpMessage
- CWinThread [MFC], ResumeThread
- CWinThread [MFC], Run
- CWinThread [MFC], SetThreadPriority
- CWinThread [MFC], SuspendThread
- CWinThread [MFC], m_bAutoDelete
- CWinThread [MFC], m_hThread
- CWinThread [MFC], m_nThreadID
- CWinThread [MFC], m_pActiveWnd
- CWinThread [MFC], m_pMainWnd
ms.assetid: 10cdc294-4057-4e76-ac7c-a8967a89af0b
ms.openlocfilehash: f2e95dd3ba8be31633590e37d95dedc8749ebdd8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367417"
---
# <a name="cwinthread-class"></a>Klasa CWinThread

Reprezentuje wątek wykonywania w aplikacji.

## <a name="syntax"></a>Składnia

```
class CWinThread : public CCmdTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinThread::CWinThread](#cwinthread)|Konstruuje `CWinThread` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinThread::CreateThread](#createthread)|Rozpoczyna wykonywanie `CWinThread` obiektu.|
|[CWinThread::ExitInstance](#exitinstance)|Zastądnąć, aby wyczyścić po zakończeniu wątku.|
|[CWinThread::GetMainWnd](#getmainwnd)|Pobiera wskaźnik do głównego okna wątku.|
|[CWinThread::GetThreadPriority](#getthreadpriority)|Pobiera priorytet bieżącego wątku.|
|[CWinThread::InitInstance](#initinstance)|Zastądeń, aby wykonać inicjowanie wystąpienia wątku.|
|[CWinThread::IsIdleMessage](#isidlemessage)|Sprawdza, czy nie ma specjalnych wiadomości.|
|[CWinThread::OnIdle](#onidle)|Zastąrpnąć, aby wykonać przetwarzanie w czasie bezczynności specyficzne dla wątku.|
|[CWinThread::PostThreadMessage](#postthreadmessage)|Wysyła wiadomość do `CWinThread` innego obiektu.|
|[CWinThread::PreTranslateMessage](#pretranslatemessage)|Filtruje wiadomości przed wysłaniem ich do funkcji systemu Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).|
|[CWinThread::ProcessMessageFilter](#processmessagefilter)|Przechwytuje niektóre komunikaty, zanim dotrą do aplikacji.|
|[CWinThread::ProcessWndProcException](#processwndprocexception)|Przechwytuje wszystkie nieobsługiwane wyjątki generowane przez komunikat wątku i programy obsługi poleceń.|
|[CWinThread::PumpMessage](#pumpmessage)|Zawiera pętlę komunikatów wątku.|
|[CWinThread::ResumeThread](#resumethread)|Zmniejsza liczbę wstrzymań wątku.|
|[CWinThread::Uruchom](#run)|Funkcja sterowania gwintami za pomocą pompy wiadomości. Zastąd, aby dostosować domyślną pętlę wiadomości.|
|[CWinThread::SetThreadPriority](#setthreadpriority)|Ustawia priorytet bieżącego wątku.|
|[CWinThread::SuspendThread](#suspendthread)|Zwiększa liczbę wstrzymania wątku.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinThread::operator HANDLE](#operator_handle)|Pobiera dojście `CWinThread` obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CWinThread::m_bAutoDelete](#m_bautodelete)|Określa, czy obiekt ma zniszczyć obiekt podczas kończenia wątku.|
|[CWinThread::m_hThread](#m_hthread)|Dojście do bieżącego wątku.|
|[CWinThread::m_nThreadID](#m_nthreadid)|Identyfikator bieżącego wątku.|
|[CWinThread::m_pActiveWnd](#m_pactivewnd)|Wskaźnik do głównego okna aplikacji kontenera, gdy serwer OLE jest aktywny w miejscu.|
|[CWinThread::m_pMainWnd](#m_pmainwnd)|Przechowuje wskaźnik do głównego okna aplikacji.|

## <a name="remarks"></a>Uwagi

Główny wątek wykonania jest zwykle dostarczany `CWinApp`przez obiekt pochodzący z ; `CWinApp` pochodzi z `CWinThread`. Dodatkowe `CWinThread` obiekty umożliwiają wiele wątków w danej aplikacji.

Istnieją dwa ogólne typy `CWinThread` wątków, które obsługuje: wątki robocze i wątki interfejsu użytkownika. Wątki robocze nie mają pompy wiadomości: na przykład wątek, który wykonuje obliczenia tła w aplikacji arkusza kalkulacyjnego. Wątki interfejsu użytkownika mają pompę komunikatów i komunikaty procesowe odebrane z systemu. [CWinApp](../../mfc/reference/cwinapp-class.md) i klasy pochodzące z niego są przykładami wątków interfejsu użytkownika. Inne wątki interfejsu użytkownika mogą również pochodzić bezpośrednio z programu `CWinThread`.

Obiekty klasy `CWinThread` zazwyczaj istnieją na czas trwania wątku. Jeśli chcesz zmodyfikować to zachowanie, ustaw [m_bAutoDelete](#m_bautodelete) na FALSE.

Klasa `CWinThread` jest niezbędne, aby kod i MFC w pełni bezpieczne wątki. Dane lokalne wątku używane przez platformę do obsługi `CWinThread` informacji specyficznych dla wątku jest zarządzany przez obiekty. Z tego powodu `CWinThread` zależność od do obsługi danych lokalnych wątku, każdy wątek, który używa MFC musi być utworzony przez MFC. Na przykład wątek utworzony przez funkcję wykonywania [_beginthread, _beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) nie można użyć żadnych interfejsów API MFC.

Aby utworzyć wątek, zadzwoń [afxBeginThread](application-information-and-management.md#afxbeginthread). Istnieją dwa formularze, w zależności od tego, czy chcesz wątku interfejsu roboczego lub interfejsu użytkownika. Jeśli chcesz wątku interfejsu użytkownika, `AfxBeginThread` przekazać do `CRuntimeClass` wskaźnika do klasy `CWinThread`pochodnej. Jeśli chcesz utworzyć wątek roboczy, przekaż do `AfxBeginThread` wskaźnika do funkcji sterującej i parametru do funkcji sterującej. Dla wątków roboczych i wątków interfejsu użytkownika można określić parametry opcjonalne, które modyfikują priorytet, rozmiar stosu, flagi tworzenia i atrybuty zabezpieczeń. `AfxBeginThread`powróci wskaźnik do nowego `CWinThread` obiektu.

Zamiast wywoływania `AfxBeginThread`można skonstruować `CWinThread`obiekt pochodny, `CreateThread`a następnie wywołać . Ta dwuetapowa metoda budowy jest przydatna, `CWinThread` jeśli chcesz ponownie użyć obiektu między kolejnymtworzeniem a zakończeniem wykonywania wątku.

Aby uzyskać `CWinThread`więcej informacji na temat , zobacz artykuły [Multithreading z C++ i MFC](../../parallel/multithreading-with-cpp-and-mfc.md), [Wielowątkowość: Tworzenie wątków interfejsu użytkownika,](../../parallel/multithreading-creating-user-interface-threads.md) [Wielowątkowe: Tworzenie wątków roboczych](../../parallel/multithreading-creating-worker-threads.md)i [Wielowątkowe: Jak używać klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

`CWinThread`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cwinthreadcreatethread"></a><a name="createthread"></a>CWinThread::CreateThread

Tworzy wątek do wykonania w przestrzeni adresowej procesu wywołującego.

```
BOOL CreateThread(
    DWORD dwCreateFlags = 0,
    UINT nStackSize = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```

### <a name="parameters"></a>Parametry

*dwCreateSlags*<br/>
Określa dodatkową flagę, która steruje tworzeniem wątku. Ta flaga może zawierać jedną z dwóch wartości:

- CREATE_SUSPENDED Rozpocznij wątek z liczbą wstrzymania jednego. Użyj CREATE_SUSPENDED, jeśli chcesz zainicjować wszelkie dane `CWinThread` członkowskie obiektu, takie jak [m_bAutoDelete](#m_bautodelete) lub dowolnych członków klasy pochodnej, przed uruchomieniem wątku. Po zakończeniu inicjowania użyj [CWinThread::ResumeThread,](#resumethread) aby uruchomić wątek. Wątek nie `CWinThread::ResumeThread` zostanie wykonany, dopóki nie zostanie wywołany.

- **0** Rozpocznij wątek natychmiast po utworzeniu.

*rozmiar nStackSize*<br/>
Określa rozmiar w bajtach stosu dla nowego wątku. Jeśli **0**, rozmiar stosu domyślnie do tego samego rozmiaru, jak w wątku podstawowego procesu.

*lpSecurityAttrs*<br/>
Wskazuje strukturę [SECURITY_ATTRIBUTES,](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) która określa atrybuty zabezpieczeń wątku.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wątek został utworzony pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Służy `AfxBeginThread` do tworzenia obiektu wątku i wykonywania go w jednym kroku. Użyj, `CreateThread` jeśli chcesz ponownie użyć obiektu wątku między kolejnymtworzeniem i zakończeniem wykonywania wątku.

## <a name="cwinthreadcwinthread"></a><a name="cwinthread"></a>CWinThread::CWinThread

Konstruuje `CWinThread` obiekt.

```
CWinThread();
```

### <a name="remarks"></a>Uwagi

Aby rozpocząć wykonywanie wątku, [wywołaj CreateThread](#createthread) funkcji elementu członkowskiego. Zwykle tworzysz wątki, wywołując [AfxBeginThread](application-information-and-management.md#afxbeginthread), który `CreateThread`wywoła ten konstruktor i .

## <a name="cwinthreadexitinstance"></a><a name="exitinstance"></a>CWinThread::ExitInstance

Wywoływana przez strukturę z poziomu rzadko zastępowane [Uruchom](#run) funkcji elementu członkowskiego, aby zakończyć to wystąpienie wątku lub jeśli wywołanie [InitInstance](#initinstance) nie powiedzie się.

```
virtual int ExitInstance();
```

### <a name="return-value"></a>Wartość zwracana

Kod zakończenia wątku; 0 oznacza brak błędów, a wartości większe niż 0 wskazują błąd. Tę wartość można pobrać, wywołując [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread).

### <a name="remarks"></a>Uwagi

Nie należy wywoływać tej funkcji `Run` elementu członkowskiego z dowolnego miejsca, ale w ramach funkcji elementu członkowskiego. Ta funkcja elementu członkowskiego jest używana tylko w wątkach interfejsu użytkownika.

Domyślna implementacja tej funkcji `CWinThread` usuwa obiekt, jeśli [m_bAutoDelete](#m_bautodelete) jest TRUE. Zastąd w tej funkcji, jeśli chcesz wykonać dodatkowe oczyszczanie po zakończeniu wątku. Implementacja `ExitInstance` należy wywołać wersję klasy podstawowej po wykonaniu kodu.

## <a name="cwinthreadgetmainwnd"></a><a name="getmainwnd"></a>CWinThread::GetMainWnd

Jeśli aplikacja jest serwerem OLE, należy wywołać tę funkcję, aby pobrać wskaźnik do aktywnego okna `m_pMainWnd` głównego aplikacji zamiast bezpośrednio odwoływać się do elementu członkowskiego obiektu aplikacji.

```
virtual CWnd* GetMainWnd();
```

### <a name="return-value"></a>Wartość zwracana

Ta funkcja zwraca wskaźnik do jednego z dwóch typów okien. Jeśli wątek jest częścią serwera OLE i ma obiekt, który jest aktywny w miejscu wewnątrz aktywnego kontenera, ta `CWinThread` funkcja zwraca [CWinApp::m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd) element członkowski danych obiektu.

Jeśli nie ma żadnego obiektu, który jest aktywny w miejscu w kontenerze lub aplikacja nie jest serwerem OLE, ta funkcja zwraca [m_pMainWnd](#m_pmainwnd) element członkowski danych obiektu wątku.

### <a name="remarks"></a>Uwagi

W przypadku wątków interfejsu użytkownika jest to równoważne `m_pActiveWnd` bezpośrednio odnoszące się do elementu członkowskiego obiektu aplikacji.

Jeśli aplikacja nie jest serwerem OLE, wywołanie tej funkcji jest `m_pMainWnd` równoznaczne bezpośrednio odwołując się do elementu członkowskiego obiektu aplikacji.

Zastąd w tej funkcji należy zmodyfikować zachowanie domyślne.

## <a name="cwinthreadgetthreadpriority"></a><a name="getthreadpriority"></a>CWinThread::GetThreadPriority

Pobiera bieżący poziom priorytetu wątku tego wątku.

```
int GetThreadPriority();
```

### <a name="return-value"></a>Wartość zwracana

Bieżący poziom priorytetu wątku w ramach klasy priorytetu. Zwrócona wartość będzie jedną z następujących wartości, wymienionych od najwyższego priorytetu do najniższego:

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

Aby uzyskać więcej informacji na temat tych priorytetów, zobacz [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) w zestawie Windows SDK.

## <a name="cwinthreadinitinstance"></a><a name="initinstance"></a>CWinThread::InitInstance

`InitInstance`należy zastąpić, aby zainicjować każde nowe wystąpienie wątku interfejsu użytkownika.

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli inicjowanie zakończy się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zazwyczaj należy zastąpić `InitInstance` do wykonywania zadań, które muszą być wykonane podczas tworzenia wątku po raz pierwszy.

Ta funkcja elementu członkowskiego jest używana tylko w wątkach interfejsu użytkownika. Wykonaj inicjowanie wątków roboczych w funkcji sterującej [przekazanej do AfxBeginThread](application-information-and-management.md#afxbeginthread).

## <a name="cwinthreadisidlemessage"></a><a name="isidlemessage"></a>CWinThread::IsIdleMessage

Zastąd w `OnIdle` tej funkcji należy zachować możliwość wywoływania po wygenerowaniu określonych komunikatów.

```
virtual BOOL IsIdleMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Wskazuje bieżącą wiadomość, która jest przetwarzana.

### <a name="return-value"></a>Wartość zwracana

Nonzero, `OnIdle` jeśli powinny być wywoływane po przetworzeniu wiadomości; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja `OnIdle` nie powoduje wywołania po nadmiarowych komunikatach myszy i komunikatach generowanych przez migające dacie.

Jeśli aplikacja utworzyła krótki czasomierz, `OnIdle` będzie często wywoływana, powodując problemy z wydajnością. Aby poprawić wydajność takiej aplikacji, należy `IsIdleMessage` zastąpić w `CWinApp`klasie pochodnej aplikacji, aby sprawdzić, WM_TIMER komunikatów w następujący sposób:

[!code-cpp[NVC_MFCDocView#189](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]

Obsługa WM_TIMER w ten sposób poprawi wydajność aplikacji korzystających z krótkich czasomierzy.

## <a name="cwinthreadm_bautodelete"></a><a name="m_bautodelete"></a>CWinThread::m_bAutoDelete

Określa, `CWinThread` czy obiekt ma zostać automatycznie usunięty po zakończeniu wątku.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Uwagi

Element `m_bAutoDelete` członkowski danych jest zmienną publiczną typu BOOL.

Wartość `m_bAutoDelete` nie wpływa na sposób dojścia wątku bazowego jest zamknięty, ale ma wpływ na czas zamykania dojścia. Uchwyt wątku jest zawsze `CWinThread` zamknięty, gdy obiekt jest niszczony.

## <a name="cwinthreadm_hthread"></a><a name="m_hthread"></a>CWinThread::m_hThread

Uchwyt do gwintu `CWinThread`dołączonego do tego .

```
HANDLE m_hThread;
```

### <a name="remarks"></a>Uwagi

Element `m_hThread` członkowski danych jest zmienną publiczną typu HANDLE. Jest prawidłowy tylko wtedy, gdy podstawowy obiekt wątku jądra obecnie istnieje, a dojście nie zostało jeszcze zamknięte.

CWinThread destruktor wywołuje CloseHandle na `m_hThread`. Jeśli [m_bAutoDelete](#m_bautodelete) jest true po zakończeniu wątku, CWinThread obiekt jest niszczony, co unieważnia wszystkie wskaźniki do CWinThread obiektu i jego zmiennych członkowskich. Może być `m_hThread` potrzebny element członkowski, aby sprawdzić wartość zakończenia wątku lub czekać na sygnał. Aby zachować CWinThread `m_hThread` obiektu i jego element członkowski `m_bAutoDelete` podczas wykonywania wątku i po jego zakończeniu, ustawić false przed zezwoleniem na wykonanie wątku, aby kontynuować. W przeciwnym razie wątek może zakończyć, zniszczyć CWinThread obiektu i zamknąć dojście przed podjęciem próby użycia go. Jeśli używasz tej techniki, jesteś odpowiedzialny za usunięcie CWinThread obiektu.

## <a name="cwinthreadm_nthreadid"></a><a name="m_nthreadid"></a>CWinThread::m_nThreadID

Identyfikator wątku dołączonego do `CWinThread`tego .

```
DWORD m_nThreadID;
```

### <a name="remarks"></a>Uwagi

Element `m_nThreadID` członkowski danych jest zmienną publiczną typu DWORD. Jest prawidłowy tylko wtedy, gdy podstawowy obiekt wątku jądra obecnie istnieje.
Zobacz także uwagi na temat [m_hThread](#m_hthread) życia.

### <a name="example"></a>Przykład

  Zobacz przykład [afxgetthread](application-information-and-management.md#afxgetthread).

## <a name="cwinthreadm_pactivewnd"></a><a name="m_pactivewnd"></a>CWinThread::m_pActiveWnd

Ten element członkowski danych służy do przechowywania wskaźnika do aktywnego obiektu okna wątku.

```
CWnd* m_pActiveWnd;
```

### <a name="remarks"></a>Uwagi

Biblioteka klas programu Microsoft Foundation automatycznie zakończy wątek `m_pActiveWnd` po zamknięciu okna, o którym mowa. Jeśli ten wątek jest wątkiem podstawowym dla aplikacji, aplikacja zostanie również zakończona. Jeśli ten element członkowski danych ma wartość `CWinApp` NULL, aktywne okno obiektu aplikacji zostanie odziedziczone. `m_pActiveWnd`jest zmienną publiczną typu `CWnd*`.

Zazwyczaj ta zmienna elementu członkowskiego jest `InitInstance`ustawiana podczas zastępowania . W wątku roboczego wartość tego elementu członkowskiego danych jest dziedziczona z jego wątku nadrzędnego.

## <a name="cwinthreadm_pmainwnd"></a><a name="m_pmainwnd"></a>CWinThread::m_pMainWnd

Ten element członkowski danych służy do przechowywania wskaźnika do obiektu okna głównego wątku.

```
CWnd* m_pMainWnd;
```

### <a name="remarks"></a>Uwagi

Biblioteka klas programu Microsoft Foundation automatycznie zakończy wątek `m_pMainWnd` po zamknięciu okna, o którym mowa. Jeśli ten wątek jest wątkiem podstawowym dla aplikacji, aplikacja zostanie również zakończona. Jeśli ten element członkowski danych ma wartość `CWinApp` NULL, okno główne obiektu aplikacji będzie używane do określenia, kiedy zakończyć wątek. `m_pMainWnd`jest zmienną publiczną typu `CWnd*`.

Zazwyczaj ta zmienna elementu członkowskiego jest `InitInstance`ustawiana podczas zastępowania . W wątku roboczego wartość tego elementu członkowskiego danych jest dziedziczona z jego wątku nadrzędnego.

## <a name="cwinthreadonidle"></a><a name="onidle"></a>CWinThread::OnIdle

Zastąpokaj tę funkcję elementu członkowskiego, aby wykonać przetwarzanie w czasie bezczynnym.

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>Parametry

*lLicza*<br/>
Licznik zwiększany za każdym `OnIdle` razem jest wywoływany, gdy kolejka komunikatów wątku jest pusta. Ta liczba jest resetowana do 0 za każdym razem, gdy nowa wiadomość jest przetwarzana. Za pomocą parametru *lCount* można określić względny czas bezczynności wątku bez przetwarzania wiadomości.

### <a name="return-value"></a>Wartość zwracana

Nonzero, aby otrzymać więcej czasu bezczynnego przetwarzania; 0, jeśli nie jest potrzebny czas przetwarzania w stanie bezczynnym.

### <a name="remarks"></a>Uwagi

`OnIdle`jest wywoływana w domyślnej pętli komunikatów, gdy kolejka komunikatów wątku jest pusta. Użyj zastąpienia, aby wywołać własne zadania bezczynnego obsługi tła.

`OnIdle`powinien zwrócić 0, aby wskazać, że nie jest wymagany dodatkowy czas bezczynny. *LCount* parametr jest zwiększany za `OnIdle` każdym razem, gdy kolejka komunikatów jest pusta i jest resetowany do 0 za każdym razem, gdy nowa wiadomość jest przetwarzana. Na podstawie tej liczby można wywołać różne procedury bezczynne.

Domyślna implementacja tej funkcji elementu członkowskiego zwalnia obiekty tymczasowe i nieużywane biblioteki łączy dynamicznych z pamięci.

Ta funkcja elementu członkowskiego jest używana tylko w wątkach interfejsu użytkownika.

Ponieważ aplikacja nie może `OnIdle` przetwarzać komunikatów, dopóki nie zwróci, nie należy wykonywać długie zadania w tej funkcji.

## <a name="cwinthreadoperator-handle"></a><a name="operator_handle"></a>CWinThread::operator HANDLE

Pobiera dojście `CWinThread` obiektu.

```
operator HANDLE() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, uchwyt obiektu wątku; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Użyj dojścia, aby bezpośrednio wywołać interfejsy API systemu Windows.

## <a name="cwinthreadpostthreadmessage"></a><a name="postthreadmessage"></a>CWinThread::PostThreadMessage

Wywoływana w celu opublikowania `CWinThread` wiadomości zdefiniowanej przez użytkownika w innym obiekcie.

```
BOOL PostThreadMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*Komunikat*<br/>
Identyfikator komunikatu zdefiniowanego przez użytkownika.

*Wparam*<br/>
Pierwszy parametr wiadomości.

*Lparam*<br/>
Parametr drugiej wiadomości.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wysłana wiadomość jest mapowana do właściwego programu obsługi wiadomości przez makro mapy wiadomości ON_THREAD_MESSAGE.

> [!NOTE]
> Po wywołaniu [PostThreadMessage,](/windows/win32/api/winuser/nf-winuser-postthreadmessagew)wiadomość jest umieszczana w kolejce komunikatów wątku. Jednak ponieważ wiadomości opublikowane w ten sposób nie są skojarzone z oknem, MFC nie będzie wysyłać je do obsługi wiadomości lub poleceń. Aby obsłużyć te wiadomości, należy zastąpić `PreTranslateMessage()` funkcję klasy pochodnej CWinApp i obsługiwać wiadomości ręcznie.

## <a name="cwinthreadpretranslatemessage"></a><a name="pretranslatemessage"></a>CWinThread::PreTranslateMessage

Zastąpuj tę funkcję, aby filtrować komunikaty okienne, zanim zostaną one wysłane do funkcji systemu Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Wskazuje [strukturę MSG](/windows/win32/api/winuser/ns-winuser-msg) zawierającą komunikat do przetworzenia.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wiadomość została `PreTranslateMessage` w pełni przetworzona i nie powinny być przetwarzane dalej. Zero, jeśli wiadomość powinna być przetwarzana w normalny sposób.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest używana tylko w wątkach interfejsu użytkownika.

## <a name="cwinthreadprocessmessagefilter"></a><a name="processmessagefilter"></a>CWinThread::ProcessMessageFilter

Funkcja haka struktury wywołuje tę funkcję elementu członkowskiego, aby filtrować i odpowiadać na niektóre komunikaty systemu Windows.

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parametry

*Kod*<br/>
Określa kod haka. Ta funkcja elementu członkowskiego używa kodu do określenia sposobu przetwarzania *lpMsg.*

*lpMsg*<br/>
Wskaźnik do [struktury MSG](/windows/win32/api/winuser/ns-winuser-msg)systemu Windows .

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wiadomość jest przetwarzana; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Funkcja hak przetwarza zdarzenia, zanim zostaną wysłane do normalnego przetwarzania wiadomości aplikacji.

Jeśli zastąpisz tę zaawansowaną funkcję, należy wywołać wersję klasy podstawowej, aby zachować przetwarzanie haków struktury.

## <a name="cwinthreadprocesswndprocexception"></a><a name="processwndprocexception"></a>CWinThread::ProcessWndProcException

Struktura wywołuje tę funkcję elementu członkowskiego, gdy program obsługi nie przechwytuje wyjątek zgłoszony w jednym z wątku wiadomości lub obsługi poleceń.

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*E*<br/>
Wskazuje nieobsługiwał wyjątek.

*pMsg*<br/>
Wskazuje [strukturę MSG](/windows/win32/api/winuser/ns-winuser-msg) zawierającą informacje o komunikacie systemu Windows, który spowodował, że struktura zgłasza wyjątek.

### <a name="return-value"></a>Wartość zwracana

-1, jeśli generowany jest WM_CREATE wyjątek; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Nie należy wywoływać tej funkcji elementu członkowskiego bezpośrednio.

Domyślna implementacja tej funkcji elementu członkowskiego obsługuje tylko wyjątki generowane z następujących komunikatów:

|Polecenie|Akcja|
|-------------|------------|
|Wm_create|Nie.|
|Wm_paint|Sprawdź poprawność okna, którego dotyczy problem, zapobiegając w ten sposób generowaniu innego komunikatu WM_PAINT.|

Zastąpojąć tę funkcję elementu członkowskiego, aby zapewnić globalną obsługę wyjątków. Wywołaj podstawową funkcjonalność tylko wtedy, gdy chcesz wyświetlić zachowanie domyślne.

Ta funkcja elementu członkowskiego jest używana tylko w wątkach, które mają pompę komunikatów.

## <a name="cwinthreadpumpmessage"></a><a name="pumpmessage"></a>CWinThread::PumpMessage

Zawiera pętlę komunikatów wątku.

```
virtual BOOL PumpMessage();
```

### <a name="remarks"></a>Uwagi

`PumpMessage`zawiera pętlę komunikatów wątku. `PumpMessage`jest wywoływana przez `CWinThread` pompy wątku wiadomości. Można wywołać `PumpMessage` bezpośrednio, aby wymusić wiadomości do przetworzenia lub można zastąpić, aby zmienić jego domyślne `PumpMessage` zachowanie.

Wywoływanie `PumpMessage` bezpośrednio i zastępowanie jego domyślnego zachowania jest zalecane tylko dla zaawansowanych użytkowników.

## <a name="cwinthreadresumethread"></a><a name="resumethread"></a>CWinThread::ResumeThread

Wywołano wznowienie wykonywania wątku, który został zawieszony przez [SuspendThread](#suspendthread) funkcji elementu członkowskiego lub wątku utworzonego z flagą CREATE_SUSPENDED.

```
DWORD ResumeThread();
```

### <a name="return-value"></a>Wartość zwracana

Poprzednia liczba wstrzymania wątku, jeśli zakończy się pomyślnie; `0xFFFFFFFF` w przeciwnym razie. Jeśli zwracana wartość wynosi zero, bieżący wątek nie został zawieszony. Jeśli zwracana wartość jest jedna, wątek został zawieszony, ale jest teraz ponownie uruchomiony. Każda wartość zwracana większa niż jedna oznacza, że wątek pozostaje zawieszony.

### <a name="remarks"></a>Uwagi

Liczba wstrzymania bieżącego wątku jest zmniejszana o jeden. Jeśli liczba wstrzymania zostanie zmniejszona do zera, wątek wznawia wykonywanie; w przeciwnym razie wątek pozostaje zawieszony.

## <a name="cwinthreadrun"></a><a name="run"></a>CWinThread::Uruchom

Zawiera domyślną pętlę komunikatów dla wątków interfejsu użytkownika.

```
virtual int Run();
```

### <a name="return-value"></a>Wartość zwracana

Wartość **int,** która jest zwracana przez wątek. Tę wartość można pobrać, wywołując [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread).

### <a name="remarks"></a>Uwagi

`Run`pobiera i wysyła wiadomości systemu Windows, dopóki aplikacja nie otrzyma [WM_QUIT](/windows/win32/winmsg/wm-quit) wiadomości. Jeśli kolejka komunikatów wątku obecnie `Run` nie `OnIdle` zawiera żadnych komunikatów, wywołania przetwarzania w czasie bezczynności. Przychodzące wiadomości przejść do funkcji elementu członkowskiego [PretranslateMessage](#pretranslatemessage) do specjalnego przetwarzania, a następnie do funkcji Systemu Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) do standardowego tłumaczenia klawiatury. Na koniec wywoływana jest funkcja [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows.

`Run`rzadko jest zastępowane, ale można go zastąpić, aby zaimplementować specjalne zachowanie.

Ta funkcja elementu członkowskiego jest używana tylko w wątkach interfejsu użytkownika.

## <a name="cwinthreadsetthreadpriority"></a><a name="setthreadpriority"></a>CWinThread::SetThreadPriority

Ta funkcja ustawia poziom priorytetu bieżącego wątku w klasie priorytetu.

```
BOOL SetThreadPriority(int nPriority);
```

### <a name="parameters"></a>Parametry

*nPriority*<br/>
Określa nowy poziom priorytetu wątku w klasie priorytetu. Ten parametr musi być jedną z następujących wartości, wymienionych od najwyższego do najniższego:

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

Aby uzyskać więcej informacji na temat tych priorytetów, zobacz [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Można go wywołać tylko po [createthread](#createthread) pomyślnie zwraca.

## <a name="cwinthreadsuspendthread"></a><a name="suspendthread"></a>CWinThread::SuspendThread

Zwiększa liczbę wstrzymania bieżącego wątku.

```
DWORD SuspendThread();
```

### <a name="return-value"></a>Wartość zwracana

Poprzednia liczba wstrzymania wątku, jeśli zakończy się pomyślnie; `0xFFFFFFFF` w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Jeśli dowolny wątek ma liczbę wstrzymania powyżej zera, ten wątek nie jest wykonywany. Wątek można wznowić, wywołując [resumeThread](#resumethread) funkcji elementu członkowskiego.

## <a name="see-also"></a>Zobacz też

[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWinApp](../../mfc/reference/cwinapp-class.md)<br/>
[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)
