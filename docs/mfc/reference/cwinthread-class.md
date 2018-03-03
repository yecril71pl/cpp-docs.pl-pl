---
title: "Cwinthread — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 406fc12869d6fe02188de6e469af17b3809df9b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cwinthread-class"></a>Cwinthread — klasa
Reprezentuje wątku do wykonania w aplikacji.  
  
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
|[CWinThread::ExitInstance](#exitinstance)|Należy przesłonić, aby wyczyścić, gdy zakończenie z wątku.|  
|[CWinThread::GetMainWnd](#getmainwnd)|Pobiera wskaźnik do okna głównego wątku.|  
|[CWinThread::GetThreadPriority](#getthreadpriority)|Pobiera priorytet bieżącego wątku.|  
|[CWinThread::InitInstance](#initinstance)|Należy przesłonić, aby zainicjować wystąpienia wątku.|  
|[CWinThread::IsIdleMessage](#isidlemessage)|Sprawdza, czy specjalnych wiadomości.|  
|[CWinThread::OnIdle](#onidle)|Należy przesłonić, aby przeprowadzić właściwe dla wątków przetwarzania czas bezczynności.|  
|[CWinThread::PostThreadMessage](#postthreadmessage)|Zapisuje komunikat do innego `CWinThread` obiektu.|  
|[CWinThread::PreTranslateMessage](#pretranslatemessage)|Filtry komunikatów przed ich wysłaniem z funkcjami systemu Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) i [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934).|  
|[CWinThread::ProcessMessageFilter](#processmessagefilter)|Przechwytuje komunikatów przed dotarciem aplikacji.|  
|[CWinThread::ProcessWndProcException](#processwndprocexception)|Przechwytuje wszystkie nieobsługiwane wyjątki rzucane przez komunikat dla wątku i programy obsługi poleceń.|  
|[CWinThread::PumpMessage](#pumpmessage)|Zawiera pętlę komunikatów wątku.|  
|[CWinThread::ResumeThread](#resumethread)|Zmniejsza a wątku zawiesić count.|  
|[CWinThread::Run](#run)|Kontrolowanie funkcji dla wątków z przekazywanie komunikatów. Należy przesłonić, aby dostosować domyślną pętlę komunikatów.|  
|[CWinThread::SetThreadPriority](#setthreadpriority)|Ustawia priorytet bieżącego wątku.|  
|[CWinThread::SuspendThread](#suspendthread)|Zwiększa a wątku zawiesić count.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWinThread::operator dojścia](#operator_handle)|Pobiera dojście `CWinThread` obiektu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWinThread::m_bAutoDelete](#m_bautodelete)|Określa, czy usunąć obiektu na zakończenie wątku.|  
|[CWinThread::m_hThread](#m_hthread)|Dojście do bieżącego wątku.|  
|[CWinThread::m_nThreadID](#m_nthreadid)|Identyfikator bieżącego wątku.|  
|[CWinThread::m_pActiveWnd](#m_pactivewnd)|Wskaźnik do głównego okna aplikacji kontenera, gdy jest aktywny w miejscu.|  
|[CWinThread::m_pMainWnd](#m_pmainwnd)|Zawiera wskaźnik do okna głównego aplikacji.|  
  
## <a name="remarks"></a>Uwagi  
 Głównym wątku do wykonania zwykle są dostarczane przez obiekt pochodzący od `CWinApp`; `CWinApp` jest pochodną `CWinThread`. Dodatkowe `CWinThread` obiektów Zezwalaj wielu wątków w danej aplikacji.  
  
 Istnieją dwa typy ogólne wątków który `CWinThread` obsługuje: wątków roboczych i wątków interfejsu użytkownika. Wątków roboczych nie ma żadnych przekazywanie komunikatów: na przykład wątku, który wykonuje obliczenia tło w aplikacji arkusza kalkulacyjnego. Wątków interfejsu użytkownika ma przekazywanie komunikatów i przetwarza wiadomości odebrane z systemu. [Cwinapp —](../../mfc/reference/cwinapp-class.md) i klas pochodnych są przykłady wątków interfejsu użytkownika. Inne wątki interfejsu użytkownika można również pochodzi bezpośrednio z `CWinThread`.  
  
 Obiekty klasy `CWinThread` zwykle istnieje w czasie trwania wątku. Jeśli chcesz zmienić to zachowanie, ustaw [m_bAutoDelete](#m_bautodelete) do **FALSE**.  
  
 `CWinThread` Klasa jest to niezbędne do zapewnienia pełnej wielowątkowość kod i MFC. Wątków lokalnych danych używany przez platformę w celu zachowania informacje specyficzne dla wątku jest zarządzana przez `CWinThread` obiektów. Ze względu na to zależność od `CWinThread` do obsługi danych lokalnych wątku, którymkolwiek wątku, który używa MFC muszą być utworzone przez MFC. Na przykład utworzone przez funkcję czasu wykonywania wątku [_beginthread —, _beginthreadex —](../../c-runtime-library/reference/beginthread-beginthreadex.md) nie można użyć dowolnego MFC interfejsów API.  
  
 Aby utworzyć wątku, należy wywołać [afxbeginthread —](application-information-and-management.md#afxbeginthread). Istnieją dwie formy, w zależności od tego, czy ma wątku roboczego lub interfejsu użytkownika. Jeśli wątku interfejsu użytkownika, należy przekazać do `AfxBeginThread` wskaźnik do `CRuntimeClass` z Twojej `CWinThread`-klasy. Jeśli chcesz utworzyć wątku roboczego przekazać do `AfxBeginThread` wskaźnik do kontrolowania funkcji i parametru do kontrolowania funkcji. Wątki robocze i wątków interfejsu użytkownika można określić parametry opcjonalne, które modyfikują priorytet, rozmiar stosu flagi tworzenia i atrybutów zabezpieczeń. `AfxBeginThread`Zwraca wskaźnik do nowej `CWinThread` obiektu.  
  
 Zamiast wywoływać metodę `AfxBeginThread`, można utworzyć `CWinThread`-pochodzi z obiektu, a następnie wywołania `CreateThread`. Ta metoda dwuetapowa konstrukcja jest przydatna, jeśli chcesz ponownie użyć `CWinThread` obiektu między kolejnymi tworzenia i zakończenia wykonaniami wątku.  
  
 Aby uzyskać więcej informacji na temat `CWinThread`, zobacz artykuły [Multithreading z C++ i MFC](../../parallel/multithreading-with-cpp-and-mfc.md), [Multithreading: Tworzenie wątków interfejsu użytkownika](../../parallel/multithreading-creating-user-interface-threads.md), [Multithreading: tworzenie procesu roboczego Wątki](../../parallel/multithreading-creating-worker-threads.md), i [wielowątkowość: jak używać klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 `CWinThread`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="createthread"></a>CWinThread::CreateThread  
 Tworzy wątku do wykonania w przestrzeni adresowej procesu wywołującego.  
  
```  
BOOL CreateThread(
    DWORD dwCreateFlags = 0,  
    UINT nStackSize = 0,  
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `dwCreateFlags`  
 Określa dodatkowe flagi, który kontroluje Tworzenie wątku. Ta flaga może zawierać jedną z dwóch wartości:  
  
- **CREATE_SUSPENDED** uruchomić wraz z liczbą Wstrzymaj jednego wątku. Użyj **CREATE_SUSPENDED** Jeśli chcesz zainicjować żadnych danych elementu członkowskiego `CWinThread` obiektów, takich jak [m_bAutoDelete](#m_bautodelete) lub członków klasy pochodnej, zanim uruchomienie wątku. Po zakończeniu inicjowania użytkownika, użyj [CWinThread::ResumeThread](#resumethread) można uruchomić wątku uruchomiona. Wątek nie zostanie wykonany, dopóki `CWinThread::ResumeThread` jest wywoływana.  
  
- **0** uruchomić wątku natychmiast po utworzeniu.  
  
 `nStackSize`  
 Określa rozmiar w bajtach stosu dla nowego wątku. Jeśli **0**, rozmiar stosu domyślnie ten sam rozmiar jak podstawowy wątku przez proces.  
  
 `lpSecurityAttrs`  
 Wskazuje [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) strukturę, która określa atrybuty zabezpieczeń dla wątku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wątek został utworzony pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `AfxBeginThread` do utworzenia obiektu wątku i wykonaj go w jednym kroku. Użyj `CreateThread` Jeśli chcesz użyć ponownie obiektu wątku między kolejnymi tworzenie i zakończenie wątku wykonania.  
  
##  <a name="cwinthread"></a>CWinThread::CWinThread  
 Konstruuje `CWinThread` obiektu.  
  
```  
CWinThread();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby rozpocząć wykonywania wątku, należy wywołać [CreateThread](#createthread) funkcję elementu członkowskiego. Wątki będą zazwyczaj utworzyć przez wywołanie metody [afxbeginthread —](application-information-and-management.md#afxbeginthread), który będzie wywoływać ten konstruktor i `CreateThread`.  
  
##  <a name="exitinstance"></a>CWinThread::ExitInstance  
 Wywoływane przez platformę z wewnątrz rzadko przesłoniętych [Uruchom](#run) funkcji członkowskiej, aby zakończyć pracę tego wystąpienia wątek, lub jeśli wywołanie [InitInstance](#initinstance) nie powiedzie się.  
  
```  
virtual int ExitInstance();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kod zakończenia wątku; 0 oznacza brak błędów, a wartości większe od 0 wskazuje błąd. Ta wartość może być pobierane przez wywołanie [Funkcja GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190).  
  
### <a name="remarks"></a>Uwagi  
 Nie wywołuj tej funkcji członkowskiej z dowolnego miejsca ale poziomu **Uruchom** funkcję elementu członkowskiego. Ta funkcja członkowska jest używana tylko wątków interfejsu użytkownika.  
  
 Domyślna implementacja ta funkcja usuwa `CWinThread` obiekt zostanie [m_bAutoDelete](#m_bautodelete) jest **TRUE**. Należy przesłonić tę funkcję, jeśli chcesz wykonać dodatkowe oczyszczanie, gdy zakończenie z wątku. Implementacji `ExitInstance` powinny wywoływać klasy podstawowej wersji po wykonaniu kodu.  
  
##  <a name="getmainwnd"></a>CWinThread::GetMainWnd  
 Jeśli aplikacja serwera OLE, wywołanie tej funkcji można pobrać wskaźnik do aktywne główne okno aplikacji zamiast bezpośrednio odwołujących się do `m_pMainWnd` element członkowski obiektu aplikacji.  
  
```  
virtual CWnd* GetMainWnd();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta funkcja zwraca wskaźnik do jednego z dwóch typów systemu windows. Jeśli Twoje wątku wchodzi w skład serwera OLE i ma obiekt, który jest aktywny w miejscu wewnątrz kontenera usługi active, ta funkcja zwraca [CWinApp::m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd) elementu członkowskiego danych `CWinThread` obiektu.  
  
 Jeśli nie ma żadnego obiektu, który jest aktywny w miejscu w kontenerze lub aplikacja nie jest serwerem OLE, funkcja zwraca [m_pMainWnd](#m_pmainwnd) element członkowski danych obiektu wątek.  
  
### <a name="remarks"></a>Uwagi  
 Dla wątków interfejsu użytkownika, co jest równoważne bezpośrednio odwołujących się do `m_pActiveWnd` element członkowski obiektu aplikacji.  
  
 Jeśli aplikacja nie jest serwerem OLE, a następnie podczas wywoływania tej funkcji jest odpowiednikiem bezpośrednio odwołujących się do `m_pMainWnd` element członkowski obiektu aplikacji.  
  
 Należy przesłonić tę funkcję, aby zmodyfikować zachowanie domyślne.  
  
##  <a name="getthreadpriority"></a>CWinThread::GetThreadPriority  
 Pobiera bieżący poziom priorytetu wątku tego wątku.  
  
```  
int GetThreadPriority();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżący poziom priorytetu wątku w swojej klasie priorytet. Wartość zwracana będzie jedną z następujących czynności, na liście z najwyższym priorytetem do najniższego:  
  
- **THREAD_PRIORITY_TIME_CRITICAL**  
  
- **THREAD_PRIORITY_HIGHEST**  
  
- **THREAD_PRIORITY_ABOVE_NORMAL**  
  
- **THREAD_PRIORITY_NORMAL**  
  
- **THREAD_PRIORITY_BELOW_NORMAL**  
  
- **THREAD_PRIORITY_LOWEST**  
  
- **THREAD_PRIORITY_IDLE**  
  
 Aby uzyskać więcej informacji o tych priorytetów, zobacz [wykonanie funkcji SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) w zestawie Windows SDK.  
  
##  <a name="initinstance"></a>CWinThread::InitInstance  
 `InitInstance`musi zostać zastąpiona w celu zainicjowania każde wystąpienie nowego wątku interfejsu użytkownika.  
  
```  
virtual BOOL InitInstance();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli inicjowanie zakończy się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Zazwyczaj można zastąpić `InitInstance` do wykonywania zadań, które należy wykonać podczas tworzenia wątku.  
  
 Ta funkcja członkowska jest używana tylko wątków interfejsu użytkownika. Zainicjować wątków roboczych kontrolowanie funkcji przekazany do [afxbeginthread —](application-information-and-management.md#afxbeginthread).  
  
##  <a name="isidlemessage"></a>CWinThread::IsIdleMessage  
 Przesłonić tę funkcję, aby zachować **OnIdle** z wywoływana po wygenerowaniu określonych wiadomości.  
  
```  
virtual BOOL IsIdleMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parametry  
 `pMsg`  
 Wskazuje bieżący przetwarzanego komunikatu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli podano niezerowe `OnIdle` powinna być wywoływana po zakończeniu przetwarzania komunikatów; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja nie wywołuje **OnIdle** po nadmiarowe myszy wiadomości i komunikaty generowane przez migający daszka.  
  
 Jeśli aplikacja została utworzona czasomierz krótkie, **OnIdle** zostanie wywołana często problemów z wydajnością. Aby zwiększyć wydajność takich aplikacji, należy zastąpić `IsIdleMessage` w aplikacji `CWinApp`-klasy do wyszukania `WM_TIMER` wiadomości w następujący sposób:  
  
 [!code-cpp[NVC_MFCDocView#189](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]  
  
 Obsługa `WM_TIMER` w ten sposób umożliwi zwiększenie wydajności aplikacji, które używają czasomierze krótki.  
  
##  <a name="m_bautodelete"></a>CWinThread::m_bAutoDelete  
 Określa, czy `CWinThread` obiekt powinien zostać automatycznie usunięty na zakończenie wątku.  
  
```  
BOOL m_bAutoDelete;  
```  
  
### <a name="remarks"></a>Uwagi  
 `m_bAutoDelete` Elementu członkowskiego danych jest publiczny zmiennej typu **BOOL**.  
  
 Wartość `m_bAutoDelete` nie wpływa na sposób podstawowej dojście wątku jest zamknięty. Dojście wątku zawsze jest zamknięty kiedy `CWinThread` obiekt zostanie zniszczony.  
  
##  <a name="m_hthread"></a>CWinThread::m_hThread  
 Dojście do wątku dołączony do tego `CWinThread`.  
  
```  
HANDLE m_hThread;  
```  
  
### <a name="remarks"></a>Uwagi  
 `m_hThread` Elementu członkowskiego danych jest publiczny zmiennej typu `HANDLE`. Jest on prawidłowy tylko wtedy, jeśli podstawowy wątku obecnie istnieje.  
  
##  <a name="m_nthreadid"></a>CWinThread::m_nThreadID  
 Identyfikator wątku dołączony do tego `CWinThread`.  
  
```  
DWORD m_nThreadID;  
```  
  
### <a name="remarks"></a>Uwagi  
 **M_nThreadID** elementu członkowskiego danych jest publiczny zmiennej typu `DWORD`. Jest on prawidłowy tylko wtedy, jeśli podstawowy wątku obecnie istnieje.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [afxgetthread —](application-information-and-management.md#afxgetthread).  
  
##  <a name="m_pactivewnd"></a>CWinThread::m_pActiveWnd  
 Użyj tego elementu członkowskiego danych do przechowywania wskaźnik do obiektu aktywnego okna dla wątku.  
  
```  
CWnd* m_pActiveWnd;  
```  
  
### <a name="remarks"></a>Uwagi  
 Microsoft Foundation Class Library automatycznie z chwilą z wątku okna odwołuje się `m_pActiveWnd` jest zamknięty. Jeśli ten wątek jest podstawowym wątku dla aplikacji, aplikacja również zostanie zakończona. Jeśli ten element członkowski danych jest **NULL**, aktywnego okna aplikacji `CWinApp` obiektu będą dziedziczone. `m_pActiveWnd`jest publiczny zmiennej typu **CWnd\***.  
  
 Zazwyczaj wartość tej zmiennej członkowskiej Aby zastąpić `InitInstance`. W wątku roboczego wartość tego elementu członkowskiego danych jest dziedziczona z jej nadrzędną wątku.  
  
##  <a name="m_pmainwnd"></a>CWinThread::m_pMainWnd  
 Użyj tego elementu członkowskiego danych do przechowywania wskaźnik do obiektu głównego okna dla wątku.  
  
```  
CWnd* m_pMainWnd;  
```  
  
### <a name="remarks"></a>Uwagi  
 Microsoft Foundation Class Library automatycznie z chwilą z wątku okna odwołuje się `m_pMainWnd` jest zamknięty. Jeśli ten wątek jest podstawowym wątku dla aplikacji, aplikacja również zostanie zakończona. Jeśli ten element członkowski danych jest **NULL**, głównego okna aplikacji `CWinApp` obiektu będzie służyć do określenia, kiedy zakończenie wątku. `m_pMainWnd`jest publiczny zmiennej typu **CWnd\***.  
  
 Zazwyczaj wartość tej zmiennej członkowskiej Aby zastąpić `InitInstance`. W wątku roboczego wartość tego elementu członkowskiego danych jest dziedziczona z jej nadrzędną wątku.  
  
##  <a name="onidle"></a>CWinThread::OnIdle  
 Przesłonić tę funkcję elementu członkowskiego do przetwarzania czas bezczynności.  
  
```  
virtual BOOL OnIdle(LONG lCount);
```  
  
### <a name="parameters"></a>Parametry  
 `lCount`  
 Licznik zwiększany po każdej `OnIdle` jest wywoływane, gdy kolejka komunikatów wątku jest pusta. Ten licznik jest resetowany do 0 zawsze, gdy nowy komunikat jest przetwarzany. Można użyć `lCount` parametr, aby określić względną długość czasu bez przetwarzania komunikatu wątek był bezczynny.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, aby otrzymać więcej przetwarzania czas bezczynności; 0, jeśli już czas bezczynności przetwarzania nie jest konieczne.  
  
### <a name="remarks"></a>Uwagi  
 `OnIdle`jest wywoływana domyślną pętlę komunikatów, gdy kolejka komunikatów wątku jest pusta. Umożliwia wywołanie własnym zadania obsługi bezczynności zastąpienia.  
  
 `OnIdle`powinien zwracać wartość 0, aby wskazać, że nie dodatkowe bezczynności przetwarzania jest wymagane. `lCount` Parametru jest zwiększany po każdej `OnIdle` jest wywoływane, gdy kolejka komunikatów jest pusty i zostanie zresetowana do 0 zawsze nowy komunikat jest przetwarzany. Można wywołać z innej procedury bezczynności na podstawie tej liczby.  
  
 Domyślna implementacja funkcji członkowskiej zwalnia obiekty tymczasowe i biblioteki dołączanej nieużywane z pamięci.  
  
 Ta funkcja członkowska jest używana tylko wątków interfejsu użytkownika.  
  
 Ponieważ aplikacja nie może przetwarzać komunikatów do `OnIdle` zwraca, nie wykonuj długich zadań w tej funkcji.  
  
##  <a name="operator_handle"></a>CWinThread::operator dojścia  
 Pobiera dojście `CWinThread` obiektu.  
  
```  
operator HANDLE() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia dojście obiektu wątku. w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Użyj uchwytu do bezpośredniego wywoływania interfejsów API systemu Windows.  
  
##  <a name="postthreadmessage"></a>CWinThread::PostThreadMessage  
 O nazwie opublikowanie wiadomości zdefiniowane przez użytkownika do drugiego `CWinThread` obiektu.  
  
```  
BOOL PostThreadMessage(
    UINT message,  
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 `message`  
 Identyfikator komunikatu zdefiniowane przez użytkownika.  
  
 `wParam`  
 Pierwszy parametr wiadomości.  
  
 `lParam`  
 Drugi parametr wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Komunikatów oczekujących na opublikowanie jest mapowany na program obsługi komunikatów prawidłowego za pomocą makra mapy wiadomości `ON_THREAD_MESSAGE`.  
  
> [!NOTE]
>  Podczas wywoływania okna [PostThreadMessage](http://msdn.microsoft.com/library/windows/desktop/ms644946) funkcji w aplikacji MFC, nie są wywoływane programy obsługi wiadomości MFC. Aby uzyskać więcej informacji zobacz artykuł bazy wiedzy, "PRB: MFC wiadomości program obsługi nie wywołuje z PostThreadMessage()" (Q142415).  
  
##  <a name="pretranslatemessage"></a>CWinThread::PreTranslateMessage  
 Zastąpienie tej funkcji do filtrowania wiadomości okna przed wysłaniem do funkcji systemu Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) i [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934).  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parametry  
 `pMsg`  
 Wskazuje [struktura MSG](../../mfc/reference/msg-structure1.md) zawierający komunikat do przetworzenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli pełni przetworzonych komunikatów w `PreTranslateMessage` i nie powinno być dalej przetwarzane. Zero, jeśli komunikat powinien zostać przetworzony w zwykły sposób.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska jest używana tylko wątków interfejsu użytkownika.  
  
##  <a name="processmessagefilter"></a>CWinThread::ProcessMessageFilter  
 Funkcja framework wymaga funkcji członkowskiej filtrować i reagowanie na niektórych komunikatów systemu Windows.  
  
```  
virtual BOOL ProcessMessageFilter(
    int code,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>Parametry  
 `code`  
 Określa kod punktu zaczepienia. Ta funkcja członkowska kod używany do określenia sposobu przetwarzania`lpMsg.`  
  
 `lpMsg`  
 Wskaźnik do systemu Windows [struktura MSG](../../mfc/reference/msg-structure1.md).  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli komunikat jest przetwarzany; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja przetwarza zdarzenia przed ich wysłaniem do normalnego komunikatu aplikacji przetwarzania.  
  
 Jeśli możesz zastąpić to zaawansowana funkcja, należy wywołać wersji klasa podstawowa do obsługi platformy utworzenie punktu zaczepienia przetwarzania.  
  
##  <a name="processwndprocexception"></a>CWinThread::ProcessWndProcException  
 Struktura wywołuje funkcji członkowskiej, gdy program obsługi nie przechwytuje wyjątek w jednej wiadomości dla wątku lub programy obsługi poleceń.  
  
```  
virtual LRESULT ProcessWndProcException(
    CException* e,  
    const MSG* pMsg);
```  
  
### <a name="parameters"></a>Parametry  
 *e*  
 Wskazuje nieobsługiwany wyjątek.  
  
 `pMsg`  
 Wskazuje [struktura MSG](../../mfc/reference/msg-structure1.md) zawierający informacje o komunikatów systemu windows, który spowodował platformę, aby zgłosić wyjątek.  
  
### <a name="return-value"></a>Wartość zwracana  
 -1, gdy `WM_CREATE` wygenerowany wyjątek; w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Nie wywołuj tej funkcji Członkowskich bezpośrednio.  
  
 Domyślna implementacja funkcji członkowskiej obsługuje tylko wyjątki generowane z następujących komunikatów:  
  
|Polecenie|Akcja|  
|-------------|------------|  
|`WM_CREATE`|Zakończyć się niepowodzeniem.|  
|`WM_PAINT`|Sprawdź poprawność zmodyfikowanego okna, aby zapobiec innego `WM_PAINT` komunikat generowania.|  
  
 Przesłonić tę funkcję elementu członkowskiego, aby zapewnić obsługę globalnej listy wyjątków. Podstawowe funkcje należy wywołać tylko wtedy, gdy chcesz wyświetlić zachowanie domyślne.  
  
 Ta funkcja członkowska jest używana tylko wątków, które mają przekazywanie komunikatów.  
  
##  <a name="pumpmessage"></a>CWinThread::PumpMessage  
 Zawiera pętlę komunikatów wątku.  
  
```  
virtual BOOL PumpMessage();
```  
  
### <a name="remarks"></a>Uwagi  
 `PumpMessage`zawiera pętlę komunikatów wątku. **PumpMessage** jest wywoływana przez `CWinThread` do pompa wiadomości wątku. Możesz wywołać `PumpMessage` bezpośrednio do wymuszenia komunikaty do przetwarzania, lub można zastąpić `PumpMessage` Aby zmienić jego zachowanie domyślne.  
  
 Wywoływanie `PumpMessage` bezpośrednio i zastępowanie jego domyślne zachowanie jest zalecane tylko dla użytkowników zaawansowanych.  
  
##  <a name="resumethread"></a>CWinThread::ResumeThread  
 Wywołuje się, aby wznowić wykonywanie wątku, który został zawieszony przez [SuspendThread](#suspendthread) funkcji członkowskiej lub utworzone za pomocą wątku **CREATE_SUSPENDED** flagi.  
  
```  
DWORD ResumeThread();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wątek na poprzednim zawiesić liczba w przypadku powodzenia; `0xFFFFFFFF` inaczej. Jeśli wartość zwracana jest wartość zero, bieżący wątek nie zostało wstrzymane. Jeśli wartość zwracana, wątek został wstrzymany, ale teraz zostanie ponownie uruchomiony. Kreator nie wznawia większą niż co oznacza, że wątek wartości zwracanej.  
  
### <a name="remarks"></a>Uwagi  
 Liczba Wstrzymaj bieżącego wątku zostanie zmniejszona o jeden. W przypadku liczby wstrzymania od zera, wątek wznawia wykonywanie; w przeciwnym razie wątku pozostanie wstrzymany.  
  
##  <a name="run"></a>CWinThread::Run  
 Udostępnia domyślną pętlę komunikatów dla wątków interfejsu użytkownika.  
  
```  
virtual int Run();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `int` Wartość zwracana przez wątek. Ta wartość może być pobierane przez wywołanie [Funkcja GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190).  
  
### <a name="remarks"></a>Uwagi  
 **Uruchom** uzyskuje i wysyła komunikaty systemu Windows, do momentu otrzymania przez aplikację [WM_QUIT](http://msdn.microsoft.com/library/windows/desktop/ms632641) wiadomości. Jeśli kolejka komunikatów wątku zawiera obecnie żadne komunikaty **Uruchom** wywołania `OnIdle` do przetwarzania czas bezczynności. Wiadomości przychodzących, przejdź do [PreTranslateMessage](#pretranslatemessage) funkcji członkowskiej przetwarzania specjalnych funkcji systemu Windows, a następnie [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) translacji standardowej klawiatury. Na koniec [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) została wywołana funkcja systemu Windows.  
  
 **Uruchom** rzadko zostanie zastąpiona, ale można je zastąpić do zaimplementowania specjalnego zachowania.  
  
 Ta funkcja członkowska jest używana tylko wątków interfejsu użytkownika.  
  
##  <a name="setthreadpriority"></a>CWinThread::SetThreadPriority  
 Ta funkcja Ustawia priorytet bieżącego wątku w swojej klasie priorytet.  
  
```  
BOOL SetThreadPriority(int nPriority);
```  
  
### <a name="parameters"></a>Parametry  
 `nPriority`  
 Określa nowy poziom priorytetu wątku w swojej klasie priorytet. Ten parametr musi być jedną z następujących wartości na liście z najwyższym priorytetem do najniższego:  
  
- **THREAD_PRIORITY_TIME_CRITICAL**  
  
- **THREAD_PRIORITY_HIGHEST**  
  
- **THREAD_PRIORITY_ABOVE_NORMAL**  
  
- **THREAD_PRIORITY_NORMAL**  
  
- **THREAD_PRIORITY_BELOW_NORMAL**  
  
- **THREAD_PRIORITY_LOWEST**  
  
- **THREAD_PRIORITY_IDLE**  
  
 Aby uzyskać więcej informacji o tych priorytetów, zobacz [wykonanie funkcji SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) w zestawie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończyło się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Można go wywołać jedynie po [CreateThread](#createthread) zwraca pomyślnie.  
  
##  <a name="suspendthread"></a>CWinThread::SuspendThread  
 Zwiększa bieżącego wątku zawiesić count.  
  
```  
DWORD SuspendThread();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wątek na poprzednim zawiesić liczba w przypadku powodzenia; `0xFFFFFFFF` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli którymkolwiek wątku ma liczbę Wstrzymaj powyżej wartości zero, nie wykonuj tego wątku. Wątek można wznowić, wywołując [ResumeThread](#resumethread) funkcję elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [CCmdTarget — klasa](../../mfc/reference/ccmdtarget-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cwinapp — klasa](../../mfc/reference/cwinapp-class.md)   
 [Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)
