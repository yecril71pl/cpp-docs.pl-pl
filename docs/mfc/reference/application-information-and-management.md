---
title: Informacje o aplikacji i zarządzanie nią
ms.date: 11/04/2016
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
ms.openlocfilehash: 934e89d928104c33f0c2038f136b5ad0ca48cbd4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507784"
---
# <a name="application-information-and-management"></a>Informacje o aplikacji i zarządzanie nią

Podczas pisania aplikacji utworzysz pojedynczy obiekt pochodny [CWinApp](../../mfc/reference/cwinapp-class.md). Czasami możesz chcieć uzyskać informacje o tym obiekcie spoza `CWinApp`obiektu pochodnego. Lub może być konieczne uzyskanie dostępu do innych globalnych obiektów "Manager".

Biblioteka MFC udostępnia następujące funkcje globalne, które ułatwiają wykonywanie następujących zadań:

### <a name="application-information-and-management-functions"></a>Informacje o aplikacji i funkcje zarządzania

|||
|-|-|
|[AfxBeginThread](#afxbeginthread)|Tworzy nowy wątek.|
|[AfxContextMenuManager](#afxcontextmenumanager)|Wskaźnik do globalnego [Menedżera menu kontekstowego](ccontextmenumanager-class.md).|
|[AfxEndThread](#afxendthread)|Kończy bieżący wątek.|
|[AfxFindResourceHandle](#afxfindresourcehandle)|Wyszukuje łańcuch zasobów i lokalizuje określony zasób według identyfikatora zasobu i typu zasobu. |
|[AfxFreeLibrary](#afxfreelibrary)|Zmniejsza liczbę odwołań do załadowanego modułu biblioteki dołączanej dynamicznie (DLL); gdy liczba odwołań osiągnie zero, moduł jest niezamapowany.|
|[AfxGetApp](#afxgetapp)|Zwraca wskaźnik do pojedynczego `CWinApp` obiektu aplikacji.|
|[AfxGetAppName](#afxgetappname)|Zwraca ciąg, który zawiera nazwę aplikacji.|
|[AfxGetInstanceHandle](#afxgetinstancehandle)|Zwraca HINSTANCE reprezentujący to wystąpienie aplikacji.|
|[AfxGetMainWnd](#afxgetmainwnd)|Zwraca wskaźnik do bieżącego okna "głównego" aplikacji innej niż OLE lub okna ramki w miejscu aplikacji serwera.|
|[AfxGetPerUserRegistration](#afxgetperuserregistration)|Użyj tej funkcji, aby określić, czy aplikacja przekierowuje dostęp do rejestru do węzła **HKEY_CURRENT_USER** ( **HKCU**).|
|[AfxGetResourceHandle](#afxgetresourcehandle)|Zwraca HINSTANCE do źródła domyślnych zasobów aplikacji. Służy do bezpośredniego uzyskiwania dostępu do zasobów aplikacji.|
|[AfxGetThread](#afxgetthread)|Pobiera wskaźnik do bieżącego obiektu [CWinThread](../../mfc/reference/cwinthread-class.md) .|
|[AfxInitRichEdit](#afxinitrichedit)|Inicjuje kontrolkę edycji wzbogaconej w wersji 1,0 dla aplikacji.|
|[AfxInitRichEdit2](#afxinitrichedit2)|Inicjuje w wersji 2,0 i nowszej kontrolkę edycji wzbogaconej dla aplikacji.|
|[AfxIsExtendedFrameClass](#afxisextendedframeclass)|Określa, czy dane okno jest obiektem ramki rozszerzonej.|
|[AfxIsMFCToolBar](#afxismfctoolbar)|Określa, czy dany okno jest obiektem paska narzędzi.|
|[AfxKeyboardManager](#afxkeyboardmanager)|Wskaźnik do globalnego [Menedżera klawiatury](ckeyboardmanager-class.md).|
|[AfxLoadLibrary](#afxloadlibrary)|Mapuje moduł DLL i zwraca dojście, którego można użyć do uzyskania adresu funkcji DLL.|
|[AfxMenuTearOffManager](#afxmenutearoffmanager)|Wskaźnik do globalnego [Menedżera menu odrywania](cmenutearoffmanager-class.md).|
|[AfxMouseManager](#afxmousemanager)|Wskaźnik do globalnego [Menedżera myszy](cmousemanager-class.md).|
|[AfxRegisterClass](#afxregisterclass)|Rejestruje klasę okna w bibliotece DLL korzystającej z MFC.|
|[AfxRegisterWndClass](#afxregisterwndclass)|Rejestruje klasę okna systemu Windows, aby uzupełnić te zarejestrowane automatycznie przez MFC.|
|[AfxSetPerUserRegistration](#afxsetperuserregistration)|Określa, czy aplikacja przekierowuje dostęp do rejestru do węzła **HKEY_CURRENT_USER** ( **HKCU**).|
|[AfxSetResourceHandle](#afxsetresourcehandle)|Ustawia dojście HINSTANCE, w którym są ładowane domyślne zasoby aplikacji.|
|[AfxShellManager](#afxshellmanager)|Wskaźnik do [Menedżera powłoki](cshellmanager-class.md)globalnego. |
|[AfxSocketInit](#afxsocketinit)|Wywołuje się, `CWinApp::InitInstance` by można było zainicjować Windows Sockets.|
|[AfxUserToolsManager](#afxusertoolsmanager)|Wskaźnik do globalnego [Menedżera narzędzi użytkownika](cusertoolsmanager-class.md).|
|[AfxWinInit](#afxwininit)|Wywoływane przez funkcję podaną `WinMain` przez MFC w ramach inicjalizacji [CWinApp](../../mfc/reference/cwinapp-class.md) aplikacji opartej na graficznym interfejsie użytkownika, aby zainicjować MFC. Musi być wywoływana bezpośrednio dla aplikacji konsolowych używających MFC.|

##  <a name="afxbeginthread"></a>AfxBeginThread

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
Wskazuje funkcję kontroli dla wątku roboczego. Nie może mieć wartości NULL. Ta funkcja musi być zadeklarowana w następujący sposób:

`UINT __cdecl MyControllingFunction( LPVOID pParam );`

*pThreadClass*<br/>
RUNTIME_CLASS obiektu pochodnego od [CWinThread](../../mfc/reference/cwinthread-class.md).

*pParam*<br/>
Parametr, który ma zostać przesłany do funkcji kontrolującej, jak pokazano w parametrze do deklaracji funkcji w *pfnThreadProc*.

*nPriority*<br/>
Żądany priorytet wątku. Aby uzyskać pełną listę i opis dostępnych priorytetów, zobacz [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) w Windows SDK.

*nStackSize*<br/>
Określa rozmiar w bajtach stosu dla nowego wątku. Jeśli wartość jest równa 0, rozmiar stosu jest domyślnie taki sam jak stos tworzenia wątku.

*dwCreateFlags*<br/>
Określa dodatkową flagę, która kontroluje tworzenie wątku. Ta flaga może zawierać jedną z dwóch wartości:

- CREATE_SUSPENDED Rozpocznij wątek z liczbą zawieszania o jednej. Użyj CREATE_SUSPENDED, jeśli chcesz zainicjować jakiekolwiek dane `CWinThread` elementu członkowskiego obiektu, takie jak [m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete) lub wszystkie elementy członkowskie klasy pochodnej, zanim wątek zacznie działać. Po zakończeniu inicjowania Użyj [CWinThread:: ResumeThread](../../mfc/reference/cwinthread-class.md#resumethread) , aby uruchomić wątek uruchomiony. Wątek nie zostanie wykonany do momentu `CWinThread::ResumeThread` wywołania.

- **0** Rozpocznij wątek natychmiast po utworzeniu.

*lpSecurityAttrs*<br/>
Wskazuje strukturę [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) , która określa atrybuty zabezpieczeń wątku. Jeśli wartość jest równa NULL, zostaną użyte te same atrybuty zabezpieczeń co wątek tworzenia. Aby uzyskać więcej informacji na temat tej struktury, zobacz Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzonego obiektu wątku lub wartość NULL, jeśli wystąpi awaria.

### <a name="remarks"></a>Uwagi

Pierwszy formularz `AfxBeginThread` tworzy wątek roboczy. Drugi formularz tworzy wątek, który może być używany jako wątek interfejsu użytkownika lub wątku roboczego.

`AfxBeginThread`Tworzy nowy `CWinThread` obiekt, wywołuje jego funkcję [](../../mfc/reference/cwinthread-class.md#createthread) myFunction, aby rozpocząć wykonywanie wątku, i zwraca wskaźnik do wątku. Kontrole są wykonywane w ramach procedury, aby upewnić się, że wszystkie obiekty są prawidłowo nieprzypisane, jeśli jakakolwiek część procesu tworzenia nie powiedzie się. Aby zakończyć wątek, wywołaj [AfxEndThread](#afxendthread) z wewnątrz wątku lub Wróć z funkcji kontrolującej wątku roboczego.

Wielowątkowość musi być włączona przez aplikację; w przeciwnym razie ta funkcja zakończy się niepowodzeniem. Aby uzyskać więcej informacji na temat włączania wielowątkowości, zapoznaj się z [/MD,/MT,/LD (Użyj biblioteki wykonawczej)](../../build/reference/md-mt-ld-use-run-time-library.md) w obszarze *Opcje kompilatora C++ wizualnego*.

Aby uzyskać więcej informacji `AfxBeginThread`na temat, zobacz [wielowątkowość artykułów: Tworzenie wątków](../../parallel/multithreading-creating-worker-threads.md) roboczych i [wielowątkowości: Tworzenie wątków](../../parallel/multithreading-creating-user-interface-threads.md)interfejsu użytkownika.

### <a name="example"></a>Przykład

Zobacz przykład dla [CSocket:: Attach](../../mfc/reference/csocket-class.md#attach).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

## <a name="afxcontextmenumanager"></a>AfxContextMenuManager

Wskaźnik do globalnego [Menedżera menu kontekstowego](ccontextmenumanager-class.md).

### <a name="syntax"></a>Składnia

```
CContextMenuManager* afxContextMenuManager;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxcontextmenumanager. h

##  <a name="afxendthread"></a>AfxEndThread

Wywołaj tę funkcję, aby zakończyć aktualnie wykonywany wątek.

```
void AFXAPI AfxEndThread(
    UINT nExitCode,
    BOOL bDelete  = TRUE);
```

### <a name="parameters"></a>Parametry

*nExitCode*<br/>
Określa kod zakończenia wątku.

*bUsunięcie*<br/>
Usuwa obiekt wątku z pamięci.

### <a name="remarks"></a>Uwagi

Musi być wywołana z poziomu wątku, aby zakończyć.

Aby uzyskać więcej informacji `AfxEndThread`na temat, zobacz [wielowątkowość artykułu: Przerywanie](../../parallel/multithreading-terminating-threads.md)wątków.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

  ## <a name="afxfindresourcehandle"></a>AfxFindResourceHandle
Służy `AfxFindResourceHandle` do przeszukiwania łańcucha zasobów i lokalizowania określonego zasobu według identyfikatora zasobu i typu zasobu.

### <a name="syntax"></a>Składnia

```
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Wskaźnik do ciągu zawierającego identyfikator zasobu.
*lpszType*<br/>
Wskaźnik do typu zasobu. Aby uzyskać listę typów zasobów, zobacz [FindResource](/windows/win32/api/winbase/nf-winbase-findresourcew) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Dojście do modułu zawierającego zasób.

### <a name="remarks"></a>Uwagi

`AfxFindResourceHandle`znajduje określony zasób i zwraca dojście do modułu, który zawiera zasób. Zasób może znajdować się w załadowanej bibliotece DLL rozszerzenia MFC. `AfxFindResourceHandle`informuje o tym, który z nich ma zasób.

Moduły są przeszukiwane w następującej kolejności:

1. Główny moduł (jeśli jest to biblioteka DLL rozszerzenia MFC).

1. Moduły inne niż systemowe.

1. Moduły specyficzne dla języka.

1. Główny moduł (jeśli jest to systemowa biblioteka DLL).

1. Moduły systemowe.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

##  <a name="afxfreelibrary"></a>AfxFreeLibrary

Obie `AfxFreeLibrary` i`AfxLoadLibrary` utrzymują liczbę odwołań dla każdego załadowanego modułu biblioteki.

```
BOOL AFXAPI AfxFreeLibrary(HINSTANCE hInstLib);
```

### <a name="parameters"></a>Parametry

*hInstLib*<br/>
Dojście załadowanego modułu biblioteki. [AfxLoadLibrary](#afxloadlibrary) zwraca ten uchwyt.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli funkcja się powiedzie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

`AfxFreeLibrary`zmniejsza liczbę odwołań do załadowanego modułu biblioteki dołączanej dynamicznie (DLL). Gdy liczba odwołań osiągnie wartość zero, moduł zostanie odmapowany z przestrzeni adresowej procesu wywołującego, a dojście nie jest już prawidłowe. Ta liczba odwołań jest zwiększana za każdym `AfxLoadLibrary` razem, gdy jest wywoływana.

Przed odmapowaniem modułu biblioteki, system umożliwia odłączenie biblioteki DLL od procesów, z których korzysta. Dzięki temu Biblioteka DLL umożliwia wyczyszczenie zasobów przyznanych w imieniu bieżącego procesu. Po powrocie funkcji punktu wejścia moduł biblioteki zostanie usunięty z przestrzeni adresowej bieżącego procesu.

Służy `AfxLoadLibrary` do mapowania modułu dll.

Upewnij się, że `AfxFreeLibrary` używasz `AfxLoadLibrary` i (zamiast funkcji `FreeLibrary` Win32 i `LoadLibrary`), jeśli aplikacja używa wielu wątków. Przy `AfxLoadLibrary` użyciu `AfxFreeLibrary` i zapewnia, że kod uruchamiania i zamykania, który jest wykonywany, gdy biblioteka DLL rozszerzenia MFC jest załadowana i zwolniona, nie powoduje uszkodzenia globalnego stanu MFC.

### <a name="example"></a>Przykład

Zobacz przykład dla [AfxLoadLibrary](#afxloadlibrary).

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDLL_. h

##  <a name="afxgetapp"></a>  AfxGetApp

Wskaźnik zwracany przez tę funkcję może być używany w celu uzyskania dostępu do informacji o aplikacji, takich jak główny kod wysyłania komunikatów lub okno z góry.

```
CWinApp* AFXAPI AfxGetApp();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pojedynczego `CWinApp` obiektu dla aplikacji.

### <a name="remarks"></a>Uwagi

Jeśli ta metoda zwróci wartość NULL, może to oznaczać, że okno główne aplikacji nie zostało jeszcze w pełni zainicjowane. Może również wskazywać na problem.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#126](../../mfc/reference/codesnippet/cpp/application-information-and-management_1.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

##  <a name="afxgetappname"></a>  AfxGetAppName

Ciąg zwracany przez tę funkcję może być używany w przypadku komunikatów diagnostycznych lub jako element główny dla nazw ciągów tymczasowych.

```
LPCTSTR AFXAPI AfxGetAppName();
```

### <a name="return-value"></a>Wartość zwracana

Ciąg zakończony znakiem null zawierający nazwę aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#127](../../mfc/reference/codesnippet/cpp/application-information-and-management_2.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

##  <a name="afxgetinstancehandle"></a>AfxGetInstanceHandle

Ta funkcja umożliwia pobranie dojścia do wystąpienia bieżącej aplikacji.

```
HINSTANCE  AFXAPI AfxGetInstanceHandle();
```

### <a name="return-value"></a>Wartość zwracana

HINSTANCE do bieżącego wystąpienia aplikacji. Jeśli wywoływana z poziomu biblioteki DLL połączonej z wersją USRDLL MFC, zwracany jest HINSTANCE do biblioteki DLL.

### <a name="remarks"></a>Uwagi

`AfxGetInstanceHandle`zawsze zwraca HINSTANCE pliku wykonywalnego (. EXE), chyba że jest wywoływana z poziomu biblioteki DLL połączonej z wersją USRDLL MFC. W tym przypadku zwraca HINSTANCE do biblioteki DLL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

##  <a name="afxgetmainwnd"></a>AfxGetMainWnd

Jeśli aplikacja jest serwerem OLE, Wywołaj tę funkcję, aby pobrać wskaźnik do aktywnego okna głównego aplikacji, zamiast bezpośrednio odwoływać się do elementu członkowskiego [m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd) obiektu aplikacji.

```
CWnd* AFXAPI AfxGetMainWnd();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli serwer ma obiekt, który znajduje się w miejscu aktywnym wewnątrz kontenera, a ten kontener jest aktywny, ta funkcja zwraca wskaźnik do obiektu okna ramki, który zawiera aktywny dokument w miejscu.

Jeśli nie ma obiektu, który jest aktywny w obrębie kontenera lub aplikacja nie jest serwerem OLE, ta funkcja po prostu zwraca *m_pMainWnd* obiektu aplikacji.

Jeśli `AfxGetMainWnd` jest wywoływana z wątku podstawowego aplikacji, zwraca okno główne aplikacji zgodnie z powyższymi regułami. Jeśli funkcja jest wywoływana z wątku pomocniczego w aplikacji, funkcja zwraca okno główne skojarzone z wątkiem, który wykonał wywołanie.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja nie jest serwerem OLE, wywołanie tej funkcji jest równoważne bezpośrednio odniesieniu się do elementu członkowskiego *m_pMainWnd* obiektu aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#129](../../mfc/reference/codesnippet/cpp/application-information-and-management_4.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

##  <a name="afxgetperuserregistration"></a>AfxGetPerUserRegistration

Użyj tej funkcji, aby określić, czy aplikacja przekierowuje dostęp do rejestru do węzła **HKEY_CURRENT_USER** ( **HKCU**).

```
BOOL AFXAPI AfxGetPerUserRegistration();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE wskazuje, że informacje rejestru są kierowane do węzła HKCU; Wartość FALSE oznacza, że aplikacja zapisuje informacje rejestru w domyślnym węźle. Domyślnym węzłem jest **HKEY_CLASSES_ROOT** ( **HKCR**).

### <a name="remarks"></a>Uwagi

Po włączeniu przekierowania rejestru platforma przekierowuje dostęp z **HKCR** do **HKEY_CURRENT_USER\Software\Classes**. Przekierowanie ma wpływ tylko na platformy MFC i ATL.

Aby zmienić, czy aplikacja przekierowuje dostęp do rejestru, użyj [AfxSetPerUserRegistration](#afxsetperuserregistration).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxstat_. h

##  <a name="afxgetresourcehandle"></a>  AfxGetResourceHandle

Użyj uchwytu HINSTANCE zwróconego przez tę funkcję, aby uzyskać dostęp do zasobów aplikacji bezpośrednio, na przykład w wywołaniach funkcji `FindResource`systemu Windows.

```
extern HINSTANCE  AfxGetResourceHandle();
```

### <a name="return-value"></a>Wartość zwracana

Dojście HINSTANCE, w którym są ładowane domyślne zasoby aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

##  <a name="afxgetthread"></a>  AfxGetThread

Wywołaj tę funkcję, aby uzyskać wskaźnik do obiektu [CWinThread](../../mfc/reference/cwinthread-class.md) reprezentującego aktualnie wykonywany wątek.

```
CWinThread* AfxGetThread();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do aktualnie wykonywanego wątku; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Musi być wywołana z poziomu żądanego wątku.

> [!NOTE]
>  W przypadku przenoszenia `AfxGetThread` projektu MFC wywołującego z Visual C++ wersji 4,2, 5,0 lub 6,0 wywołania `AfxGetThread` [AfxGetApp](#afxgetapp) , jeśli nie zostanie znaleziony żaden wątek. W nowszych wersjach kompilatora zwraca wartość null, `AfxGetThread` Jeśli nie znaleziono wątku. Jeśli potrzebujesz wątku aplikacji, musisz wywołać metodę `AfxGetApp`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

##  <a name="afxinitrichedit"></a>AfxInitRichEdit

Wywołaj tę funkcję, aby zainicjować kontrolkę edycji wzbogaconej (wersja 1,0) dla aplikacji.

```
BOOL AFXAPI AfxInitRichEdit();
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest dostępna w celu zapewnienia zgodności z poprzednimi wersjami. Nowe aplikacje powinny używać [Funkcja afxinitrichedit2](#afxinitrichedit2).

`AfxInitRichEdit`ładuje RICHED32. DLL, aby zainicjować wersję 1,0 kontrolki edycji wzbogaconej. Aby użyć wersji 2,0 i 3,0 kontrolki edycji wzbogaconej, biblioteki riched20. Należy załadować plik DLL. Jest to realizowane z wywołaniem do [Funkcja afxinitrichedit2](#afxinitrichedit2).

Aby zaktualizować kontrolki edycji wzbogaconej w C++ istniejących aplikacjach wizualnych do wersji 2,0, Otwórz. Plik RC jako tekst, Zmień nazwę klasy każdej kontrolki edycji wzbogaconej z "RICHEDIT" na "RichEdit20a". Następnie zastąp wywołanie do `AfxInitRichEdit`. `AfxInitRichEdit2`

Ta funkcja inicjuje również bibliotekę formantów wspólnych, jeśli biblioteka nie została jeszcze zainicjowana dla tego procesu. Jeśli używasz kontrolki edycji wzbogaconej bezpośrednio z poziomu aplikacji MFC, należy wywołać tę funkcję, aby upewnić się, że MFC prawidłowo zainicjowało środowisko uruchomieniowe kontrolki edycji wzbogaconej. Jeśli wywołasz metodę Create metody [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md)lub [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), zazwyczaj nie musisz wywoływać tej funkcji, ale w niektórych przypadkach może to być konieczne.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

##  <a name="afxinitrichedit2"></a>Funkcja afxinitrichedit2

Wywołaj tę funkcję, aby zainicjować kontrolkę edycji wzbogaconej (w wersji 2,0 i nowszej) dla aplikacji.

```
BOOL AFXAPI AfxInitRichEdit2();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby załadować biblioteki riched20. DLL i zainicjuj wersję 2,0 kontrolki edycji wzbogaconej. Jeśli wywołasz metodę Create metody [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md)lub [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), zazwyczaj nie musisz wywoływać tej funkcji, ale w niektórych przypadkach może to być konieczne.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

  ## <a name="afxisextendedframeclass"></a>AfxIsExtendedFrameClass
Określa, czy dane okno jest obiektem ramki rozszerzonej.

### <a name="syntax"></a>Składnia

```
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
podczas Wskaźnik do obiektu, który jest wyprowadzany z `CWnd`.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli podane okno jest obiektem ramki rozszerzonej; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość TRUE, jeśli *pWnd* dziedziczy z jednej z następujących klas:

- `CFrameWndEx`

- `CMDIFrameWndEx`

- `COleIPFrameWndEx`

- `COleDocIPFrameWndEx`

- `CMDIChildWndEx`

Ta metoda jest przydatna, gdy trzeba sprawdzić, czy parametr funkcji lub metody jest oknem ramki rozszerzonej.

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXPRIV. h

## <a name="afxismfctoolbar"></a>AfxIsMFCToolBar

Określa, czy dany okno jest obiektem paska narzędzi.

### <a name="syntax"></a>Składnia

```
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
podczas Wskaźnik do obiektu, który jest wyprowadzany z `CWnd`.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli podane okno jest obiektem Toolbar; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca `TRUE` wartość, jeśli *pWnd* dziedziczy z `CMFCToolBar`. Ta metoda jest przydatna, gdy trzeba sprawdzić, czy parametr funkcji lub metody jest `CMFCToolBar` obiektem.

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXPRIV. h

## <a name="afxkeyboardmanager"></a>AfxKeyboardManager

Wskaźnik do globalnego [Menedżera klawiatury](ckeyboardmanager-class.md).

### <a name="syntax"></a>Składnia

```
CKeyboardManager* afxKeyboardManager;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxkeyboardmanager. h

##  <a name="afxloadlibrary"></a>AfxLoadLibrary

Służy `AfxLoadLibrary` do mapowania modułu dll.

```
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName);
```

### <a name="parameters"></a>Parametry

*lpszModuleName*<br/>
Wskazuje ciąg zakończony znakiem null, który zawiera nazwę modułu (a. DLL lub. Plik EXE). Określona nazwa jest nazwą pliku modułu.

Jeśli ciąg Określa ścieżkę, ale plik nie istnieje w określonym katalogu, funkcja kończy się niepowodzeniem.

Jeśli ścieżka nie zostanie określona i rozszerzenie nazwy pliku zostanie pominięte, domyślne rozszerzenie. Biblioteka DLL jest dołączana. Jednak ciąg filename może zawierać znak końcowy (.), aby wskazać, że nazwa modułu nie ma rozszerzenia. Jeśli ścieżka nie zostanie określona, funkcja wyszukuje plik w następującej kolejności:

- Katalog, z którego załadowana została aplikacja.

- Bieżący katalog.

- **Windows 95/98:** Katalog systemu Windows. **Windows NT:** 32-bitowy katalog systemu Windows. Nazwa tego katalogu to SYSTEM32.

- **Tylko system Windows NT:** 16-bitowy katalog systemu Windows. Nie istnieje funkcja Win32, która uzyskuje ścieżkę do tego katalogu, ale jest przeszukiwana. Nazwą tego katalogu jest SYSTEM.

- Katalog systemu Windows.

- Katalogi, które są wymienione w zmiennej środowiskowej PATH.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana jest dojściem do modułu. Jeśli funkcja się nie powiedzie, zwracana wartość ma wartość NULL.

### <a name="remarks"></a>Uwagi

Zwraca dojście, które może być używane w [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) w celu uzyskania adresu funkcji DLL. `AfxLoadLibrary`może również służyć do mapowania innych modułów wykonywalnych.

Każdy proces zachowuje liczbę odwołań dla każdego załadowanego modułu biblioteki. Ta liczba odwołań jest zwiększana za każdym `AfxLoadLibrary` razem, gdy jest wywoływana i jest zmniejszana za każdym razem, gdy `AfxFreeLibrary` jest wywoływana. Gdy liczba odwołań osiągnie wartość zero, moduł zostanie odmapowany z przestrzeni adresowej procesu wywołującego, a dojście nie jest już prawidłowe.

Upewnij się, że `AfxLoadLibrary` używane `AfxFreeLibrary` są funkcje i (zamiast funkcji `LoadLibrary` Win32 `FreeLibrary`i), jeśli aplikacja używa wielu wątków i w przypadku dynamicznego ładowania biblioteki DLL rozszerzenia MFC. Za `AfxLoadLibrary` pomocą `AfxFreeLibrary` i upewnij się, że kod uruchamiania i zamykania, który jest wykonywany, gdy biblioteka DLL rozszerzenia MFC jest załadowana i zwolniona, nie powoduje uszkodzenia globalnego stanu MFC.

Używanie `AfxLoadLibrary` w aplikacji wymaga dynamicznego łączenia z biblioteką DLL MFC; plik nagłówka dla `AfxLoadLibrary`, Afxdll_. h, jest uwzględniany tylko wtedy, gdy MFC jest połączone z aplikacją jako biblioteka DLL. Jest to możliwe dzięki zaprojektowaniu, ponieważ należy połączyć się z biblioteką DLL MFC w celu użycia lub utworzenia bibliotek DLL rozszerzenia MFC.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_DLLUser#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]
[!code-cpp[NVC_MFC_DLLUser#2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]
[!code-cpp[NVC_MFC_DLLUser#3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDLL_. h

## <a name="afxmenutearoffmanager"></a>AfxMenuTearOffManager

Wskaźnik do globalnego [Menedżera menu odrywania](cmenutearoffmanager-class.md).

### <a name="syntax"></a>Składnia

```
CMenuTearOffManager* g_pTearOffMenuManager;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmenutearoffmanager. h

## <a name="afxmousemanager"></a>AfxMouseManager

Wskaźnik do globalnego [Menedżera myszy](cmousemanager-class.md).

### <a name="syntax"></a>Składnia

```
CMouseManager* afxMouseManager;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmousemanager. h

##  <a name="afxregisterclass"></a>  AfxRegisterClass

Ta funkcja służy do rejestrowania klas okien w bibliotece DLL korzystającej z MFC.

```
BOOL AFXAPI AfxRegisterClass(WNDCLASS* lpWndClass);
```

### <a name="parameters"></a>Parametry

*lpWndClass*<br/>
Wskaźnik do struktury [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) zawierającej informacje o klasie okna, która ma zostać zarejestrowana. Aby uzyskać więcej informacji na temat tej struktury, zobacz Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli klasa została pomyślnie zarejestrowana; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli używasz tej funkcji, Klasa zostanie automatycznie wyrejestrowana, gdy biblioteka DLL zostanie zwolniona.

W kompilacjach, które nie są `AfxRegisterClass` oparte na bibliotece DLL, identyfikator jest definiowany jako makro mapowane na `RegisterClass`funkcję systemu Windows, ponieważ klasy zarejestrowane w aplikacji są automatycznie wyrejestrowane. Jeśli używasz `AfxRegisterClass` `RegisterClass`zamiast, kod może być używany bez zmiany zarówno w aplikacji, jak i w bibliotece DLL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_DLL#3](../../atl-mfc-shared/codesnippet/cpp/application-information-and-management_10.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

##  <a name="afxregisterwndclass"></a>AfxRegisterWndClass —

Umożliwia zarejestrowanie własnych klas okien.

```
LPCTSTR AFXAPI AfxRegisterWndClass(
    UINT nClassStyle,
    HCURSOR hCursor = 0,
    HBRUSH hbrBackground = 0,
    HICON hIcon = 0);
```

### <a name="parameters"></a>Parametry

*nClassStyle*<br/>
Określa styl klasy systemu Windows lub kombinację stylów utworzonych przy użyciu operatora bitowego lub ( **&#124;** ) dla klasy Window. Aby zapoznać się z listą stylów klasy, zapoznaj się ze strukturą [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) w Windows SDK. Jeśli wartość jest równa NULL, ustawienia domyślne zostaną ustawione w następujący sposób:

- Ustawia styl myszy na CS_DBLCLKS, który wysyła wiadomości dwukrotnego kliknięcia do procedury okna, gdy użytkownik kliknie dwukrotnie mysz.

- Ustawia styl kursora strzałki w standardowym IDC_ARROW systemu Windows.

- Ustawia dla pędzla w tle wartość NULL, więc okno nie będzie wymazywać jego tła.

- Ustawia ikonę na ikonę standardowego, Waving flagi logo systemu Windows.

*hCursor*<br/>
Określa dojście do zasobu kursora, który ma zostać zainstalowany w każdym oknie utworzonym z klasy Window. Jeśli używasz domyślnej wartości **0**, zostanie wyświetlony standardowy kursor IDC_ARROW.

*hbrBackground*<br/>
Określa dojście do zasobu pędzla, który ma zostać zainstalowany w każdym oknie utworzonym z klasy Window. Jeśli używasz domyślnej wartości **0**, będziesz mieć pusty pędzel w tle, a okno domyślnie nie wymaże jego tła podczas przetwarzania [WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd).

*hIcon*<br/>
Określa dojście do zasobu ikony, który ma zostać zainstalowany w każdym oknie utworzonym z klasy Window. Jeśli zostanie użyta wartość domyślna **0**, zostanie wykorzystana Standardowa ikona logo systemu Windows z flagą Waving.

### <a name="return-value"></a>Wartość zwracana

Ciąg zakończony znakiem null zawierający nazwę klasy. Tę nazwę klasy można przekazać do `Create` funkcji składowej w `CWnd` lub innych klasach pochodnych **CWnd**, aby utworzyć okno. Nazwa jest generowana przez biblioteka MFC.

> [!NOTE]
>  Wartość zwracana jest wskaźnikiem do bufora statycznego. Aby zapisać ten ciąg, przypisz go do `CString` zmiennej.

### <a name="remarks"></a>Uwagi

Biblioteka MFC automatycznie rejestruje kilka klas standardowego okna. Wywołaj tę funkcję, jeśli chcesz zarejestrować własne klasy okien.

Nazwa zarejestrowana dla klasy `AfxRegisterWndClass` jest zależna wyłącznie od parametrów. Jeśli wywołasz `AfxRegisterWndClass` wiele razy z identycznymi parametrami, rejestruje klasy tylko przy pierwszym wywołaniu. Kolejne wywołania `AfxRegisterWndClass` z identycznymi parametrami po prostu zwracają już zarejestrowaną metodę ClassName.

Jeśli wywołasz `AfxRegisterWndClass` wiele klas pochodnych CWnd z identycznymi parametrami, zamiast uzyskać osobną klasę okna dla każdej klasy, każda klasa współużytkuje tę samą klasę okna. Może to spowodować problemy, jeśli używany jest styl klasy CS_CLASSDC. Zamiast wielu klas okien CS_CLASSDC, należy wykonać jedną klasę okna CS_CLASSDC, a wszystkie C++ okna, które używają tej klasy, współużytkują ten sam kontroler domeny. Aby uniknąć tego problemu, zadzwoń do [AfxRegisterClass](#afxregisterclass) w celu zarejestrowania klasy.

Zapoznaj się z [uwagą techniczną TN001: Rejestracja](../../mfc/tn001-window-class-registration.md) klasy okna `AfxRegisterWndClass` , aby uzyskać więcej informacji na temat rejestracji klas okien i funkcji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

##  <a name="afxsetperuserregistration"></a>AfxSetPerUserRegistration

Określa, czy aplikacja przekierowuje dostęp do rejestru do węzła **HKEY_CURRENT_USER** ( **HKCU**).

```
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
podczas Wartość TRUE wskazuje, że informacje rejestru są kierowane do węzła HKCU; Wartość FALSE oznacza, że aplikacja zapisuje informacje rejestru w domyślnym węźle. Domyślnym węzłem jest **HKEY_CLASSES_ROOT** ( **HKCR**).

### <a name="remarks"></a>Uwagi

Przed systemem Windows Vista aplikacje, które uzyskały dostęp do rejestru, zazwyczaj korzystają z węzła **HKEY_CLASSES_ROOT** . Jednak w systemach operacyjnych Windows Vista i nowszych należy uruchomić aplikację w trybie podniesionych uprawnień, aby zapisać w HKCR.

Ta metoda umożliwia aplikacji odczytywanie i zapisywanie w rejestrze bez uruchamiania w trybie podniesionych uprawnień przez przekierowanie dostępu rejestru z HKCR do HKCU. Aby uzyskać więcej informacji, zobacz [strony właściwości konsolidatora](../../build/reference/linker-property-pages.md).

Po włączeniu przekierowania rejestru platforma przekierowuje dostęp z HKCR do **HKEY_CURRENT_USER\Software\Classes**. Przekierowanie ma wpływ tylko na platformy MFC i ATL.

Domyślna implementacja uzyskuje dostęp do rejestru w obszarze HKCR.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxstat_. h

##  <a name="afxsetresourcehandle"></a>  AfxSetResourceHandle

Ta funkcja służy do ustawiania uchwytu HINSTANCE, który określa, gdzie są ładowane zasoby domyślne aplikacji.

```
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);
```

### <a name="parameters"></a>Parametry

*hInstResource*<br/>
Wystąpienie lub dojście modułu do. Plik EXE lub DLL, z którego są ładowane zasoby aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#135](../../mfc/reference/codesnippet/cpp/application-information-and-management_12.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

## <a name="afxshellmanager"></a>AfxShellManager

Wskaźnik do [Menedżera powłoki](cshellmanager-class.md)globalnego.

### <a name="syntax"></a>Składnia

```
CShellManager* afxShellManager;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxshellmanager. h

##  <a name="afxsocketinit"></a>AfxSocketInit

Wywołaj tę funkcję w `CWinApp::InitInstance` zastąpieniu, aby zainicjować Windows Sockets.

```
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);
```

### <a name="parameters"></a>Parametry

*lpwsaData*<br/>
Wskaźnik do struktury [WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata) . Jeśli *lpwsaData* nie jest równa null, adres `WSADATA` struktury jest wypełniany `WSAStartup`przez wywołanie. Ta funkcja gwarantuje również, `WSACleanup` że jest wywoływana dla Ciebie przed zakończeniem działania aplikacji.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

W przypadku korzystania z gniazd MFC w wątkach pomocniczych w statycznie połączonej aplikacji MFC `AfxSocketInit` należy wywołać w każdym wątku, który używa gniazd do inicjowania bibliotek gniazd. Domyślnie `AfxSocketInit` jest wywoływana tylko w wątku podstawowym.

### <a name="requirements"></a>Wymagania

  **Nagłówek** AfxSock. h

## <a name="afxusertoolsmanager"></a>AfxUserToolsManager

Wskaźnik do globalnego [Menedżera narzędzi użytkownika](cusertoolsmanager-class.md).

### <a name="syntax"></a>Składnia

```
CUserToolsManager* afxUserToolsManager;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxusertoolsmanager. h

##  <a name="afxwininit"></a>AfxWinInit

Ta funkcja jest wywoływana przez funkcję dostarczoną `WinMain` przez MFC w ramach inicjalizacji [CWinApp](../../mfc/reference/cwinapp-class.md) aplikacji opartej na graficznym interfejsie użytkownika w celu zainicjowania MFC.

```
BOOL AFXAPI AfxWinInit(
    HINSTANCE hInstance,
    HINSTANCE hPrevInstance,
    LPTSTR lpCmdLine,
    int nCmdShow);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Dojście aktualnie uruchomionego modułu.

*hPrevInstance*<br/>
Dojście do poprzedniego wystąpienia aplikacji. W przypadku aplikacji opartych na systemie Win32 ten parametr ma zawsze **wartość null**.

*lpCmdLine*<br/>
Wskazuje ciąg zakończony znakiem null określający wiersz polecenia dla aplikacji.

*nCmdShow*<br/>
Określa sposób wyświetlania głównego okna aplikacji graficznego interfejsu użytkownika.

### <a name="remarks"></a>Uwagi

W przypadku aplikacji konsolowej, która nie korzysta z funkcji dostarczonej `WinMain` przez MFC, należy wywołać `AfxWinInit` bezpośrednio, aby zainicjować MFC.

Jeśli wywołujesz `AfxWinInit` siebie, należy zadeklarować wystąpienie `CWinApp` klasy. W przypadku aplikacji konsolowej można zrezygnować z wyprowadzenia własnej klasy z `CWinApp` i zamiast tego używać `CWinApp` wystąpienia bezpośredniego. Ta technika jest odpowiednia, jeśli użytkownik zdecyduje się na pozostawienie wszystkich funkcji aplikacji w implementacji **głównej**.

> [!NOTE]
>  Gdy tworzy kontekst aktywacji dla zestawu, MFC używa zasobu manifestu dostarczonego przez moduł użytkownika. Kontekst aktywacji jest tworzony w `AfxWinInit`. Aby uzyskać więcej informacji, zobacz [Obsługa kontekstów aktywacji w stanie modułu MFC](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

## <a name="see-also"></a>Zobacz także

[Makra i Globals](mfc-macros-and-globals.md)<br/>
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
