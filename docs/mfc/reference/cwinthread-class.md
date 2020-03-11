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
ms.openlocfilehash: 43154e1ec4c6b856ad203a4b9ac49e4f4bcf9576
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866568"
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
|[CWinThread:: CWinThread](#cwinthread)|Konstruuje obiekt `CWinThread`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinThread:: onthread](#createthread)|Uruchamia wykonywanie obiektu `CWinThread`.|
|[CWinThread:: ExitInstance](#exitinstance)|Zastąpienie do oczyszczenia po zakończeniu wątku.|
|[CWinThread:: GetMainWnd](#getmainwnd)|Pobiera wskaźnik do okna głównego wątku.|
|[CWinThread:: GetThreadPriority](#getthreadpriority)|Pobiera priorytet bieżącego wątku.|
|[CWinThread:: InitInstance](#initinstance)|Przesłoń, aby przeprowadzić inicjowanie wystąpienia wątku.|
|[CWinThread:: IsIdleMessage](#isidlemessage)|Sprawdza specjalne komunikaty.|
|[CWinThread:: OnIdle](#onidle)|Przesłoń, aby wykonać przetwarzanie w czasie bezczynności dla określonego wątku.|
|[CWinThread::P ostThreadMessage](#postthreadmessage)|Zapisuje komunikat do innego obiektu `CWinThread`.|
|[CWinThread::P reTranslateMessage](#pretranslatemessage)|Filtruje komunikaty przed ich wysłaniem do funkcji systemu Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).|
|[CWinThread::P rocessMessageFilter](#processmessagefilter)|Przechwytuje niektóre komunikaty przed osiągnięciem aplikacji.|
|[CWinThread::P rocessWndProcException](#processwndprocexception)|Przechwytuje wszystkie Nieobsłużone wyjątki zgłoszone przez komunikaty wątku i procedury obsługi poleceń.|
|[CWinThread::P umpMessage](#pumpmessage)|Zawiera pętlę komunikatów wątku.|
|[CWinThread:: ResumeThread](#resumethread)|Zmniejsza liczbę wstrzymań wątku.|
|[CWinThread:: Run](#run)|Kontrolowanie funkcji dla wątków przy użyciu pompy komunikatów. Przesłoń, aby dostosować domyślną pętlę komunikatów.|
|[CWinThread:: SetThreadPriority](#setthreadpriority)|Ustawia priorytet bieżącego wątku.|
|[CWinThread:: SuspendThread](#suspendthread)|Zwiększa liczbę wstrzymań wątku.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinThread:: uchwyt operatora](#operator_handle)|Pobiera uchwyt obiektu `CWinThread`.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CWinThread:: m_bAutoDelete](#m_bautodelete)|Określa, czy obiekt ma zostać zniszczony podczas kończenia wątku.|
|[CWinThread:: m_hThread](#m_hthread)|Dojście do bieżącego wątku.|
|[CWinThread:: m_nThreadID](#m_nthreadid)|Identyfikator bieżącego wątku.|
|[CWinThread:: m_pActiveWnd](#m_pactivewnd)|Wskaźnik do głównego okna aplikacji kontenera, gdy serwer OLE jest aktywny.|
|[CWinThread:: m_pMainWnd](#m_pmainwnd)|Przechowuje wskaźnik do głównego okna aplikacji.|

## <a name="remarks"></a>Uwagi

Główny wątek wykonywania jest zwykle dostarczany przez obiekt pochodzący z `CWinApp`; `CWinApp` pochodzi od `CWinThread`. Dodatkowe obiekty `CWinThread` umożliwiają używanie wielu wątków w danej aplikacji.

Istnieją dwa ogólne typy wątków, które `CWinThread` obsługuje: wątki robocze i wątki interfejsu użytkownika. Wątki robocze nie mają żadnej pompy komunikatów: na przykład wątek wykonujący obliczenia w tle w aplikacji arkusza kalkulacyjnego. Wątki interfejsu użytkownika mają pompę komunikatów i przetwarzają komunikaty odebrane z systemu. [CWinApp](../../mfc/reference/cwinapp-class.md) i klasy pochodne są przykładami wątków interfejsu użytkownika. Inne wątki interfejsu użytkownika mogą być również wyprowadzane bezpośrednio z `CWinThread`.

Obiekty klasy `CWinThread` zwykle istnieją na czas trwania wątku. Jeśli chcesz zmodyfikować to zachowanie, ustaw [m_bAutoDelete](#m_bautodelete) na false.

Klasa `CWinThread` jest niezbędna do zapewnienia, że kod i w pełni wielowątkowy wątek MFC. Dane lokalne wątku używane przez platformę do obsługi informacji dotyczących wątku są zarządzane przez `CWinThread` obiektów. Ze względu na to, że zależność od `CWinThread` obsługiwać dane lokalne wątku, każdy wątek, który używa MFC, musi być utworzony przez MFC. Na przykład wątek utworzony przez funkcję wykonawczą [_beginthread, _beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) nie może używać żadnych interfejsów API MFC.

Aby utworzyć wątek, wywołaj [AfxBeginThread](application-information-and-management.md#afxbeginthread). Istnieją dwie formy, w zależności od tego, czy użytkownik ma mieć wątek procesu roboczego, czy interfejsu użytkownika. Jeśli chcesz, aby wątek interfejsu użytkownika przeszedł do `AfxBeginThread` wskaźnik do `CRuntimeClass` klasy pochodnej `CWinThread`. Jeśli chcesz utworzyć wątek roboczy, Przekaż do `AfxBeginThread` wskaźnikiem do funkcji kontrolującej i parametru do funkcji kontrolującej. Dla wątków roboczych i wątków interfejsu użytkownika można określić parametry opcjonalne, które modyfikują priorytet, rozmiar stosu, flagi tworzenia i atrybuty zabezpieczeń. `AfxBeginThread` zwróci wskaźnik do nowego obiektu `CWinThread`.

Zamiast wywoływania `AfxBeginThread`, można skonstruować obiekt pochodny `CWinThread`, a następnie wywołać `CreateThread`. Ta metoda konstrukcji dwuetapowej jest przydatna, jeśli chcesz ponownie użyć obiektu `CWinThread` między kolejnymi operacjami tworzenia i zakończenia wykonywania wątków.

Aby uzyskać więcej informacji na temat `CWinThread`, zobacz artykuł [wielowątkowość z C++ i MFC](../../parallel/multithreading-with-cpp-and-mfc.md), [wielowątkowość: Tworzenie wątków interfejsu użytkownika](../../parallel/multithreading-creating-user-interface-threads.md), [wielowątkowość: Tworzenie wątków roboczych](../../parallel/multithreading-creating-worker-threads.md)i [wielowątkowość: jak używać klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CWinThread`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

##  <a name="createthread"></a>CWinThread:: onthread

Tworzy wątek do wykonania w przestrzeni adresowej procesu wywołującego.

```
BOOL CreateThread(
    DWORD dwCreateFlags = 0,
    UINT nStackSize = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```

### <a name="parameters"></a>Parametry

*dwCreateFlags*<br/>
Określa dodatkową flagę, która kontroluje tworzenie wątku. Ta flaga może zawierać jedną z dwóch wartości:

- CREATE_SUSPENDED uruchomić wątek z liczbą wstrzymania jednego. Użyj CREATE_SUSPENDED, jeśli chcesz zainicjować jakiekolwiek dane elementu członkowskiego obiektu `CWinThread`, takie jak [m_bAutoDelete](#m_bautodelete) lub dowolnych elementów członkowskich klasy pochodnej, zanim wątek zacznie działać. Po zakończeniu inicjowania Użyj [CWinThread:: ResumeThread](#resumethread) , aby uruchomić wątek uruchomiony. Wątek nie zostanie wykonany do momentu wywołania `CWinThread::ResumeThread`.

- **0** Rozpocznij wątek natychmiast po utworzeniu.

*nStackSize*<br/>
Określa rozmiar w bajtach stosu dla nowego wątku. Jeśli **wartość jest równa 0**, rozmiar stosu jest domyślnie taki sam jak rozmiar wątku podstawowego procesu.

*lpSecurityAttrs*<br/>
Wskazuje strukturę [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) , która określa atrybuty zabezpieczeń wątku.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wątek został utworzony pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj `AfxBeginThread`, aby utworzyć obiekt wątku i wykonać go w jednym kroku. Użyj `CreateThread`, jeśli chcesz ponownie użyć obiektu wątku między kolejnymi tworzeniem i zakończeniem wykonywania wątków.

##  <a name="cwinthread"></a>CWinThread:: CWinThread

Konstruuje obiekt `CWinThread`.

```
CWinThread();
```

### <a name="remarks"></a>Uwagi

Aby rozpocząć wykonywanie wątku, wywołaj [funkcję elementu](#createthread) Członkowskiego. Zwykle tworzone są wątki przez wywołanie [AfxBeginThread](application-information-and-management.md#afxbeginthread), który wywoła tego konstruktora i `CreateThread`.

##  <a name="exitinstance"></a>CWinThread:: ExitInstance

Wywoływane przez platformę z w rzadko [przesłoniętej](#run) funkcji składowej, aby zakończyć to wystąpienie wątku, lub jeśli wywołanie do [InitInstance](#initinstance) zakończy się niepowodzeniem.

```
virtual int ExitInstance();
```

### <a name="return-value"></a>Wartość zwracana

Kod zakończenia wątku; wartość 0 oznacza brak błędów, a wartości większe niż 0 wskazują na błąd. Tę wartość można pobrać, wywołując [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread).

### <a name="remarks"></a>Uwagi

Nie wywołuj tej funkcji elementu członkowskiego z dowolnego miejsca, ale w ramach funkcji składowej `Run`. Ta funkcja członkowska jest używana tylko w wątkach interfejsu użytkownika.

Domyślna implementacja tej funkcji usuwa obiekt `CWinThread`, jeśli [m_bAutoDelete](#m_bautodelete) ma wartość true. Zastąp tę funkcję, jeśli chcesz przeprowadzić dodatkowe czyszczenie po zakończeniu wątku. Implementacja `ExitInstance` powinna wywołać wersję klasy bazowej po wykonaniu kodu.

##  <a name="getmainwnd"></a>CWinThread:: GetMainWnd

Jeśli aplikacja jest serwerem OLE, Wywołaj tę funkcję, aby pobrać wskaźnik do aktywnego okna głównego aplikacji, zamiast bezpośrednio odwoływać się do `m_pMainWnd` elementu członkowskiego obiektu aplikacji.

```
virtual CWnd* GetMainWnd();
```

### <a name="return-value"></a>Wartość zwracana

Ta funkcja zwraca wskaźnik do jednego z dwóch typów okien. Jeśli wątek jest częścią serwera OLE i ma obiekt, który znajduje się w miejscu aktywnym wewnątrz aktywnego kontenera, ta funkcja zwraca element członkowski danych [CWinApp:: m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd) obiektu `CWinThread`.

Jeśli nie ma obiektu, który jest aktywny w obrębie kontenera lub aplikacja nie jest serwerem OLE, ta funkcja zwraca element członkowski danych [m_pMainWnd](#m_pmainwnd) obiektu wątku.

### <a name="remarks"></a>Uwagi

W przypadku wątków interfejsu użytkownika jest to równoważne bezpośrednio odniesieniu się do `m_pActiveWnd` elementu członkowskiego obiektu aplikacji.

Jeśli aplikacja nie jest serwerem OLE, wywołanie tej funkcji jest równoważne bezpośrednio odniesieniu się do `m_pMainWnd` elementu członkowskiego obiektu aplikacji.

Zastąp tę funkcję, aby zmodyfikować zachowanie domyślne.

##  <a name="getthreadpriority"></a>CWinThread:: GetThreadPriority

Pobiera bieżący poziom priorytetu wątku tego wątku.

```
int GetThreadPriority();
```

### <a name="return-value"></a>Wartość zwracana

Bieżący poziom priorytetu wątku w ramach jego klasy priorytetu. Zwracana wartość będzie jedną z następujących elementów: od najwyższego priorytetu do najniższego.

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

Aby uzyskać więcej informacji na temat tych priorytetów, zobacz [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) w Windows SDK.

##  <a name="initinstance"></a>CWinThread:: InitInstance

`InitInstance` musi zostać zastąpiony, aby zainicjować każde nowe wystąpienie wątku interfejsu użytkownika.

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli Inicjalizacja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zwykle zastępuje się `InitInstance` wykonywania zadań, które należy wykonać podczas pierwszego utworzenia wątku.

Ta funkcja członkowska jest używana tylko w wątkach interfejsu użytkownika. Wykonaj inicjalizację wątków roboczych w funkcji kontrolującej przesłanej do [AfxBeginThread](application-information-and-management.md#afxbeginthread).

##  <a name="isidlemessage"></a>CWinThread:: IsIdleMessage

Zastąp tę funkcję, aby zapobiec wywoływaniu `OnIdle` po wygenerowaniu określonych komunikatów.

```
virtual BOOL IsIdleMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Wskazuje bieżący komunikat, który jest przetwarzany.

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli `OnIdle` powinien zostać wywołany po przetworzeniu komunikatu; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Implementacja domyślna nie wywołuje `OnIdle` po nadmiarowych komunikatach myszy i komunikatach generowanych przez migotanie karetki.

Jeśli aplikacja utworzyła krótki czasomierz, `OnIdle` będzie często wywoływany, co powoduje problemy z wydajnością. Aby ulepszyć taką wydajność aplikacji, Zastąp `IsIdleMessage` w klasie pochodnej `CWinApp`aplikacji, aby sprawdzić, czy WM_TIMER komunikaty są następujące:

[!code-cpp[NVC_MFCDocView#189](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]

Obsługa WM_TIMER w ten sposób poprawi wydajność aplikacji, które używają krótkich czasomierzy.

##  <a name="m_bautodelete"></a>CWinThread:: m_bAutoDelete

Określa, czy obiekt `CWinThread` powinien zostać automatycznie usunięty podczas kończenia wątku.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Uwagi

Element członkowski danych `m_bAutoDelete` jest publiczną zmienną typu BOOL.

Wartość `m_bAutoDelete` nie ma wpływu na sposób zamykania uchwytu wątku bazowego, ale wpływa na chronometraż zamykania dojścia. Dojście do wątku jest zawsze zamknięte, gdy obiekt `CWinThread` zostanie zniszczony.

##  <a name="m_hthread"></a>CWinThread:: m_hThread

Dojście do wątku dołączonego do tego `CWinThread`.

```
HANDLE m_hThread;
```

### <a name="remarks"></a>Uwagi

Element członkowski danych `m_hThread` jest publiczną zmienną dojścia do typu. Jest on prawidłowy tylko wtedy, gdy źródłowy obiekt wątku jądra już istnieje, a uchwyt nie został jeszcze zamknięty.

Destruktor CWinThread wywołuje metodę CloseHandle na `m_hThread`. Jeśli [m_bAutoDelete](#m_bautodelete) ma wartość true, gdy wątek kończy działanie, obiekt CWinThread zostaje zniszczony, co unieważnia wszystkie wskaźniki do obiektu CWinThread i jego zmienne składowe. Może być potrzebny członek `m_hThread` do sprawdzenia wartości zakończenia wątku lub oczekiwania na sygnał. Aby zachować obiekt CWinThread i jego element członkowski `m_hThread` podczas wykonywania wątku i po jego zakończeniu, ustaw `m_bAutoDelete` na wartość FALSE, aby umożliwić kontynuowanie wykonywania wątku. W przeciwnym razie wątek może zakończyć działanie, zniszczyć obiekt CWinThread i zamknąć uchwyt przed podjęciem próby jego użycia. W przypadku korzystania z tej techniki użytkownik jest odpowiedzialny za usunięcie obiektu CWinThread.

##  <a name="m_nthreadid"></a>CWinThread:: m_nThreadID

Identyfikator wątku dołączonego do tego `CWinThread`.

```
DWORD m_nThreadID;
```

### <a name="remarks"></a>Uwagi

Element członkowski danych `m_nThreadID` jest publiczną zmienną typu DWORD. Jest on prawidłowy tylko wtedy, gdy źródłowy obiekt wątku jądra już istnieje.
Zobacz także uwagi dotyczące okresu istnienia [m_hThread](#m_hthread) .

### <a name="example"></a>Przykład

  Zobacz przykład dla [AfxGetThread](application-information-and-management.md#afxgetthread).

##  <a name="m_pactivewnd"></a>CWinThread:: m_pActiveWnd

Ten element członkowski danych służy do przechowywania wskaźnika do obiektu aktywnego okna wątku.

```
CWnd* m_pActiveWnd;
```

### <a name="remarks"></a>Uwagi

Biblioteka MFC automatycznie zakończy wątek, gdy okno, do którego odwołuje się `m_pActiveWnd`, zostanie zamknięte. Jeśli ten wątek jest wątkiem podstawowym dla aplikacji, aplikacja zostanie również zakończona. Jeśli ten element członkowski danych ma wartość NULL, aktywne okno dla obiektu `CWinApp` aplikacji zostanie Odziedziczone. `m_pActiveWnd` jest publiczną zmienną typu `CWnd*`.

Zazwyczaj ta zmienna elementu członkowskiego jest ustawiana podczas przesłonięcia `InitInstance`. W wątku roboczym wartość tego elementu członkowskiego danych jest dziedziczona z jego wątku nadrzędnego.

##  <a name="m_pmainwnd"></a>CWinThread:: m_pMainWnd

Ten element członkowski danych służy do przechowywania wskaźnika do obiektu głównego okna wątku.

```
CWnd* m_pMainWnd;
```

### <a name="remarks"></a>Uwagi

Biblioteka MFC automatycznie zakończy wątek, gdy okno, do którego odwołuje się `m_pMainWnd`, zostanie zamknięte. Jeśli ten wątek jest wątkiem podstawowym dla aplikacji, aplikacja zostanie również zakończona. Jeśli ten element członkowski danych ma wartość NULL, okno główne dla obiektu `CWinApp` aplikacji zostanie użyte do określenia, kiedy przerwać wątek. `m_pMainWnd` jest publiczną zmienną typu `CWnd*`.

Zazwyczaj ta zmienna elementu członkowskiego jest ustawiana podczas przesłonięcia `InitInstance`. W wątku roboczym wartość tego elementu członkowskiego danych jest dziedziczona z jego wątku nadrzędnego.

##  <a name="onidle"></a>CWinThread:: OnIdle

Przesłoń tę funkcję elementu członkowskiego, aby przeprowadzić przetwarzanie w czasie bezczynności.

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>Parametry

*lCount*<br/>
Licznik jest zwiększany za każdym razem, `OnIdle` jest wywoływana, gdy kolejka komunikatów wątku jest pusta. Ta liczba jest resetowana do wartości 0 za każdym razem, gdy nowy komunikat jest przetwarzany. Za pomocą parametru *lCount* można określić względną długość czasu bezczynności wątku bez przetwarzania komunikatu.

### <a name="return-value"></a>Wartość zwracana

Różna od zera, aby uzyskać więcej czasu bezczynności przetwarzania; 0, jeśli nie jest wymagany żaden dodatkowy czas przetwarzania.

### <a name="remarks"></a>Uwagi

`OnIdle` jest wywoływana w domyślnej pętli komunikatów, gdy kolejka komunikatów wątku jest pusta. Użyj zastąpień do wywołania własnych zadań programu obsługi bezczynności w tle.

`OnIdle` powinien zwrócić wartość 0, aby wskazać, że nie jest wymagany dodatkowy czas przetwarzania. *LCount* parametr jest zwiększany za każdym `OnIdle` razem, gdy kolejka komunikatów jest pusta, i zostaje zresetowana do 0 za każdym razem, gdy zostanie przetworzony nowy komunikat. Możesz wywoływać różne procedury bezczynności w oparciu o tę liczbę.

Domyślna implementacja tej funkcji składowej zwalnia obiekty tymczasowe i nieużywane biblioteki dołączane dynamicznie z pamięci.

Ta funkcja członkowska jest używana tylko w wątkach interfejsu użytkownika.

Ponieważ aplikacja nie może przetwarzać komunikatów przed zwróceniem `OnIdle`, nie wykonuj zadań w tej funkcji.

##  <a name="operator_handle"></a>CWinThread:: uchwyt operatora

Pobiera uchwyt obiektu `CWinThread`.

```
operator HANDLE() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, uchwyt obiektu wątku; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Użyj uchwytu, aby bezpośrednio wywołać interfejsy API systemu Windows.

##  <a name="postthreadmessage"></a>CWinThread::P ostThreadMessage

Wywołuje się, by opublikować komunikat zdefiniowany przez użytkownika do innego obiektu `CWinThread`.

```
BOOL PostThreadMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*komunikat*<br/>
Identyfikator komunikatu zdefiniowanego przez użytkownika.

*wParam*<br/>
Pierwszy parametr komunikatu.

*lParam*<br/>
Drugi parametr komunikatu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ogłoszony komunikat jest mapowany do odpowiedniego programu obsługi komunikatów przez makro mapy wiadomości ON_THREAD_MESSAGE.

> [!NOTE]
> Po wywołaniu [PostThreadMessage](/windows/win32/api/winuser/nf-winuser-postthreadmessagew)komunikat zostanie umieszczony w kolejce komunikatów wątku. Jednak ze względu na to, że komunikaty ogłoszone w ten sposób nie są skojarzone z oknem, MFC nie wyśle ich do obsługi komunikatów lub poleceń. Aby obsłużyć te komunikaty, Zastąp funkcję `PreTranslateMessage()` klasy pochodnej CWinApp i ręcznie Obsługuj komunikaty.

##  <a name="pretranslatemessage"></a>CWinThread::P reTranslateMessage

Przesłoń tę funkcję w celu filtrowania komunikatów okna przed ich wysłaniem do funkcji systemu Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Wskazuje [strukturę komunikatów](/windows/win32/api/winuser/ns-winuser-msg) zawierającą komunikat do przetworzenia.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli komunikat został w pełni przetworzony w `PreTranslateMessage` i nie powinien być przetwarzany jeszcze. Zero, jeśli komunikat powinien być przetwarzany w normalny sposób.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest używana tylko w wątkach interfejsu użytkownika.

##  <a name="processmessagefilter"></a>CWinThread::P rocessMessageFilter

Funkcja Hook platformy wywołuje tę funkcję elementu członkowskiego, aby filtrować i odpowiadać na określone komunikaty systemu Windows.

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parametry

*kodu*<br/>
Określa kod punktu zaczepienia. Ta funkcja członkowska używa kodu do określenia sposobu przetwarzania *lpMsg.*

*lpMsg*<br/>
Wskaźnik do [struktury komunikatów](/windows/win32/api/winuser/ns-winuser-msg)systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli komunikat jest przetwarzany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Funkcja Hook przetwarza zdarzenia przed wysłaniem ich do normalnego przetwarzania komunikatów aplikacji.

Jeśli zastąpisz tę funkcję zaawansowaną, pamiętaj, aby wywołać wersję klasy bazowej, aby zachować przetwarzanie punktu zaczepienia struktury.

##  <a name="processwndprocexception"></a>CWinThread::P rocessWndProcException

Struktura wywołuje tę funkcję elementu członkowskiego, gdy program obsługi nie przechwytuje wyjątku zgłoszonego w jednym z komunikatów lub obsługi poleceń wątku.

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*e*<br/>
Wskazuje nieobsługiwany wyjątek.

*pMsg*<br/>
Wskazuje [strukturę komunikatów](/windows/win32/api/winuser/ns-winuser-msg) zawierającą informacje o komunikacie systemu Windows, który spowodował wygenerowanie wyjątku przez strukturę.

### <a name="return-value"></a>Wartość zwracana

-1, jeśli zostanie wygenerowany wyjątek WM_CREATE; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Nie wywołuj tej funkcji elementu członkowskiego bezpośrednio.

Domyślna implementacja tej funkcji składowej obsługuje tylko wyjątki wygenerowane z następujących komunikatów:

|Polecenie|Akcja|
|-------------|------------|
|WM_CREATE|Udało.|
|WM_PAINT|Sprawdź poprawność danego okna, uniemożliwiając generowanie innego komunikatu WM_PAINT.|

Przesłoń tę funkcję elementu członkowskiego, aby zapewnić globalną obsługę wyjątków. Wywołaj funkcje podstawowe tylko wtedy, gdy chcesz wyświetlić zachowanie domyślne.

Ta funkcja członkowska jest używana tylko w wątkach, które mają pompę komunikatów.

##  <a name="pumpmessage"></a>CWinThread::P umpMessage

Zawiera pętlę komunikatów wątku.

```
virtual BOOL PumpMessage();
```

### <a name="remarks"></a>Uwagi

`PumpMessage` zawiera pętlę komunikatów wątku. `PumpMessage` jest wywoływana przez `CWinThread` do pompy komunikatów wątku. Możesz wywoływać `PumpMessage` bezpośrednio, aby wymusić przetwarzanie komunikatów, lub zastąpić `PumpMessage`, aby zmienić jego zachowanie domyślne.

Wywoływanie `PumpMessage` bezpośrednio i zastępowanie jego domyślnego zachowania jest zalecane tylko dla zaawansowanych użytkowników.

##  <a name="resumethread"></a>CWinThread:: ResumeThread

Wywołuje się, by wznowić wykonywanie wątku, który został wstrzymany przez funkcję elementu członkowskiego [SuspendThread](#suspendthread) , lub wątku utworzonego za pomocą flagi CREATE_SUSPENDED.

```
DWORD ResumeThread();
```

### <a name="return-value"></a>Wartość zwracana

Liczba poprzednich zawieszeń wątku w przypadku powodzenia; `0xFFFFFFFF` w przeciwnym razie. Jeśli wartość zwracana wynosi zero, bieżący wątek nie został wstrzymany. Jeśli wartość zwracana jest taka, wątek został wstrzymany, ale jest teraz ponownie uruchamiany. Każda wartość zwracana większa od jednej oznacza, że wątek pozostaje zawieszony.

### <a name="remarks"></a>Uwagi

Liczba wstrzymań bieżącego wątku jest zmniejszona o jeden. Jeśli liczba wstrzymań zostanie zredukowana do zera, wątek wznawia wykonywanie; w przeciwnym razie wątek pozostaje zawieszony.

##  <a name="run"></a>CWinThread:: Run

Udostępnia domyślną pętlę komunikatów dla wątków interfejsu użytkownika.

```
virtual int Run();
```

### <a name="return-value"></a>Wartość zwracana

Wartość **int** zwracana przez wątek. Tę wartość można pobrać, wywołując [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread).

### <a name="remarks"></a>Uwagi

`Run` uzyskuje i wysyła komunikaty systemu Windows do momentu odebrania komunikatu [WM_QUIT](/windows/win32/winmsg/wm-quit) przez aplikację. Jeśli kolejka komunikatów wątku nie zawiera obecnie żadnych komunikatów, `Run` wywołuje `OnIdle`, aby przetworzyć czas bezczynności. Komunikaty przychodzące przechodzą do funkcji składowej [PreTranslateMessage](#pretranslatemessage) na potrzeby przetwarzania specjalnego, a następnie do funkcji systemu Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) na potrzeby translacji standardowej klawiatury. Na koniec funkcja [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) systemu Windows jest wywoływana.

`Run` jest rzadko zastępowany, ale można go zastąpić, aby zaimplementować specjalne zachowanie.

Ta funkcja członkowska jest używana tylko w wątkach interfejsu użytkownika.

##  <a name="setthreadpriority"></a>CWinThread:: SetThreadPriority

Ta funkcja ustawia poziom priorytetu bieżącego wątku w ramach jego klasy priorytetu.

```
BOOL SetThreadPriority(int nPriority);
```

### <a name="parameters"></a>Parametry

*nPriority*<br/>
Określa nowy poziom priorytetu wątku w ramach jego klasy priorytetu. Ten parametr musi być jedną z następujących wartości, które są wyświetlane na podstawie najwyższego priorytetu:

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

Aby uzyskać więcej informacji na temat tych priorytetów, zobacz [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Może być wywoływana tylko po pomyślnym powrocie przez [wątek](#createthread) .

##  <a name="suspendthread"></a>CWinThread:: SuspendThread

Zwiększa liczbę wstrzymań bieżącego wątku.

```
DWORD SuspendThread();
```

### <a name="return-value"></a>Wartość zwracana

Liczba poprzednich zawieszeń wątku w przypadku powodzenia; `0xFFFFFFFF` w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Jeśli którykolwiek wątek ma liczbę wstrzymań powyżej zero, ten wątek nie jest wykonywany. Wątek można wznowić, wywołując funkcję elementu członkowskiego [ResumeThread](#resumethread) .

## <a name="see-also"></a>Zobacz także

[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWinApp](../../mfc/reference/cwinapp-class.md)<br/>
[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)
