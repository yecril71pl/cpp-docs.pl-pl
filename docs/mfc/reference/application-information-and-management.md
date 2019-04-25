---
title: Informacje o aplikacji i zarządzanie nią
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
ms.openlocfilehash: 78b9ae467d3504f3922c540a3e4cd100322d8f4e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151285"
---
# <a name="application-information-and-management"></a>Informacje o aplikacji i zarządzanie nią

Podczas pisania aplikacji, Utwórz jeden [CWinApp](../../mfc/reference/cwinapp-class.md)-pochodnych obiektu. Czasami możesz chcieć uzyskać informacje na temat tego obiektu wynikające ze poza `CWinApp`-pochodnych obiektu. Lub może być wymagany dostęp do innych obiektów globalnych "Manager".

Biblioteki klas Microsoft Foundation udostępnia następujące funkcje globalne, które ułatwiają wykonanie tych zadań:

### <a name="application-information-and-management-functions"></a>Informacje o aplikacji i funkcji zarządzania

|||
|-|-|
|[AfxBeginThread](#afxbeginthread)|Tworzy nowy wątek.|
|[AfxContextMenuManager](#afxcontextmenumanager)|Wskaźnik do globalnego [Menedżera menu kontekstowe](ccontextmenumanager-class.md).|
|[AfxEndThread](#afxendthread)|Kończy działanie bieżącego wątku.|
|[AfxFindResourceHandle](#afxfindresourcehandle)|Zawiera łańcuch zasobów, a następnie zlokalizuj identyfikator zasobu, zasób i typu zasobu. |
|[AfxFreeLibrary](#afxfreelibrary)|Dekrementuje liczbę odwołań modułu załadować biblioteki dołączanej (dynamicznie DLL); Gdy licznik odwołań osiągnie zero, moduł jest niezamapowany.|
|[AfxGetApp](#afxgetapp)|Zwraca wskaźnik do aplikacji przez jednego `CWinApp` obiektu.|
|[AfxGetAppName](#afxgetappname)|Zwraca ciąg zawierający nazwę aplikacji.|
|[AfxGetInstanceHandle](#afxgetinstancehandle)|Zwraca HINSTANCE, reprezentujące tego wystąpienia aplikacji.|
|[AfxGetMainWnd](#afxgetmainwnd)|Zwraca wskaźnik do bieżącego okna "główny" aplikacji innych niż OLE lub okno ramowe w miejscu aplikacji serwera.|
|[AfxGetPerUserRegistration](#afxgetperuserregistration)|Ta funkcja służy do określenia, czy aplikacja przekierowuje dostęp do rejestru **HKEY_CURRENT_USER** ( **HKCU**) węzła.|
|[AfxGetResourceHandle](#afxgetresourcehandle)|Zwraca HINSTANCE źródłem zasoby domyślne aplikacji. Umożliwia bezpośredni dostęp do zasobów aplikacji.|
|[AfxGetThread](#afxgetthread)|Pobiera wskaźnik do bieżącego [CWinThread](../../mfc/reference/cwinthread-class.md) obiektu.|
|[AfxInitRichEdit](#afxinitrichedit)|Inicjuje w wersji 1.0 tekstu sformatowanego sterowania dla aplikacji.|
|[AfxInitRichEdit2](#afxinitrichedit2)|Inicjuje w wersji 2.0 i nowsze wersje kontrolki tekstu sformatowanego sterowania dla aplikacji.|
|[AfxIsExtendedFrameClass](#afxisextendedframeclass)|Określa, czy dany okna jest obiekt w ramce rozszerzonej.|
|[Afxismfctoolbar —](#afxismfctoolbar)|Określa, czy dany okna jest obiekt paska narzędzi.|
|[AfxKeyboardManager](#afxkeyboardmanager)|Wskaźnik do globalnego [Menedżera klawiatury](ckeyboardmanager-class.md).|
|[AfxLoadLibrary](#afxloadlibrary)|Mapuje modułu DLL i zwraca uchwyt, który może służyć w celu uzyskania adresu funkcji DLL.|
|[AfxMenuTearOffManager](#afxmenutearoffmanager)|Wskaźnik do globalnego [Menedżera menu odrywania](cmenutearoffmanager-class.md).|
|[AfxMouseManager](#afxmousemanager)|Wskaźnik do globalnego [Menedżera myszy](cmousemanager-class.md).|
|[AfxRegisterClass](#afxregisterclass)|Rejestruje klasę okna w bibliotece DLL, która używa biblioteki MFC.|
|[AfxRegisterWndClass](#afxregisterwndclass)|Rejestruje klasę okna Windows, aby uzupełnić te automatycznie zarejestrować przez MFC.|
|[AfxSetPerUserRegistration](#afxsetperuserregistration)|Określa, czy aplikacja przekierowuje dostęp do rejestru **HKEY_CURRENT_USER** ( **HKCU**) węzła.|
|[AfxSetResourceHandle](#afxsetresourcehandle)|Ustawia uchwyt HINSTANCE załadunku domyślnych zasobów aplikacji.|
|[AfxShellManager](#afxshellmanager)|Wskaźnik do globalnego [Menedżera powłoki](cshellmanager-class.md). |
|[AfxSocketInit](#afxsocketinit)|Wywoływane w `CWinApp::InitInstance` należy przesłonić, aby zainicjować Windows Sockets.|
|[AfxUserToolsManager](#afxusertoolsmanager)|Wskaźnik do globalnego [Menedżera narzędzi](cusertoolsmanager-class.md).|
|[AfxWinInit](#afxwininit)|Wywoływane przez podany MFC `WinMain` funkcji jako część [CWinApp](../../mfc/reference/cwinapp-class.md) inicjowania aplikacji Graficznym interfejsem użytkownika, można zainicjować biblioteki MFC. Musi być wywoływana bezpośrednio do aplikacji konsoli, które używają MFC.|

##  <a name="afxbeginthread"></a>  AfxBeginThread

Wywołaj tę funkcję, aby utworzyć nowy wątek.

```
CWinThread* AfxBeginThread(
    AFX_THREADPROC pfnThreadProc,
    LPVOID pParam,
    int nPriority = THREAD_PRIORITY_NORMAL,
    UINT nStackSize = 0,
    DWORD dwCreateFlags = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);

CWinThread* AfxBeginThread(
    CRuntimeClass* pThreadClass,
    int nPriority = THREAD_PRIORITY_NORMAL,
    UINT nStackSize = 0,
    DWORD dwCreateFlags = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```

### <a name="parameters"></a>Parametry

*pfnThreadProc*<br/>
Wskazuje funkcje kontroli wątku roboczego. Nie może mieć wartości NULL. Ta funkcja musi być zadeklarowana w następujący sposób:

`UINT __cdecl MyControllingFunction( LPVOID pParam );`

*pThreadClass*<br/>
RUNTIME_CLASS obiektu pochodną [CWinThread](../../mfc/reference/cwinthread-class.md).

*pParam*<br/>
Parametr do przekazania do funkcji kontroli zgodnie z informacjami w parametrze do deklaracji funkcji w *pfnThreadProc*.

*nPriority*<br/>
Żądany priorytet wątku. Aby uzyskać pełną listę i opis dostępnych priorytetów, zobacz [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) w zestawie Windows SDK.

*nStackSize*<br/>
Określa rozmiar w bajtach stosu dla nowego wątku. Jeśli jest to 0, rozmiar stosu domyślnie taki sam jak rozmiar stosu wątku tworzącego.

*dwCreateFlags*<br/>
Określa dodatkowy znacznik, który steruje tworzeniem wątku. Ta flaga może zawierać jedną z dwóch wartości:

- CREATE_SUSPENDED zaczynać wątek wstrzymania liczenia jedengo. Użyj CREATE_SUSPENDED, jeśli chcesz inicjalizować dane z `CWinThread` obiektów, takich jak [m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete) lub wszystkie elementy członkowskie swojej otrzymanej klasy, zanim uruchamiania wątku. Po zakończeniu inicjalizacji, użyj [CWinThread::ResumeThread](../../mfc/reference/cwinthread-class.md#resumethread) można uruchomić wątek systemu. Wątek nie zostanie wykonany dopóki `CWinThread::ResumeThread` jest wywoływana.

- **0** uruchomić wątku od razu po utworzeniu.

*lpSecurityAttrs*<br/>
Wskazuje [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) strukturę, która określa atrybuty zabezpieczeń dla wątku. Jeśli ma wartość NULL, będą używane te same atrybuty zabezpieczeń jako wątku tworzącego. Aby uzyskać więcej informacji na temat tej struktury zobacz zestaw Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzony obiekt wątku lub wartość NULL, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Pierwszy formularz `AfxBeginThread` tworzy wątek roboczy. Druga forma tworzy wątek, który może funkcjonować jako wątek interfejsu użytkownika lub Wątek roboczy.

`AfxBeginThread` Tworzy nową `CWinThread` obiektu, wywołuje jego [CreateThread](../../mfc/reference/cwinthread-class.md#createthread) funkcji, aby rozpocząć wykonywanie wątku i zwraca wskaźnik do wątku. Kontrole są wprowadzane w trakcie trwania procedury upewnij się, że wszystkie obiekty są zdelokowane poprawnie w przypadku dowolnej części tworzenia nie. Aby zakończyć wątek, wywołaj [AfxEndThread](#afxendthread) z w ramach wątku lub zwróć z funkcji kontroli wątku roboczego.

Wielowątkowość musi być włączona przez aplikację; w przeciwnym wypadku funkcja zakończy się niepowodzeniem. Aby uzyskać więcej informacji na temat włączania wielowątkowości, zobacz [/ / MD, / MT, /LD (Korzystaj z bibliotek wykonawczych)](../../build/reference/md-mt-ld-use-run-time-library.md) w obszarze *opcjach kompilatora Visual C++*.

Aby uzyskać więcej informacji na temat `AfxBeginThread`, zobacz artykuły [wielowątkowość: Tworzenie wątków roboczych](../../parallel/multithreading-creating-worker-threads.md) i [wielowątkowość: Tworzenie wątków interfejsu użytkownika](../../parallel/multithreading-creating-user-interface-threads.md).

### <a name="example"></a>Przykład

Zobacz przykład [CSocket::Dołącz](../../mfc/reference/csocket-class.md#attach).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

## <a name="afxcontextmenumanager"></a> Afxcontextmenumanager —

Wskaźnik do globalnego [Menedżera menu kontekstowe](ccontextmenumanager-class.md).

### <a name="syntax"></a>Składnia

```
CContextMenuManager* afxContextMenuManager;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxcontextmenumanager.h

##  <a name="afxendthread"></a>  AfxEndThread

Wywołaj tę funkcję, aby zakończyć aktualnie wykonywany wątek.

```
void AFXAPI AfxEndThread(
    UINT nExitCode,
    BOOL bDelete  = TRUE);
```

### <a name="parameters"></a>Parametry

*nExitCode*<br/>
Określa kod wyjścia wątku.

*bDelete*<br/>
Usuwa obiekt ciągu z pamięci.

### <a name="remarks"></a>Uwagi

Musi być wywołana z wewnątrz wątku, który ma zostać zakończony.

Aby uzyskać więcej informacji na temat `AfxEndThread`, zapoznaj się z artykułem [wielowątkowość: Przerywanie wątków](../../parallel/multithreading-terminating-threads.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

  ## <a name="afxfindresourcehandle"></a>AfxFindResourceHandle
Użyj `AfxFindResourceHandle` zapoznaj się z łańcucha zasobów i zlokalizować określonego zasobu, identyfikator i zasobów typu zasobu.

### <a name="syntax"></a>Składnia

```
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Wskaźnik do ciągu zawierającego identyfikator zasobu.
*lpszType*<br/>
Wskaźnik do typu zasobu. Aby uzyskać listę typów zasobów, zobacz [FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Dojście do modułu, który zawiera zasób.

### <a name="remarks"></a>Uwagi

`AfxFindResourceHandle` Wyszukuje określonego zasobu i zwraca uchwyt do modułu, który zawiera zasób. Zasób może być w dowolnym rozszerzeń MFC DLL, które zostały załadowane. `AfxFindResourceHandle` informuje, który z nich ma zasobu.

Moduły są przeszukiwane w następującej kolejności:

1. Moduł główny (jeśli jest to biblioteka DLL rozszerzenia MFC).

1. Inne niż system modułów.

1. Moduły specyficzne dla języka.

1. Moduł główny (jeśli jest systemowej biblioteki DLL).

1. Moduły systemu.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="afxfreelibrary"></a>  AfxFreeLibrary

Zarówno `AfxFreeLibrary` i `AfxLoadLibrary` Obsługa licznika odwołań dla każdego modułu załadować biblioteki.

```
BOOL AFXAPI AfxFreeLibrary(HINSTANCE hInstLib);
```

### <a name="parameters"></a>Parametry

*hInstLib*<br/>
Uchwyt modułu załadować biblioteki. [AfxLoadLibrary](#afxloadlibrary) zwraca tego uchwytu.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli funkcja się powiedzie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

`AfxFreeLibrary` Dekrementuje liczbę odwołań modułu załadować biblioteki dołączanej (dynamicznie DLL). Gdy licznik odwołań osiągnie zero, moduł jest niezamapowany przestrzeni adresowej procesu wywołującego, a uchwyt nie jest już prawidłowy. Ten licznik odwołań rośnie każdorazowo `AfxLoadLibrary` jest wywoływana.

Przed usuwania mapowania modułu biblioteki, system umożliwia DLL można odłączyć od procesów korzystania z niego. To daje możliwość wyczyścić zasoby przydzielone w imieniu bieżący proces biblioteki DLL. Po powrocie funkcję punktu wejścia, moduł biblioteki jest usuwany z przestrzeni adresowej bieżącego procesu.

Użyj `AfxLoadLibrary` do mapowania modułu biblioteki DLL.

Należy użyć `AfxFreeLibrary` i `AfxLoadLibrary` (zamiast funkcji Win32 `FreeLibrary` i `LoadLibrary`) Jeśli aplikacja korzysta z wielu wątków. Za pomocą `AfxLoadLibrary` i `AfxFreeLibrary` zapewnia, że kod uruchamiania i zamykania, który wykonuje, gdy rozszerzenia MFC biblioteki DLL jest ładowany i zwolnione nie doprowadzić do uszkodzenia globalne MFC.

### <a name="example"></a>Przykład

Zobacz przykład [AfxLoadLibrary](#afxloadlibrary).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdll_.h

##  <a name="afxgetapp"></a>  AfxGetApp

Wskaźnik zwracany przez tę funkcję może służyć do dostępu do aplikacji informacje, takie jak kod głównego wysyłania komunikatu lub w oknie najwyższego poziomu.

```
CWinApp* AFXAPI AfxGetApp();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do jednego `CWinApp` obiektu dla aplikacji.

### <a name="remarks"></a>Uwagi

Jeśli ta metoda zwraca wartość NULL, może to oznaczać, że okno główne aplikacji nie został w pełni zainicjowany jeszcze. Ponadto może to wskazywać na problem.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#126](../../mfc/reference/codesnippet/cpp/application-information-and-management_1.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

##  <a name="afxgetappname"></a>  AfxGetAppName

Ciągu zwracanego przez tę funkcję może służyć jako główny lub komunikaty diagnostyczne dla tymczasowych ciągów nazwy.

```
LPCTSTR AFXAPI AfxGetAppName();
```

### <a name="return-value"></a>Wartość zwracana

Ciąg zakończony wartością null zawierający nazwę aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#127](../../mfc/reference/codesnippet/cpp/application-information-and-management_2.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

##  <a name="afxgetinstancehandle"></a>  AfxGetInstanceHandle

Ta funkcja pozwala pobrać dojście wystąpienia w bieżącej aplikacji.

```
HINSTANCE  AFXAPI AfxGetInstanceHandle();
```

### <a name="return-value"></a>Wartość zwracana

HINSTANCE do bieżącego wystąpienia aplikacji. Jeśli wywołane z wnętrza biblioteki DLL połączone z wersją USRDLL MFC, zwracany jest HINSTANCE do biblioteki DLL.

### <a name="remarks"></a>Uwagi

`AfxGetInstanceHandle` zawsze zwraca HINSTANCE pliku wykonywalnego (. Z rozszerzeniem EXE), chyba że jest ona wywoływana z poziomu biblioteki DLL połączone z wersją USRDLL MFC. W takim przypadku zwraca HINSTANCE, do biblioteki DLL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

##  <a name="afxgetmainwnd"></a>  Afxgetmainwnd —

Jeśli aplikacja serwera OLE, należy wywołać tę funkcję, aby pobrać wskaźnik do aktywnego okna głównego aplikacji, a nie bezpośrednio odnoszące się do [elementu m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd) elementu członkowskiego obiektu aplikacji.

```
CWnd* AFXAPI AfxGetMainWnd();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli serwer ma obiekt, który jest w miejscu aktywny wewnątrz kontenera, a ten kontener jest aktywny, ta funkcja zwraca wskaźnik do obiektu okna ramki, który zawiera aktywnego dokumentu w miejscu.

Jeśli nie ma żadnego obiektu, który jest aktywny w miejscu, w ramach kontenera lub aplikacja nie jest serwerem OLE, ta funkcja po prostu zwraca *elementu m_pMainWnd* obiektu aplikacji.

Jeśli `AfxGetMainWnd` jest wywoływana z wątku głównego aplikacji, funkcja zwraca okna głównego aplikacji, zgodnie z powyższymi zasadami. Jeśli funkcja jest wywoływana z wątek pomocniczy w aplikacji, funkcja zwraca okno główne skojarzonych z wątkiem, który zgłosił wywołania.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja nie jest serwerem OLE, a następnie wywołaniu tej funkcji jest odpowiednikiem bezpośrednio odnoszące się do *elementu m_pMainWnd* elementu członkowskiego obiektu aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#129](../../mfc/reference/codesnippet/cpp/application-information-and-management_4.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

##  <a name="afxgetperuserregistration"></a>  AfxGetPerUserRegistration

Ta funkcja służy do określenia, czy aplikacja przekierowuje dostęp do rejestru **HKEY_CURRENT_USER** ( **HKCU**) węzła.

```
BOOL AFXAPI AfxGetPerUserRegistration();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE wskazuje, że informacje rejestru zostaje skierowany do węzła HKCU; Wartość FALSE wskazuje, że aplikacja zapisze informacje rejestru do węzła domyślnego. Węzeł domyślny jest **HKEY_CLASSES_ROOT** ( **HKCR**).

### <a name="remarks"></a>Uwagi

Jeśli zostanie włączone przekierowanie do rejestru, struktura przekierowuje dostęp z **HKCR** do **HKEY_CURRENT_USER\Software\Classes**. Dotyczy tylko struktury MFC i ATL przekierowania.

Aby określić, czy aplikacja przekierowuje dostęp do rejestru, należy użyć [afxsetperuserregistration —](#afxsetperuserregistration).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxstat_.h

##  <a name="afxgetresourcehandle"></a>  AfxGetResourceHandle

Użyj obsługi HINSTANCE zwracane przez tę funkcję, aby uzyskać dostęp do zasobów aplikacji bezpośrednio, na przykład w wywołaniach Windows funkcji `FindResource`.

```
extern HINSTANCE  AfxGetResourceHandle();
```

### <a name="return-value"></a>Wartość zwracana

Dojście HINSTANCE, w których domyślne zasoby aplikacji są ładowane.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

##  <a name="afxgetthread"></a>  AfxGetThread

Wywołaj tę funkcję, aby uzyskać wskaźnik do [CWinThread](../../mfc/reference/cwinthread-class.md) obiekt reprezentujący aktualnie wykonywany wątek.

```
CWinThread* AfxGetThread();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do aktualnie wykonywany wątek; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Musi być wywołana z wewnątrz wątku żądaną.

> [!NOTE]
>  Jeśli są przenoszenie wywoływania projektu MFC `AfxGetThread` od wersji Visual C++ 4.2, 5.0 lub 6.0, `AfxGetThread` wywołania [afxgetapp —](#afxgetapp) Jeśli żaden wątek nie zostanie znaleziony. W nowszych wersjach kompilatora `AfxGetThread` zwraca wartość NULL, jeśli żaden wątek nie został znaleziony. Jeśli chcesz, aby wątek aplikacji, należy wywołać `AfxGetApp`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

##  <a name="afxinitrichedit"></a>  Afxinitrichedit —

Wywołaj tę funkcję, aby zainicjować kontrolki edycji wzbogaconej (w wersji 1.0) dla aplikacji.

```
BOOL AFXAPI AfxInitRichEdit();
```

### <a name="remarks"></a>Uwagi

Ta funkcja zapewnia zgodności z poprzednimi wersjami. Nowe aplikacje powinny używać [afxinitrichedit2 —](#afxinitrichedit2).

`AfxInitRichEdit` ładuje RICHED32. Biblioteki DLL do zainicjowania rozwiniętej kontroli edycji w wersji 1.0. Do korzystania z wersji 2.0 i 3.0 kontrolki edycji wzbogaconej, RICHED20. Biblioteki DLL muszą zostać załadowane. Jest to realizowane przy wywołaniu [afxinitrichedit2 —](#afxinitrichedit2).

Aby zaktualizować formantów edycji wzbogaconej w istniejących aplikacji Visual C++ w wersji 2.0, Otwórz. Plik RC jako tekst, zmienić nazwę klasy każdego formantu bogatej edycji z "RICHEDIT" do "RichEdit20a". Następnie zastąp wywołanie `AfxInitRichEdit` z `AfxInitRichEdit2`.

Ta funkcja inicjuje również biblioteki formantów wspólnych, jeśli biblioteka nie zainicjowano już dla procesu. Jeśli używasz kontrolki edycji wzbogaconej bezpośrednio z aplikacji MFC, należy wywołać tę funkcję, aby zapewnić MFC prawidłowo zainicjuje środowisko wykonawcze formantu bogatej edycji. Jeśli wywołanie metody tworzenia [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md), lub [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), zazwyczaj nie trzeba wywołać tę funkcję, ale w niektórych przypadkach może być wymagane.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

##  <a name="afxinitrichedit2"></a>  AfxInitRichEdit2

Wywołaj tę funkcję, aby zainicjować kontrolki edycji wzbogaconej (w wersji 2.0 lub nowszej) dla aplikacji.

```
BOOL AFXAPI AfxInitRichEdit2();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby załadować RICHED20. Biblioteki DLL i zainicjować wersji 2.0 zaawansowanych edytować formantu. Jeśli wywołanie metody tworzenia [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md), lub [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), zazwyczaj nie trzeba wywołać tę funkcję, ale w niektórych przypadkach może być wymagane.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

  ## <a name="afxisextendedframeclass"></a>  Afxisextendedframeclass —
Określa, czy dany okna jest obiekt w ramce rozszerzonej.

### <a name="syntax"></a>Składnia

```
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[in] Wskaźnik do obiektu, który jest tworzony na podstawie `CWnd`.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli podana okno jest obiekt w ramce rozszerzone; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość TRUE, jeśli *pWnd* pochodzi z jednej z następujących klas:

- `CFrameWndEx`

- `CMDIFrameWndEx`

- `COleIPFrameWndEx`

- `COleDocIPFrameWndEx`

- `CMDIChildWndEx`

Ta metoda jest przydatna, gdy konieczne jest sprawdzenie, czy parametr funkcji lub metody jest rozszerzona ramki okna.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxpriv.h

## <a name="afxismfctoolbar"></a> Afxismfctoolbar —

Określa, czy dany okna jest obiekt paska narzędzi.

### <a name="syntax"></a>Składnia

```
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[in] Wskaźnik do obiektu, który jest tworzony na podstawie `CWnd`.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli podana okna jest obiektem paska narzędzi w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca `TRUE` Jeśli *pWnd* pochodzi od klasy `CMFCToolBar`. Ta metoda jest przydatna, gdy należy zweryfikować, że parametr funkcji lub metody jest `CMFCToolBar` obiektu.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxpriv.h

## <a name="afxkeyboardmanager"></a> AfxKeyboardManager

Wskaźnik do globalnego [Menedżera klawiatury](ckeyboardmanager-class.md).

### <a name="syntax"></a>Składnia

```
CKeyboardManager* afxKeyboardManager;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxkeyboardmanager.h

##  <a name="afxloadlibrary"></a>  AfxLoadLibrary

Użyj `AfxLoadLibrary` do mapowania modułu biblioteki DLL.

```
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName);
```

### <a name="parameters"></a>Parametry

*lpszModuleName*<br/>
Wskazuje ciąg zakończony znakiem null, która zawiera nazwę modułu (albo. Biblioteki DLL lub. Plik EXE). Podana nazwa jest nazwą pliku modułu.

Jeśli ciąg Określa ścieżkę, ale plik nie istnieje w określonym katalogu, funkcja kończy się niepowodzeniem.

Jeśli ścieżka nie zostanie określona, a rozszerzenie nazwy pliku jest pominięty, domyślnym rozszerzeniem. Biblioteka DLL jest dołączany. Jednak ciągu nazwy pliku może zawierać końcowy znak punktu (.) do wskazania, że nazwa modułu nie ma rozszerzenia. Ścieżka nie zostanie określona, funkcja wyszukuje plik w następującej kolejności:

- Katalog, z którego aplikacja jest ładowany.

- Bieżący katalog.

- **Windows 95/98:** Katalog systemu Windows. **Windows NT:** Katalog systemu Windows 32-bitowych. Nazwa katalogu jest SYSTEM32.

- **Tylko Windows NT:** Katalog systemu Windows 16-bitowych. Brak żadnej funkcji Win32, który uzyskuje ścieżki tego katalogu, ale przeszukiwany jest. Nazwa katalogu jest systemu.

- Katalog Windows.

- Katalogi, które są wymienione w zmiennej środowiskowej PATH.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana jest dojścia do modułu. Jeśli funkcja zawiedzie, wartość zwracana jest wartość NULL.

### <a name="remarks"></a>Uwagi

Zwraca uchwyt, który może służyć w [GetProcAddress](/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress) można pobrać adresu funkcji DLL. `AfxLoadLibrary` można również mapować inne moduły pliku wykonywalnego.

Każdy proces przechowuje licznik odwołań dla każdego modułu załadować biblioteki. Ten licznik odwołań rośnie każdorazowo `AfxLoadLibrary` nosi nazwę i jest zmniejszana każdorazowo `AfxFreeLibrary` jest wywoływana. Gdy licznik odwołań osiągnie zero, moduł jest niezamapowany przestrzeni adresowej procesu wywołującego, a uchwyt nie jest już prawidłowy.

Należy użyć `AfxLoadLibrary` i `AfxFreeLibrary` (zamiast funkcji Win32 `LoadLibrary` i `FreeLibrary`) Jeśli aplikacja korzysta z wielu wątków i dynamicznie ładuje rozszerzenia MFC biblioteki DLL. Za pomocą `AfxLoadLibrary` i `AfxFreeLibrary` ubezpieczycielom, uruchamiania i zamykania kod, który wykonuje, gdy rozszerzenia MFC biblioteki DLL jest ładowany i zwolnione nie doprowadzić do uszkodzenia globalne MFC.

Za pomocą `AfxLoadLibrary` w aplikacji wymaga dynamicznie połączyć wersja dll biblioteki MFC; plik nagłówkowy `AfxLoadLibrary`, Afxdll_.h, jest tylko uwzględniony Jeżeli MFC jest połączony z aplikacji jako biblioteki DLL. To jest celowe, ponieważ trzeba połączyć wersja dll biblioteki MFC, aby użyć lub utworzyć biblioteki DLL rozszerzeń MFC.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_DLLUser#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]
[!code-cpp[NVC_MFC_DLLUser#2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]
[!code-cpp[NVC_MFC_DLLUser#3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdll_.h

## <a name="afxmenutearoffmanager"></a> Afxmenutearoffmanager —

Wskaźnik do globalnego [Menedżera menu odrywania](cmenutearoffmanager-class.md).

### <a name="syntax"></a>Składnia

```
CMenuTearOffManager* g_pTearOffMenuManager;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmenutearoffmanager.h

## <a name="afxmousemanager"></a>  Afxmousemanager —

Wskaźnik do globalnego [Menedżera myszy](cmousemanager-class.md).

### <a name="syntax"></a>Składnia

```
CMouseManager* afxMouseManager;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmousemanager.h

##  <a name="afxregisterclass"></a>  AfxRegisterClass

Ta funkcja umożliwia rejestrowanie klas okien w bibliotece DLL, która używa biblioteki MFC.

```
BOOL AFXAPI AfxRegisterClass(WNDCLASS* lpWndClass);
```

### <a name="parameters"></a>Parametry

*lpWndClass*<br/>
Wskaźnik do [WNDCLASS](/windows/desktop/api/winuser/ns-winuser-tagwndclassa) struktury zawierający informacje na temat klasy okna do zarejestrowania. Aby uzyskać więcej informacji na temat tej struktury zobacz zestaw Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli klasa zostanie pomyślnie zarejestrowana; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Funkcja ta klasa jest automatycznie wyrejestrowana podczas biblioteki DLL jest zwalniana.

W kompilacjach-DLL `AfxRegisterClass` identyfikator nie został zdefiniowany jako makro, który jest mapowany do funkcji Windows `RegisterClass`, ponieważ klasy zarejestrowanego w aplikacji są automatycznie wyrejestrowana. Jeśli używasz `AfxRegisterClass` zamiast `RegisterClass`, kod można używać bez zmian w aplikacji i w bibliotece DLL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_DLL#3](../../atl-mfc-shared/codesnippet/cpp/application-information-and-management_10.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

##  <a name="afxregisterwndclass"></a>  AfxRegisterWndClass

Umożliwia rejestrowanie własnych klas okien.

```
LPCTSTR AFXAPI AfxRegisterWndClass(
    UINT nClassStyle,
    HCURSOR hCursor = 0,
    HBRUSH hbrBackground = 0,
    HICON hIcon = 0);
```

### <a name="parameters"></a>Parametry

*nClassStyle*<br/>
Określa styl klasy Windows lub kombinacji style, utworzone za pomocą bitowej OR ( **&#124;**) — operator dla klasy okna. Aby uzyskać listę style klasy, zobacz [WNDCLASS](/windows/desktop/api/winuser/ns-winuser-tagwndclassa) struktury w zestawie Windows SDK. Jeśli ma wartość NULL, wartości domyślne będzie można ustawić w następujący sposób:

- Ustawia styl myszy CS_DBLCLKS, które wysyła kliknij dwukrotnie wiadomości do procedury okna, gdy użytkownik kliknie dwukrotnie myszy.

- Ustawia styl kursora strzałki IDC_ARROW standardowa Windows.

- Ustawia pędzel tła na wartość NULL, więc okna nie spowoduje to wymazanie tłem.

- Ustawia ikonę ikona logo Windows standard, którzy wymachują flagi.

*hCursor*<br/>
Określa dojście do zasobu kursora do zainstalowania w każdym oknie utworzone na podstawie klasy okna. Jeśli używasz domyślnego **0**, zostanie wyświetlony standardowy kursora IDC_ARROW.

*hbrBackground*<br/>
Określa dojście do zasobu pędzla, który ma być zainstalowany w każde okno utworzone na podstawie klasy okna. Jeśli używasz domyślnego **0**, będzie miał wartość NULL pędzel tła i okna domyślnie usunie tłem podczas przetwarzania [WM_ERASEBKGND](/windows/desktop/winmsg/wm-erasebkgnd).

*hIcon*<br/>
Określa dojście do zasobu ikony, która ma być zainstalowany w każde okno utworzone na podstawie klasy okna. Jeśli używasz domyślnego **0**, zostanie wyświetlony standardowy, którzy wymachują flagi ikona logo Windows.

### <a name="return-value"></a>Wartość zwracana

Ciąg zakończony wartością null zawierający nazwę klasy. Można przekazać tę nazwę klasy, aby `Create` funkcji składowej we `CWnd` lub innych **CWnd —** pochodne klasy można utworzyć okna. Nazwa jest generowana przez bibliotekę Microsoft Foundation Class.

> [!NOTE]
>  Wartość zwracana jest wskaźnik do buforu statyczne. Aby zapisać ten ciąg, Przypisz ją do `CString` zmiennej.

### <a name="remarks"></a>Uwagi

Biblioteki klas Microsoft Foundation automatycznie rejestruje kilka klas standardowego okna. Wywołaj tę funkcję, jeśli chcesz zarejestrować własne klasy okna.

Ta nazwa jest zarejestrowana dla klasy przez `AfxRegisterWndClass` zależy wyłącznie od parametrów. Jeśli wywołasz `AfxRegisterWndClass` wiele razy z identycznymi parametrami tylko rejestruje klasę przy pierwszym wywołaniu. Kolejne wywołania `AfxRegisterWndClass` z identycznymi parametrami po prostu zwrócenia classname już zarejestrowany.

Jeśli wywołasz `AfxRegisterWndClass` dla wielu klas pochodnych CWnd z identycznymi parametrami zamiast klasy oddzielne okno dla każdej klasy, każda klasa udostępnia tej samej klasy okna. Może to spowodować problemy, jeśli CS_CLASSDC stylu klasy jest używany. Zamiast wielu klas okna CS_CLASSDC na końcu jedną klasę okna CS_CLASSDC i wszystkie C++ tego samego kontrolera domeny Udostępnianie systemu windows, które używają tej klasy. Aby uniknąć tego problemu, należy wywołać [afxregisterclass —](#afxregisterclass) można zarejestrować klasy.

Zapoznaj się Uwaga techniczna [TN001: Rejestrowanie klasy okna](../../mfc/tn001-window-class-registration.md) więcej informacji na temat rejestrowanie klasy okna i `AfxRegisterWndClass` funkcji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

##  <a name="afxsetperuserregistration"></a>  AfxSetPerUserRegistration

Określa, czy aplikacja przekierowuje dostęp do rejestru **HKEY_CURRENT_USER** ( **HKCU**) węzła.

```
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bWłączenie*<br/>
[in] Wartość TRUE wskazuje, że informacje rejestru zostaje skierowany do węzła HKCU; Wartość FALSE wskazuje, że aplikacja zapisze informacje rejestru do węzła domyślnego. Węzeł domyślny jest **HKEY_CLASSES_ROOT** ( **HKCR**).

### <a name="remarks"></a>Uwagi

Przed Windows Vista, aplikacje, które uzyskać dostępu do rejestru, zwykle używane **HKEY_CLASSES_ROOT** węzła. Jednak przy użyciu Windows Vista lub nowszych systemach operacyjnych, należy uruchomić aplikację w trybie podniesionych uprawnień do zapisu do klucza HKCR.

Ta metoda pozwala aplikacji na odczytywanie i zapisywanie do rejestru, bez konieczności uruchamiania w trybie podniesionych uprawnień, przekierowując dostęp z HKCR do rejestru HKCU. Aby uzyskać więcej informacji, zobacz [strony właściwości konsolidatora](../../build/reference/linker-property-pages.md).

Jeśli włączysz przekierowanie do rejestru, struktura przekierowuje dostęp z klucza HKCR **HKEY_CURRENT_USER\Software\Classes**. Dotyczy tylko struktury MFC i ATL przekierowania.

Domyślna implementacja uzyskuje dostęp do kluczu HKCR rejestru.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxstat_.h

##  <a name="afxsetresourcehandle"></a>  AfxSetResourceHandle

Ta funkcja służy do ustawiania uchwytu HINSTANCE, który określa, gdzie są ładowane domyślnych zasobów aplikacji.

```
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);
```

### <a name="parameters"></a>Parametry

*hInstResource*<br/>
Uchwyt wystąpienia lub moduł, tak aby. Plik EXE lub DLL, z którego są ładowane zasoby aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#135](../../mfc/reference/codesnippet/cpp/application-information-and-management_12.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

## <a name="afxshellmanager"></a>  Afxshellmanager —

Wskaźnik do globalnego [Menedżera powłoki](cshellmanager-class.md).

### <a name="syntax"></a>Składnia

```
CShellManager* afxShellManager;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxshellmanager.h

##  <a name="afxsocketinit"></a>  AfxSocketInit

Wywołaj tę funkcję w swojej `CWinApp::InitInstance` należy przesłonić, aby zainicjować Windows Sockets.

```
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);
```

### <a name="parameters"></a>Parametry

*lpwsaData*<br/>
Wskaźnik do [WSADATA](/windows/desktop/api/winsock2/ns-winsock2-wsadata) struktury. Jeśli *lpwsaData* nie jest równa NULL, a następnie adres `WSADATA` struktury jest wypełniana przez wywołanie metody `WSAStartup`. Funkcja ta również zapewnia, że `WSACleanup` jest wywoływana dla Ciebie, zanim aplikacja zakończy.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Korzystając z MFC gniazd w pomocnicze wątki w statycznie połączonym aplikacji MFC, należy wywołać `AfxSocketInit` w każdy wątek, który używa gniazda można zainicjować biblioteki gniazda. Domyślnie `AfxSocketInit` jest wywoływana tylko w wątku głównym.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxsock.h

## <a name="afxusertoolsmanager"></a>  AfxUserToolsManager

Wskaźnik do globalnego [Menedżera narzędzi](cusertoolsmanager-class.md).

### <a name="syntax"></a>Składnia

```
CUserToolsManager* afxUserToolsManager;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxusertoolsmanager.h

##  <a name="afxwininit"></a>  Afxwininit —

Ta funkcja jest wywoływana przez podany MFC `WinMain` funkcji jako część [CWinApp](../../mfc/reference/cwinapp-class.md) inicjowania aplikacji Graficznym interfejsem użytkownika, można zainicjować biblioteki MFC.

```
BOOL AFXAPI AfxWinInit(
    HINSTANCE hInstance,
    HINSTANCE hPrevInstance,
    LPTSTR lpCmdLine,
    int nCmdShow);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Uchwyt modułu aktualnie uruchomione.

*hPrevInstance*<br/>
Dojście do poprzedniego wystąpienia aplikacji. W przypadku aplikacji Win32-na podstawie tego parametru jest zawsze **NULL**.

*lpCmdLine*<br/>
Wskazuje ciąg zakończony znakiem null określający wiersza polecenia dla aplikacji.

*nCmdShow*<br/>
Określa, jak będzie wyświetlane okno główne aplikacji graficznego interfejsu użytkownika.

### <a name="remarks"></a>Uwagi

Dla aplikacji konsoli, która nie używa MFC dostarczony `WinMain` funkcji, należy wywołać `AfxWinInit` bezpośrednio do zainicjowania MFC.

Jeśli wywołasz `AfxWinInit` samodzielnie, należy zadeklarować wystąpienie `CWinApp` klasy. Dla aplikacji konsoli, można wybrać nie pochodzi z klasy z `CWinApp` i zamiast tego użyć wystąpienia `CWinApp` bezpośrednio. Ta technika jest odpowiednie, jeśli użytkownik zdecyduje się Pozostaw wszystkie funkcje dla aplikacji w danej implementacji **głównego**.

> [!NOTE]
>  Podczas tworzenia kontekstu aktywacji dla zestawu, MFC wykorzystuje zasobu manifestu, dostarczone przez użytkownika moduł. Kontekst aktywacji jest tworzony w `AfxWinInit`. Aby uzyskać więcej informacji, zobacz [Obsługa kontekstów aktywacji w stanie modułu MFC](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

## <a name="see-also"></a>Zobacz także

[Makra i funkcje globalne](mfc-macros-and-globals.md)<br/>
[Klasa CWinApp](cwinapp-class.md)<br/>
[Klasa CContextMenuManager](ccontextmenumanager-class.md)<br/>
[Klasa CWnd](cwnd-class.md)<br/>
[Klasa CFrameWndEx](cframewndex-class.md)<br/>
[Klasa CMFCToolBar](cmfctoolbar-class.md)<br/>
[Klasa CKeyboardManager](ckeyboardmanager-class.md)<br/>
[Klasa CMenuTearOffManager](cmenutearoffmanager-class.md)<br/>
[Klasa CMouseManager](cmousemanager-class.md)<br/>
[Klasa CShellManager](cshellmanager-class.md)<br/>
[Klasa CUserToolsManager](cusertoolsmanager-class.md)
