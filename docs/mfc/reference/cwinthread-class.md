---
title: Cwinthread — klasa
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
ms.openlocfilehash: 0e02f123580696519e59d828ec590456cbd2a81c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270137"
---
# <a name="cwinthread-class"></a>Cwinthread — klasa

Przedstawia wątek wykonania wewnątrz aplikacji.

## <a name="syntax"></a>Składnia

```
class CWinThread : public CCmdTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinThread::CWinThread](#cwinthread)|Konstruuje `CWinThread` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinThread::CreateThread](#createthread)|Rozpoczyna wykonywanie `CWinThread` obiektu.|
|[CWinThread::ExitInstance](#exitinstance)|Należy przesłonić, aby wyczyścić, gdy wątek kończy działanie.|
|[CWinThread::GetMainWnd](#getmainwnd)|Pobiera wskaźnik do głównego okna dla wątku.|
|[CWinThread::GetThreadPriority](#getthreadpriority)|Pobiera priorytet bieżącego wątku.|
|[CWinThread::InitInstance](#initinstance)|Należy przesłonić, aby wykonać inicjowania wystąpienia wątku.|
|[CWinThread::IsIdleMessage](#isidlemessage)|Sprawdza, czy specjalne wiadomości.|
|[CWinThread::OnIdle](#onidle)|Należy przesłonić, aby wykonać przetwarzanie w czasie bezczynności właściwe dla wątków.|
|[CWinThread::PostThreadMessage](#postthreadmessage)|Publikuje komunikat do innego `CWinThread` obiektu.|
|[CWinThread::PreTranslateMessage](#pretranslatemessage)|Filtry komunikatów przed ich wysłaniem do funkcji Windows [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage).|
|[CWinThread::ProcessMessageFilter](#processmessagefilter)|Przechwytuje niektóre komunikaty zanim osiągną one aplikację.|
|[CWinThread::ProcessWndProcException](#processwndprocexception)|Przechwytuje wszystkie nieobsługiwane wyjątki rzucane przez komunikat dla wątku i programy obsługi poleceń.|
|[CWinThread::PumpMessage](#pumpmessage)|zawiera pętli komunikatów dla wątku.|
|[CWinThread::ResumeThread](#resumethread)|Zmniejsza wątku zawiesić count.|
|[CWinThread::Run](#run)|Kontrolowanie funkcji dla wątków, za pomocą "pompy komunikatów". Przesłoń, aby dostosować domyślną pętlę komunikatów.|
|[CWinThread::SetThreadPriority](#setthreadpriority)|Ustawia priorytet bieżącego wątku.|
|[CWinThread::SuspendThread](#suspendthread)|Zwiększa na wątku zawiesić count.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinThread::operator UCHWYTU](#operator_handle)|Pobiera uchwyt `CWinThread` obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CWinThread::m_bAutoDelete](#m_bautodelete)|Określa, czy zniszczenie obiektu na zakończenie wątku.|
|[CWinThread::m_hThread](#m_hthread)|Dojście do bieżącego wątku.|
|[CWinThread::m_nThreadID](#m_nthreadid)|Identyfikator bieżącego wątku.|
|[CWinThread::m_pActiveWnd](#m_pactivewnd)|Wskaźnik do głównego okna aplikacji kontenera, gdy jest aktywny w miejscu.|
|[CWinThread::m_pMainWnd](#m_pmainwnd)|Przechowuje wskaźnik do okna głównego aplikacji.|

## <a name="remarks"></a>Uwagi

Główny wątek wykonywania zwykle są dostarczane przez obiekt, który pochodzi od `CWinApp`; `CWinApp` jest tworzony na podstawie `CWinThread`. Dodatkowe `CWinThread` obiektów zezwolić wielu wątków w danej aplikacji.

Istnieją dwa ogólne typy wątków, `CWinThread` obsługuje: wątki robocze i wątki interfejsu użytkownika. Wątki robocze mają nie "pompy komunikatów": na przykład wątku, który wykonuje obliczenia tło w aplikacji arkusza kalkulacyjnego. Wątki interfejsu użytkownika mają "pompy komunikatów" i przetwarzania komunikatów odebranych z systemu. [Klasa CWinApp](../../mfc/reference/cwinapp-class.md) i klas pochodzących z niego są przykładami wątki interfejsu użytkownika. Inne wątki interfejsu użytkownika mogą również pochodzić bezpośrednio od `CWinThread`.

Obiekty klasy `CWinThread` istnieją zazwyczaj na czas trwania wątku. Jeśli chcesz zmienić to zachowanie, ustaw [m_bAutoDelete](#m_bautodelete) na wartość FALSE.

`CWinThread` Klasa jest konieczne tylko Twój kod i MFC pełni metodą o bezpiecznych wątkach. Zarządza wątków lokalnych danych używane przez platformę, aby zachować informacje właściwe dla wątków `CWinThread` obiektów. Ze względu na to zależność od `CWinThread` do obsługi danych lokalnej wątku, dowolnego wątku, który korzysta z MFC musi utworzonego przez MFC. Na przykład wątku utworzone za pomocą funkcji wykonawczej [_beginthread, _beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) nie można używać dowolnych interfejsów API MFC.

Aby utworzyć wątek, wywołaj [AfxBeginThread](application-information-and-management.md#afxbeginthread). Istnieją dwie formy, w zależności od tego, czy chcesz, aby wątek procesu roboczego lub interfejsu użytkownika. Jeśli wątek interfejsu użytkownika, należy przekazać do `AfxBeginThread` wskaźnik do `CRuntimeClass` z Twojej `CWinThread`-klasy pochodnej. Jeśli chcesz utworzyć wątku roboczego przekazać do `AfxBeginThread` wskaźnik do funkcji kontroli oraz parametr do funkcji kontroli. Dla obu wątków i wątki interfejsu użytkownika można określić parametry opcjonalne, które modyfikują priorytet, rozmiar stosu, flagi tworzenia i atrybuty zabezpieczeń. `AfxBeginThread` Zwraca wskaźnik do nowego `CWinThread` obiektu.

Zamiast wywoływać metodę `AfxBeginThread`, możesz utworzyć `CWinThread`-pochodzi z obiektu, a następnie wywołać następnie `CreateThread`. Ta metoda dwuetapowa konstrukcja jest przydatna, jeśli chcesz ponownie użyć `CWinThread` obiektu między kolejnymi stworzeniem i zakończeń wykonań wątku.

Aby uzyskać więcej informacji na temat `CWinThread`, zobacz artykuły [wielowątkowość z C++ i MFC](../../parallel/multithreading-with-cpp-and-mfc.md), [wielowątkowość: Tworzenie wątków interfejsu użytkownika](../../parallel/multithreading-creating-user-interface-threads.md), [wielowątkowość: Tworzenie wątków roboczych](../../parallel/multithreading-creating-worker-threads.md), i [wielowątkowość: Jak używać klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CWinThread`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="createthread"></a>  CWinThread::CreateThread

Tworzy wątek do wykonania w przestrzeni adresowej procesu wywołującego.

```
BOOL CreateThread(
    DWORD dwCreateFlags = 0,
    UINT nStackSize = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```

### <a name="parameters"></a>Parametry

*dwCreateFlags*<br/>
Określa dodatkowy znacznik, który steruje tworzeniem wątku. Ta flaga może zawierać jedną z dwóch wartości:

- CREATE_SUSPENDED zaczynać wątek wstrzymania liczenia jedengo. Użyj CREATE_SUSPENDED, jeśli chcesz inicjalizować dane z `CWinThread` obiektów, takich jak [m_bAutoDelete](#m_bautodelete) lub wszystkie elementy członkowskie swojej otrzymanej klasy, zanim uruchamiania wątku. Po zakończeniu inicjalizacji, użyj [CWinThread::ResumeThread](#resumethread) można uruchomić wątek systemu. Wątek nie zostanie wykonany dopóki `CWinThread::ResumeThread` jest wywoływana.

- **0** uruchomić wątku od razu po utworzeniu.

*nStackSize*<br/>
Określa rozmiar w bajtach stosu dla nowego wątku. Jeśli **0**, rozmiar stosu jest domyślnie taki sam rozmiar jak z wątku głównego procesu.

*lpSecurityAttrs*<br/>
Wskazuje [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) strukturę, która określa atrybuty zabezpieczeń dla wątku.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli wątek został utworzony pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj `AfxBeginThread` do tworzenia obiektu wątku, a następnie uruchomić go w jednym kroku. Użyj `CreateThread` Jeśli chcesz ponownie użyć obiektu wątku między kolejnymi stworzeniem i zakończenie wątku wykonania.

##  <a name="cwinthread"></a>  CWinThread::CWinThread

Konstruuje `CWinThread` obiektu.

```
CWinThread();
```

### <a name="remarks"></a>Uwagi

Aby rozpocząć wykonywanie wątku, należy wywołać [CreateThread](#createthread) funkcja elementu członkowskiego. Zazwyczaj utworzy wątków przez wywołanie metody [AfxBeginThread](application-information-and-management.md#afxbeginthread), która będzie wywoływać ten konstruktor i `CreateThread`.

##  <a name="exitinstance"></a>  CWinThread::ExitInstance

Metoda wywoływana przez platformę z w ramach rzadko zastąpione [Uruchom](#run) funkcja elementu członkowskiego, aby zakończyć pracę tego wystąpienia obiektu wątku, lub jeśli wywołanie [InitInstance](#initinstance) zakończy się niepowodzeniem.

```
virtual int ExitInstance();
```

### <a name="return-value"></a>Wartość zwracana

Kod wyjścia wątku; 0 oznacza brak błędów i wartości jest większa niż 0 wskazuje błąd. Ta wartość może być pobierany przez wywołanie [GetExitCodeThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getexitcodethread).

### <a name="remarks"></a>Uwagi

Nie wywołuj tej funkcji elementu członkowskiego z dowolnego miejsca ale poziomu `Run` funkcja elementu członkowskiego. Ta funkcja członkowska jest używany tylko w wątki interfejsu użytkownika.

Domyślna implementacja tej funkcji spowoduje usunięcie `CWinThread` obiektu, jeśli [m_bAutoDelete](#m_bautodelete) ma wartość TRUE. Należy przesłonić tę funkcję, jeśli chcesz wykonać dodatkowe oczyszczanie, gdy wątek kończy działanie. Implementacja `ExitInstance` powinny wywoływać wersją klasy bazowej, po wykonaniu kodu.

##  <a name="getmainwnd"></a>  CWinThread::GetMainWnd

Jeśli aplikacja serwera OLE, należy wywołać tę funkcję, aby pobrać wskaźnik do aktywnego okna głównego aplikacji, a nie bezpośrednio odnoszące się do `m_pMainWnd` elementu członkowskiego obiektu aplikacji.

```
virtual CWnd* GetMainWnd();
```

### <a name="return-value"></a>Wartość zwracana

Ta funkcja zwraca wskaźnik do jednego z dwóch typów systemu windows. Jeśli wątek jest częścią serwera OLE i ma obiekt, który jest aktywny w miejscu wewnątrz aktywny kontener, ta funkcja zwraca [CWinApp::m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd) element członkowski danych `CWinThread` obiektu.

Jeśli nie ma żadnego obiektu, który jest aktywny w miejscu w kontenerze, lub aplikacja nie jest serwerem OLE, ta funkcja zwraca [elementu m_pMainWnd](#m_pmainwnd) element członkowski danych obiektu wątek.

### <a name="remarks"></a>Uwagi

Wątki interfejsu użytkownika, to jest odpowiednik bezpośrednio odnoszące się do `m_pActiveWnd` elementu członkowskiego obiektu aplikacji.

Jeśli aplikacja nie jest serwerem OLE, a następnie wywołaniu tej funkcji jest odpowiednikiem bezpośrednio odnoszące się do `m_pMainWnd` elementu członkowskiego obiektu aplikacji.

Należy przesłonić tę funkcję, aby zmodyfikować zachowanie domyślne.

##  <a name="getthreadpriority"></a>  CWinThread::GetThreadPriority

Pobiera bieżący poziom priorytetu wątku tego wątku.

```
int GetThreadPriority();
```

### <a name="return-value"></a>Wartość zwracana

Bieżący poziom priorytetu wątku w swojej klasie priorytetu. Zwrócona wartość będzie miała jedną z następujących pozycji, na liście z najwyższym priorytetem do najniższego:

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

Aby uzyskać więcej informacji na temat tych priorytetów, zobacz [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) w zestawie Windows SDK.

##  <a name="initinstance"></a>  CWinThread::InitInstance

`InitInstance` musi zostać zastąpiona w celu zainicjowania każde wystąpienie nowego wątku interfejsu użytkownika.

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli inicjowanie zakończy się; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zazwyczaj można zastąpić `InitInstance` do wykonywania zadań, które należy wykonać, gdy najpierw jest tworzony wątek.

Ta funkcja członkowska jest używany tylko w wątki interfejsu użytkownika. Wykonaj inicjowania wątków roboczych w przekazany do funkcji kontroli [AfxBeginThread](application-information-and-management.md#afxbeginthread).

##  <a name="isidlemessage"></a>  CWinThread::IsIdleMessage

Przesłonić tę funkcję, aby zachować `OnIdle` wywoływaniu po wygenerowaniu określonych wiadomości.

```
virtual BOOL IsIdleMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Wskazuje bieżący przetwarzanego komunikatu.

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość różną od zera `OnIdle` powinna być wywoływana po przetworzeniu komunikatu; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wywołuje `OnIdle` po komunikaty myszy nadmiarowy i komunikaty generowane przez migająca dioda daszka.

Jeśli aplikacja została utworzona krótki czasomierz `OnIdle` zostanie wywołana często powoduje problemy z wydajnością. Aby poprawić wydajność takich aplikacji, należy zastąpić `IsIdleMessage` aplikacji w witrynie `CWinApp`-klasy w celu sprawdzenia komunikatów WM_TIMER w następujący sposób:

[!code-cpp[NVC_MFCDocView#189](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]

Obsługa WM_TIMER w ten sposób umożliwi zwiększenie wydajności aplikacji, które używaj czasomierzy krótki.

##  <a name="m_bautodelete"></a>  CWinThread::m_bAutoDelete

Określa, czy `CWinThread` obiekt powinien zostać automatycznie usunięty na zakończenie wątku.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Uwagi

`m_bAutoDelete` Element członkowski danych jest publiczną zmienną typu wartość logiczna.

Wartość `m_bAutoDelete` nie wpływa na sposób podstawowy element obsługujący wątek jest zamknięty. Dojście wątku jest zawsze zamknięte, kiedy `CWinThread` niszczony jest obiekt.

##  <a name="m_hthread"></a>  CWinThread::m_hThread

Uchwyt do wątku, dołączony do tego `CWinThread`.

```
HANDLE m_hThread;
```

### <a name="remarks"></a>Uwagi

`m_hThread` Element członkowski danych jest publiczną zmienną typu UCHWYTU. Jest on prawidłowy tylko wtedy, jeśli podstawowy wątek obecnie istnieje.

##  <a name="m_nthreadid"></a>  CWinThread::m_nThreadID

Identyfikator wątku jest dołączony do tego `CWinThread`.

```
DWORD m_nThreadID;
```

### <a name="remarks"></a>Uwagi

`m_nThreadID` Element członkowski danych jest publiczną zmienną typu DWORD. Jest on prawidłowy tylko wtedy, jeśli podstawowy wątek obecnie istnieje.

### <a name="example"></a>Przykład

  Zobacz przykład [afxgetthread —](application-information-and-management.md#afxgetthread).

##  <a name="m_pactivewnd"></a>  CWinThread::m_pActiveWnd

Ten element członkowski danych umożliwiają przechowywanie wskaźnik do obiektu aktywnego okna dla wątku.

```
CWnd* m_pActiveWnd;
```

### <a name="remarks"></a>Uwagi

Biblioteki klas Microsoft Foundation automatycznie z chwilą wątek okna odwołuje się `m_pActiveWnd` jest zamknięty. Jeśli ten wątek jest wątek główny w aplikacji, aplikacji również zostanie zakończony. Jeśli ten element członkowski danych ma wartość NULL, aktywnego okna aplikacji `CWinApp` obiektu będą dziedziczone. `m_pActiveWnd` jest publiczną zmienną typu `CWnd*`.

Zazwyczaj ta zmienna członka jest ustawiany podczas zastąpienia `InitInstance`. W przypadku wątku roboczego wartość ten element członkowski danych są dziedziczone z jego wątku nadrzędnego.

##  <a name="m_pmainwnd"></a>  CWinThread::m_pMainWnd

Ten element członkowski danych umożliwiają przechowywanie wskaźnik do obiektu głównego okna dla wątku.

```
CWnd* m_pMainWnd;
```

### <a name="remarks"></a>Uwagi

Biblioteki klas Microsoft Foundation automatycznie z chwilą wątek okna odwołuje się `m_pMainWnd` jest zamknięty. Jeśli ten wątek jest wątek główny w aplikacji, aplikacji również zostanie zakończony. Jeśli ten element członkowski danych ma wartość NULL, głównego okna aplikacji `CWinApp` obiekt będzie używany do określenia, kiedy zakończenie wątku. `m_pMainWnd` jest publiczną zmienną typu `CWnd*`.

Zazwyczaj ta zmienna członka jest ustawiany podczas zastąpienia `InitInstance`. W przypadku wątku roboczego wartość ten element członkowski danych są dziedziczone z jego wątku nadrzędnego.

##  <a name="onidle"></a>  CWinThread::OnIdle

Zastąpienie tej funkcji elementu członkowskiego, aby wykonać przetwarzanie w czasie bezczynności (%).

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>Parametry

*lCount*<br/>
Licznik jest zwiększany każdorazowo `OnIdle` jest wywoływana, gdy kolejka komunikatów wątku jest pusta. Ten licznik jest resetowany do 0 każdorazowo, gdy nowy komunikat jest przetwarzany. Możesz użyć *lCount* parametru, aby określić względną długość czasu wątku była bezczynna bez przetwarzania wiadomości.

### <a name="return-value"></a>Wartość zwracana

Różna od zera, aby otrzymać więcej przetwarzania czas bezczynności; 0, jeśli nie ma więcej czas bezczynności przetwarzania nie jest konieczne.

### <a name="remarks"></a>Uwagi

`OnIdle` jest wywoływana w domyślną pętlę komunikatów, gdy kolejka komunikatów wątku jest pusta. Przesłonięcia umożliwia wywoływanie własne tła zadania obsługi bezczynności (%).

`OnIdle` powinien zostać zwrócony 0, aby wskazać, że nie dodatkowe bezczynności czas przetwarzania jest wymagane. *LCount* parametru jest zwiększany po każdej `OnIdle` jest wywoływana, gdy kolejka komunikatów jest pusty i zostaje zresetowana do 0 za każdym razem, nowy komunikat jest przetwarzany. Można wywołać z innej procedury bezczynności na podstawie tej liczby.

Domyślna implementacja tej funkcji elementu członkowskiego zwalnia obiekty tymczasowe i biblioteki dołączanej dynamicznie nieużywane z pamięci.

Ta funkcja członkowska jest używany tylko w wątki interfejsu użytkownika.

Ponieważ aplikacja nie może przetworzyć wiadomości do momentu `OnIdle` zwraca, nie wykonuj długich zadań w tej funkcji.

##  <a name="operator_handle"></a>  CWinThread::operator UCHWYTU

Pobiera uchwyt `CWinThread` obiektu.

```
operator HANDLE() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, uchwyt obiektu wątku; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Bezpośrednie wywoływanie interfejsów API Windows za pomocą uchwytu.

##  <a name="postthreadmessage"></a>  CWinThread::PostThreadMessage

Wywołany do publikowania wiadomości zdefiniowanych przez użytkownika do innego `CWinThread` obiektu.

```
BOOL PostThreadMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*komunikat*<br/>
Identyfikator komunikatu zdefiniowanych przez użytkownika.

*wParam*<br/>
Pierwszy parametr wiadomości.

*lParam*<br/>
Drugi parametr wiadomości.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ogłoszony komunikat jest mapowany do obsługi właściwego wiadomości za pomocą makra mapy komunikatów ON_THREAD_MESSAGE.

> [!NOTE]
> Gdy wywołujesz [PostThreadMessage](/windows/desktop/api/winuser/nf-winuser-postthreadmessagea), komunikat jest umieszczana w kolejce komunikatów dla wątku. Jednak ponieważ komunikaty publikowane w ten sposób nie są skojarzone z oknem, MFC nie wyśle je do obsługi komunikatów lub polecenie. Aby umożliwić obsługę tych komunikatów, należy zastąpić `PreTranslateMessage()` funkcji usługi CWinApp klasy pochodnej klasy, a następnie ręcznie obsługi wiadomości.

##  <a name="pretranslatemessage"></a>  CWinThread::PreTranslateMessage

Zastąp tę funkcję, aby przefiltrować komunikaty okna, zanim zostaną rozesłane do funkcji Windows [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage).

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Wskazuje [struktura MSG](/windows/desktop/api/winuser/ns-winuser-tagmsg) zawierający komunikat do przetworzenia.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli w pełnym przetworzeniem komunikat `PreTranslateMessage` i nie powinny być dalej przetwarzane. Zero, jeśli komunikat mają być przetwarzane w zwykły sposób.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest używany tylko w wątki interfejsu użytkownika.

##  <a name="processmessagefilter"></a>  CWinThread::ProcessMessageFilter

Funkcja podłączania struktury wywołania tej funkcji elementu członkowskiego, filtrować i reagować na niektórych komunikatów Windows.

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parametry

*Kod*<br/>
Określa kod punktów zaczepienia. Ta funkcja członkowska używa kodu, aby określić sposób przetwarzania *lpMsg.*

*lpMsg*<br/>
Wskaźnik do Windows [struktura MSG](/windows/desktop/api/winuser/ns-winuser-tagmsg).

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli komunikat jest przetwarzany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Funkcja podłączania przetwarza zdarzenia przed wysłaniem ich do aplikacji normalny komunikat dotyczący przetwarzania.

Jeśli zastąpisz tę funkcję zaawansowanej, pamiętaj wywołać wersji klasy podstawowej, aby zachować struktury utworzenie punktu zaczepienia przetwarzania.

##  <a name="processwndprocexception"></a>  CWinThread::ProcessWndProcException

Struktura wywołuje tej funkcji elementu członkowskiego, w każdym przypadku, gdy program obsługi nie przechwytuje wyjątek zgłoszony w jednej wiadomości dla wątku lub programy obsługi poleceń.

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*e*<br/>
Wskazuje nieobsługiwany wyjątek.

*pMsg*<br/>
Wskazuje [struktura MSG](/windows/desktop/api/winuser/ns-winuser-tagmsg) zawierające informacje dotyczące komunikatów systemu windows, które spowodowało platformę, aby zgłosić wyjątek.

### <a name="return-value"></a>Wartość zwracana

-1, jeśli generowany jest wyjątek WM_CREATE; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Nie wywołuj tej funkcji elementu członkowskiego bezpośrednio.

Domyślna implementacja tej funkcji elementu członkowskiego obsługuje tylko wyjątki generowane z następujących komunikatów:

|Polecenie|Akcja|
|-------------|------------|
|WM_CREATE|Zakończyć się niepowodzeniem.|
|WM_PAINT|Sprawdź poprawność zmodyfikowanego okna, w związku z tym uniemożliwia innym komunikat WM_PAINT generowany.|

Zastąpienie tej funkcji elementu członkowskiego w celu zapewnienia obsługi globalnej listy wyjątków. Podstawowe funkcje należy wywołać tylko wtedy, gdy chcesz wyświetlić zachowanie domyślne.

Ta funkcja członkowska jest używany tylko w wątki, które zawierają "pompy komunikatów".

##  <a name="pumpmessage"></a>  CWinThread::PumpMessage

zawiera pętli komunikatów dla wątku.

```
virtual BOOL PumpMessage();
```

### <a name="remarks"></a>Uwagi

`PumpMessage` zawiera pętli komunikatów dla wątku. `PumpMessage` jest wywoływana przez `CWinThread` pompy komunikatów dla wątku. Możesz wywołać `PumpMessage` bezpośrednio wymusić komunikaty mają być przetwarzane, lub możesz zastąpić `PumpMessage` na zmianę zachowania domyślnego.

Wywoływanie `PumpMessage` bezpośrednio i przesłanianie jej zachowanie domyślne jest zalecane tylko dla zaawansowanych użytkowników.

##  <a name="resumethread"></a>  CWinThread::ResumeThread

Wywołuje się, aby wznowić wykonywanie wątku, który został zawieszony przez [SuspendThread](#suspendthread) funkcji członkowskiej lub utworzone przy użyciu flagi CREATE_SUSPENDED wątku.

```
DWORD ResumeThread();
```

### <a name="return-value"></a>Wartość zwracana

Wątek w poprzednim zawiesić liczba w przypadku powodzenia; `0xFFFFFFFF` inaczej. Jeśli wartość zwracana wynosi zero, bieżący wątek nie zostało wstrzymane. Jeśli wartość zwracaną, wątek zostało wstrzymane, ale teraz ponownie uruchomiona. Wartość zwracana większa niż co oznacza, że wątek Kreator nie wznawia działania.

### <a name="remarks"></a>Uwagi

Wstrzymania liczenia bieżącego wątku została zmniejszona o jeden. W przypadku wstrzymania liczenia na zero, wątek wznawia działanie; w przeciwnym razie wątek Kreator nie wznawia działania.

##  <a name="run"></a>  CWinThread::Run

Udostępnia domyślną pętlę komunikatów dla wątków interfejsu użytkownika.

```
virtual int Run();
```

### <a name="return-value"></a>Wartość zwracana

**Int** wartość zwracana przez wątek. Ta wartość może być pobierany przez wywołanie [GetExitCodeThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getexitcodethread).

### <a name="remarks"></a>Uwagi

`Run` uzyskuje i wysyła komunikaty Windows, aż aplikacja otrzymuje [WM_QUIT](/windows/desktop/winmsg/wm-quit) wiadomości. Jeśli kolejka komunikatów wątku zawiera obecnie żadne komunikaty o `Run` wywołania `OnIdle` do wykonywania przetwarzania w czasie bezczynności (%). Komunikaty przychodzące, przejdź do [pretranslatemessage —](#pretranslatemessage) funkcja elementu członkowskiego dla specjalnego przetwarzania, a następnie do funkcji Windows [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) standardowy interfejs użytkownika translacji. Na koniec [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) Windows funkcja jest wywoływana.

`Run` rzadko zostanie zastąpiona, ale można ją zastąpić, tak aby implementował specjalnego zachowania.

Ta funkcja członkowska jest używany tylko w wątki interfejsu użytkownika.

##  <a name="setthreadpriority"></a>  CWinThread::SetThreadPriority

Funkcja ta ustawia poziom priorytetu bieżącego wątku w swojej klasie priorytetu.

```
BOOL SetThreadPriority(int nPriority);
```

### <a name="parameters"></a>Parametry

*nPriority*<br/>
Określa nowy poziom priorytetu wątku w swojej klasie priorytetu. Ten parametr musi mieć jedną z następujących wartości, na liście z najwyższym priorytetem do najniższego:

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

Aby uzyskać więcej informacji na temat tych priorytetów, zobacz [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Można go wywołać jedynie po [CreateThread](#createthread) zwraca pomyślnie.

##  <a name="suspendthread"></a>  CWinThread::SuspendThread

Zwiększa bieżącego wątku zawiesić count.

```
DWORD SuspendThread();
```

### <a name="return-value"></a>Wartość zwracana

Wątek w poprzednim zawiesić liczba w przypadku powodzenia; `0xFFFFFFFF` inaczej.

### <a name="remarks"></a>Uwagi

Jeśli wątek wstrzymania liczenia większych niż zero, który nie jest wykonywane. Wątek może być wznowione przez wywołanie metody [ResumeThread](#resumethread) funkcja elementu członkowskiego.

## <a name="see-also"></a>Zobacz także

[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWinApp](../../mfc/reference/cwinapp-class.md)<br/>
[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)
