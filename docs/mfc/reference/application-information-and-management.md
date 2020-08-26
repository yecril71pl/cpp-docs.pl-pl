---
title: Informacje o aplikacji i zarządzanie nią
description: Odwołanie do informacji o aplikacji i funkcji zarządzania w programie Microsoft Foundation Class Library (MFC).
ms.date: 01/27/2020
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
ms.openlocfilehash: 3412ed3f02e93d3e8c947d4f730355c219493a77
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832310"
---
# <a name="application-information-and-management"></a>Informacje o aplikacji i zarządzanie nią

Podczas pisania aplikacji utworzysz pojedynczy obiekt pochodny [CWinApp](../../mfc/reference/cwinapp-class.md). Czasami możesz chcieć uzyskać informacje o tym obiekcie spoza `CWinApp` obiektu pochodnego. Lub może być konieczne uzyskanie dostępu do innych globalnych obiektów "Manager".

Biblioteka MFC udostępnia następujące funkcje globalne, które ułatwiają wykonywanie następujących zadań:

## <a name="application-information-and-management-functions"></a>Informacje o aplikacji i funkcje zarządzania

| Nazwa | Opis |
|-|-|
|[AfxBeginThread](#afxbeginthread)|Tworzy nowy wątek.|
|[AfxContextMenuManager](#afxcontextmenumanager)|Wskaźnik do globalnego [Menedżera menu kontekstowego](ccontextmenumanager-class.md).|
|[AfxEndThread](#afxendthread)|Kończy bieżący wątek.|
|[AfxFindResourceHandle](#afxfindresourcehandle)|Wyszukuje łańcuch zasobów i lokalizuje określony zasób według identyfikatora zasobu i typu zasobu. |
|[AfxFreeLibrary](#afxfreelibrary)|Zmniejsza liczbę odwołań do załadowanego modułu biblioteki dołączanej dynamicznie (DLL). Gdy liczba odwołań osiągnie zero, moduł jest niezamapowany.|
|[AfxGetApp](#afxgetapp)|Zwraca wskaźnik do pojedynczego `CWinApp` obiektu aplikacji.|
|[AfxGetAppName](#afxgetappname)|Zwraca ciąg, który zawiera nazwę aplikacji.|
|[AfxGetInstanceHandle](#afxgetinstancehandle)|Zwraca HINSTANCE reprezentujący to wystąpienie aplikacji.|
|[AfxGetMainWnd](#afxgetmainwnd)|Zwraca wskaźnik do bieżącego okna "głównego" aplikacji innej niż OLE lub okna ramki w miejscu aplikacji serwera.|
|[AfxGetPerUserRegistration](#afxgetperuserregistration)|Użyj tej funkcji, aby określić, czy aplikacja przekierowuje dostęp do rejestru do węzła **HKEY_CURRENT_USER** (**HKCU**).|
|[AfxGetResourceHandle](#afxgetresourcehandle)|Zwraca HINSTANCE do źródła domyślnych zasobów aplikacji. Użyj, aby bezpośrednio uzyskać dostęp do zasobów aplikacji.|
|[AfxGetThread](#afxgetthread)|Pobiera wskaźnik do bieżącego obiektu [CWinThread](../../mfc/reference/cwinthread-class.md) .|
|[AfxInitRichEdit](#afxinitrichedit)|Inicjuje kontrolkę edycji wzbogaconej w wersji 1,0 dla aplikacji.|
|[Funkcja afxinitrichedit2](#afxinitrichedit2)|Inicjuje w wersji 2,0 i nowszej kontrolkę edycji wzbogaconej dla aplikacji.|
|[AfxIsExtendedFrameClass](#afxisextendedframeclass)|Określa, czy dane okno jest obiektem ramki rozszerzonej.|
|[AfxIsMFCToolBar](#afxismfctoolbar)|Określa, czy dany okno jest obiektem paska narzędzi.|
|[AfxKeyboardManager](#afxkeyboardmanager)|Wskaźnik do globalnego [Menedżera klawiatury](ckeyboardmanager-class.md).|
|[AfxLoadLibrary](#afxloadlibrary)|Mapuje moduł DLL i zwraca dojście, którego można użyć do uzyskania adresu funkcji DLL.|
|[AfxLoadLibraryEx](#afxloadlibraryex)|Mapuje moduł DLL przy użyciu określonych opcji i zwraca dojście, którego można użyć do uzyskania adresu funkcji DLL.|
|[AfxMenuTearOffManager](#afxmenutearoffmanager)|Wskaźnik do [Menedżera menu odrywania](cmenutearoffmanager-class.md)globalnego.|
|[AfxMouseManager](#afxmousemanager)|Wskaźnik do globalnego [Menedżera myszy](cmousemanager-class.md).|
|[AfxRegisterClass](#afxregisterclass)|Rejestruje klasę okna w bibliotece DLL korzystającej z MFC.|
|[AfxRegisterWndClass —](#afxregisterwndclass)|Rejestruje klasę okna systemu Windows, aby uzupełnić te zarejestrowane automatycznie przez MFC.|
|[AfxSetPerUserRegistration](#afxsetperuserregistration)|Określa, czy aplikacja przekierowuje dostęp do rejestru do węzła **HKEY_CURRENT_USER** (**HKCU**).|
|[AfxSetResourceHandle](#afxsetresourcehandle)|Ustawia dojście HINSTANCE, w którym są ładowane domyślne zasoby aplikacji.|
|[AfxShellManager](#afxshellmanager)|Wskaźnik do [Menedżera powłoki](cshellmanager-class.md)globalnego. |
|[AfxSocketInit](#afxsocketinit)|Wywołuje się, `CWinApp::InitInstance` by można było zainicjować Windows Sockets.|
|[AfxUserToolsManager](#afxusertoolsmanager)|Wskaźnik do globalnego [Menedżera narzędzi użytkownika](cusertoolsmanager-class.md).|
|[AfxWinInit](#afxwininit)|Wywoływane przez funkcję podaną przez MFC w `WinMain` ramach inicjalizacji [CWinApp](../../mfc/reference/cwinapp-class.md) aplikacji opartej na graficznym interfejsie użytkownika, aby zainicjować MFC. Musi być wywoływana bezpośrednio dla aplikacji konsolowych używających MFC.|

## <a name="afxbeginthread"></a><a name="afxbeginthread"></a> AfxBeginThread

Wywołaj tę funkcję, aby utworzyć nowy wątek.

```cpp
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

*pfnThreadProc*\
Wskazuje funkcję kontroli dla wątku roboczego. Wskaźnik nie może mieć wartości NULL. Ta funkcja musi być zadeklarowana w następujący sposób:

`UINT __cdecl MyControllingFunction( LPVOID pParam );`

*pThreadClass*\
RUNTIME_CLASS obiektu pochodnego od [CWinThread](../../mfc/reference/cwinthread-class.md).

*pParam*\
Parametr do przekazania do funkcji kontrolującej.

*nPriority*\
Priorytet ustawiony dla wątku. Aby uzyskać pełną listę i opis dostępnych priorytetów, zobacz [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) w Windows SDK.

*nStackSize*\
Określa rozmiar w bajtach stosu dla nowego wątku. Jeśli wartość jest równa 0, rozmiar stosu jest domyślnie taki sam jak stos tworzenia wątku.

*dwCreateFlags*\
Określa dodatkową flagę, która kontroluje tworzenie wątku. Ta flaga może zawierać jedną z dwóch wartości:

- CREATE_SUSPENDED uruchomić wątek z liczbą wstrzymania jednego. Użyj CREATE_SUSPENDED, jeśli chcesz zainicjować jakiekolwiek dane elementu członkowskiego `CWinThread` obiektu, takie jak [m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete) lub dowolnych elementów członkowskich klasy pochodnej, zanim wątek zacznie działać. Po zakończeniu inicjowania Użyj [CWinThread:: ResumeThread](../../mfc/reference/cwinthread-class.md#resumethread) , aby uruchomić wątek uruchomiony. Wątek nie zostanie wykonany do momentu `CWinThread::ResumeThread` wywołania.

- **0** Rozpocznij wątek natychmiast po utworzeniu.

*lpSecurityAttrs*\
Wskazuje strukturę [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) , która określa atrybuty zabezpieczeń wątku. Jeśli wartość jest równa NULL, używane są te same atrybuty zabezpieczeń co wątek tworzenia. Aby uzyskać więcej informacji na temat tej struktury, zobacz Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzonego obiektu wątku lub wartość NULL, jeśli wystąpi awaria.

### <a name="remarks"></a>Uwagi

Pierwszy formularz `AfxBeginThread` tworzy wątek roboczy. Drugi formularz tworzy wątek, który może być używany jako wątek interfejsu użytkownika lub wątku roboczego.

`AfxBeginThread`Tworzy nowy `CWinThread` obiekt, wywołuje jego funkcję [CreateThread](../../mfc/reference/cwinthread-class.md#createthread) myFunction, aby rozpocząć wykonywanie wątku, i zwraca wskaźnik do wątku. Kontrole są wykonywane w ramach procedury, aby upewnić się, że wszystkie obiekty są prawidłowo nieprzypisane, jeśli jakakolwiek część procesu tworzenia nie powiedzie się. Aby zakończyć wątek, wywołaj [AfxEndThread](#afxendthread) z wewnątrz wątku lub Wróć z funkcji kontrolującej wątku roboczego.

Wielowątkowość musi być włączona przez aplikację; w przeciwnym razie ta funkcja zakończy się niepowodzeniem. Aby uzyskać więcej informacji na temat włączania wielowątkowości, zobacz [/MD,/MT,/LD (Korzystanie z biblioteki wykonawczej)](../../build/reference/md-mt-ld-use-run-time-library.md).

Aby uzyskać więcej informacji na temat `AfxBeginThread` , zobacz artykuł [wielowątkowość: Tworzenie wątków roboczych](../../parallel/multithreading-creating-worker-threads.md) i [wielowątkowość: Tworzenie wątków interfejsu użytkownika](../../parallel/multithreading-creating-user-interface-threads.md).

### <a name="example"></a>Przykład

Zobacz przykład dla [CSocket:: Attach](../../mfc/reference/csocket-class.md#attach).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

## <a name="afxcontextmenumanager"></a><a name="afxcontextmenumanager"></a> AfxContextMenuManager

Wskaźnik do globalnego [Menedżera menu kontekstowego](ccontextmenumanager-class.md).

### <a name="syntax"></a>Składnia

```cpp
CContextMenuManager* afxContextMenuManager;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxcontextmenumanager. h

## <a name="afxendthread"></a><a name="afxendthread"></a> AfxEndThread

Wywołaj tę funkcję, aby zakończyć aktualnie wykonywany wątek.

```cpp
void AFXAPI AfxEndThread(
    UINT nExitCode,
    BOOL bDelete  = TRUE);
```

### <a name="parameters"></a>Parametry

*nExitCode*\
Określa kod zakończenia wątku.

*bUsunięcie*\
Usuwa obiekt wątku z pamięci.

### <a name="remarks"></a>Uwagi

Musi być wywołana z poziomu wątku, aby zakończyć.

Aby uzyskać więcej informacji na temat `AfxEndThread` , zobacz [wielowątkowość artykułu: kończenie wątków](../../parallel/multithreading-terminating-threads.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

## <a name="afxfindresourcehandle"></a><a name="afxfindresourcehandle"></a> AfxFindResourceHandle

Służy `AfxFindResourceHandle` do przeszukiwania łańcucha zasobów i lokalizowania określonego zasobu według identyfikatora zasobu i typu zasobu.

### <a name="syntax"></a>Składnia

```cpp
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );
```

### <a name="parameters"></a>Parametry

*lpszName*\
Wskaźnik do ciągu zawierającego identyfikator zasobu.
*lpszType*\
Wskaźnik do typu zasobu. Aby uzyskać listę typów zasobów, zobacz [FindResource](/windows/win32/api/winbase/nf-winbase-findresourcea) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Dojście do modułu zawierającego zasób.

### <a name="remarks"></a>Uwagi

`AfxFindResourceHandle` znajduje określony zasób i zwraca dojście do modułu, który zawiera zasób. Zasób może znajdować się we wszystkich załadowanych bibliotekach DLL rozszerzenia MFC. `AfxFindResourceHandle` informuje o tym, który z nich ma zasób.

Moduły są przeszukiwane w następującej kolejności:

1. Moduł główny, jeśli jest to biblioteka DLL rozszerzenia MFC.

1. Moduły inne niż systemowe.

1. Moduły specyficzne dla języka.

1. Moduł główny, jeśli jest to systemowa biblioteka DLL.

1. Moduły systemowe.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

## <a name="afxfreelibrary"></a><a name="afxfreelibrary"></a> AfxFreeLibrary

Obie `AfxFreeLibrary` i `AfxLoadLibrary` utrzymują liczbę odwołań dla każdego załadowanego modułu biblioteki.

```cpp
BOOL AFXAPI AfxFreeLibrary(HINSTANCE hInstLib);
```

### <a name="parameters"></a>Parametry

*hInstLib*\
Dojście załadowanego modułu biblioteki. [AfxLoadLibrary](#afxloadlibrary) zwraca ten uchwyt.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli funkcja się powiedzie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

`AfxFreeLibrary` zmniejsza liczbę odwołań do załadowanego modułu biblioteki dołączanej dynamicznie (DLL). Gdy liczba odwołań osiągnie wartość zero, moduł zostanie odmapowany z przestrzeni adresowej procesu wywołującego, a dojście nie jest już prawidłowe. Ta liczba odwołań jest zwiększana za każdym razem, gdy `AfxLoadLibrary` jest wywoływana.

Przed odmapowaniem modułu biblioteki, system umożliwia odłączenie biblioteki DLL od procesów, z których korzysta. Dzięki temu Biblioteka DLL umożliwia wyczyszczenie zasobów przyznanych dla bieżącego procesu. Po powrocie funkcji punktu wejścia moduł biblioteki zostanie usunięty z przestrzeni adresowej bieżącego procesu.

Służy `AfxLoadLibrary` do mapowania modułu dll.

Upewnij się, że używasz `AfxFreeLibrary` i `AfxLoadLibrary` (zamiast funkcji Win32 `FreeLibrary` i), `LoadLibrary` Jeśli aplikacja używa wielu wątków. Przy użyciu `AfxLoadLibrary` i `AfxFreeLibrary` zapewnia, że kod uruchamiania i zamykania, który jest wykonywany, gdy biblioteka DLL rozszerzenia MFC jest załadowana i zwolniona, nie powoduje uszkodzenia globalnego stanu MFC.

### <a name="example"></a>Przykład

Zobacz przykład dla [AfxLoadLibrary](#afxloadlibrary).

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDLL_. h

## <a name="afxgetapp"></a><a name="afxgetapp"></a> AfxGetApp

Wskaźnik zwracany przez tę funkcję może być używany w celu uzyskania dostępu do informacji o aplikacji, takich jak główny kod wysyłania komunikatów lub okno z góry.

```cpp
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

## <a name="afxgetappname"></a><a name="afxgetappname"></a> AfxGetAppName

Zwracany ciąg może być używany w przypadku komunikatów diagnostycznych lub jako element główny dla nazw ciągów tymczasowych.

```cpp
LPCTSTR AFXAPI AfxGetAppName();
```

### <a name="return-value"></a>Wartość zwracana

Ciąg zakończony znakiem null zawierający nazwę aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#127](../../mfc/reference/codesnippet/cpp/application-information-and-management_2.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

## <a name="afxgetinstancehandle"></a><a name="afxgetinstancehandle"></a> AfxGetInstanceHandle

Ta funkcja umożliwia pobranie dojścia do wystąpienia bieżącej aplikacji.

```cpp
HINSTANCE  AFXAPI AfxGetInstanceHandle();
```

### <a name="return-value"></a>Wartość zwracana

HINSTANCE do bieżącego wystąpienia aplikacji. Jeśli wywoływana z poziomu biblioteki DLL połączonej z wersją USRDLL MFC, zwracany jest HINSTANCE do biblioteki DLL.

### <a name="remarks"></a>Uwagi

`AfxGetInstanceHandle` zawsze zwraca HINSTANCE pliku wykonywalnego (. EXE), chyba że jest wywoływana z poziomu biblioteki DLL połączonej z wersją USRDLL MFC. W tym przypadku zwraca HINSTANCE do biblioteki DLL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

## <a name="afxgetmainwnd"></a><a name="afxgetmainwnd"></a> AfxGetMainWnd

Jeśli aplikacja jest serwerem OLE, Wywołaj tę funkcję, aby pobrać wskaźnik do aktywnego głównego okna aplikacji. Użyj tego wyniku zamiast bezpośrednio odwoływać się do [m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd) elementu członkowskiego obiektu aplikacji.

```cpp
CWnd* AFXAPI AfxGetMainWnd();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do obiektu okna ramki, który zawiera aktywny dokument w miejscu, jeśli serwer ma obiekt, który jest aktywny w miejscu wewnątrz aktywnego kontenera.

Jeśli nie ma obiektu, który jest aktywny w obrębie kontenera lub aplikacja nie jest serwerem OLE, ta funkcja zwraca *m_pMainWnd* obiektu aplikacji.

Jeśli `AfxGetMainWnd` jest wywoływana z wątku podstawowego aplikacji, zwraca okno główne aplikacji zgodnie z powyższymi regułami. Jeśli funkcja jest wywoływana z wątku pomocniczego w aplikacji, funkcja zwraca okno główne skojarzone z wątkiem, który wykonał wywołanie.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja nie jest serwerem OLE, wywołanie tej funkcji jest równoważne bezpośrednio odniesieniu się do *m_pMainWnd* elementu członkowskiego obiektu aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#129](../../mfc/reference/codesnippet/cpp/application-information-and-management_4.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

## <a name="afxgetperuserregistration"></a><a name="afxgetperuserregistration"></a> AfxGetPerUserRegistration

Użyj tej funkcji, aby określić, czy aplikacja przekierowuje dostęp do rejestru do węzła **HKEY_CURRENT_USER** (**HKCU**).

```cpp
BOOL AFXAPI AfxGetPerUserRegistration();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE wskazuje, że informacje rejestru są kierowane do węzła HKCU. Wartość FALSE oznacza, że aplikacja zapisuje informacje rejestru w domyślnym węźle. Domyślnym węzłem jest **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="remarks"></a>Uwagi

Po włączeniu przekierowania rejestru platforma przekierowuje dostęp z **HKCR** do **HKEY_CURRENT_USER \software\classes**. Przekierowanie ma wpływ tylko na platformy MFC i ATL.

Aby zmienić, czy aplikacja przekierowuje dostęp do rejestru, użyj [AfxSetPerUserRegistration](#afxsetperuserregistration).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxstat_. h

## <a name="afxgetresourcehandle"></a><a name="afxgetresourcehandle"></a> AfxGetResourceHandle

Użyj uchwytu HINSTANCE zwróconego przez tę funkcję, aby uzyskać dostęp do zasobów aplikacji bezpośrednio, na przykład w wywołaniach funkcji systemu Windows `FindResource` .

```cpp
extern HINSTANCE  AfxGetResourceHandle();
```

### <a name="return-value"></a>Wartość zwracana

Dojście HINSTANCE, w którym są ładowane domyślne zasoby aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

## <a name="afxgetthread"></a><a name="afxgetthread"></a> AfxGetThread

Wywołaj tę funkcję, aby uzyskać wskaźnik do obiektu [CWinThread](../../mfc/reference/cwinthread-class.md) reprezentującego aktualnie wykonywany wątek.

```cpp
CWinThread* AfxGetThread();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do aktualnie wykonywanego wątku; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Musi być wywołana z poziomu wątku.

> [!NOTE]
> W przypadku przenoszenia projektu MFC wywołującego `AfxGetThread` z Visual C++ wersje 4,2, 5,0 lub 6,0 program `AfxGetThread` wywołuje [AfxGetApp](#afxgetapp) , jeśli nie zostanie znaleziony żaden wątek. W nowszych wersjach kompilatora `AfxGetThread` zwraca wartość null, jeśli nie znaleziono wątku. Jeśli potrzebujesz wątku aplikacji, musisz wywołać metodę `AfxGetApp` .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

## <a name="afxinitrichedit"></a><a name="afxinitrichedit"></a> AfxInitRichEdit

Wywołaj tę funkcję, aby zainicjować kontrolkę edycji wzbogaconej (wersja 1,0) dla aplikacji.

```cpp
BOOL AFXAPI AfxInitRichEdit();
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest dostępna w celu zapewnienia zgodności z poprzednimi wersjami. Nowe aplikacje powinny używać [Funkcja afxinitrichedit2](#afxinitrichedit2).

`AfxInitRichEdit` ładuje RICHED32.DLL w celu zainicjowania wersji 1,0 kontrolki edycji wzbogaconej. Aby użyć wersji 2,0 i 3,0 kontrolki edycji wzbogaconej, należy załadować RICHED20.DLL. Jest ona ładowana przez wywołanie [Funkcja afxinitrichedit2](#afxinitrichedit2).

Aby zaktualizować kontrolki edycji wzbogaconej w istniejących aplikacjach Visual C++ do wersji 2,0, Otwórz. Plik RC jako tekst, Zmień nazwę klasy każdej kontrolki edycji wzbogaconej z "RICHEDIT" na "RichEdit20a". Następnie zastąp wywołanie do `AfxInitRichEdit` `AfxInitRichEdit2` .

Ta funkcja inicjuje również bibliotekę formantów wspólnych, jeśli biblioteka nie została jeszcze zainicjowana dla tego procesu. Jeśli używasz kontrolki edycji wzbogaconej bezpośrednio z poziomu aplikacji MFC, Wywołaj tę funkcję, aby upewnić się, że MFC prawidłowo zainicjowało środowisko uruchomieniowe kontrolki edycji wzbogaconej. Jeśli wywołasz `Create` metodę [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md)lub [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), zazwyczaj nie musisz wywoływać tej funkcji, ale w niektórych przypadkach może to być konieczne.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

## <a name="afxinitrichedit2"></a><a name="afxinitrichedit2"></a> Funkcja afxinitrichedit2

Wywołaj tę funkcję, aby zainicjować kontrolkę edycji wzbogaconej (w wersji 2,0 i nowszej) dla aplikacji.

```cpp
BOOL AFXAPI AfxInitRichEdit2();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby załadować RICHED20.DLL i zainicjować wersję 2,0 kontrolki edycji wzbogaconej. Jeśli wywołasz `Create` metodę [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md)lub [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), zazwyczaj nie musisz wywoływać tej funkcji, ale w niektórych przypadkach może to być konieczne.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

## <a name="afxisextendedframeclass"></a><a name="afxisextendedframeclass"></a> AfxIsExtendedFrameClass

Określa, czy dane okno jest obiektem ramki rozszerzonej.

### <a name="syntax"></a>Składnia

```cpp
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );
```

### <a name="parameters"></a>Parametry

*pWnd*\
podczas Wskaźnik do obiektu, który jest wyprowadzany z `CWnd` .

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

## <a name="afxismfctoolbar"></a><a name="afxismfctoolbar"></a> AfxIsMFCToolBar

Określa, czy dany okno jest obiektem paska narzędzi.

### <a name="syntax"></a>Składnia

```cpp
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*\
podczas Wskaźnik do obiektu, który jest wyprowadzany z `CWnd` .

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli podane okno jest obiektem Toolbar; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość, `TRUE` Jeśli *pWnd* dziedziczy z `CMFCToolBar` . Ta metoda jest przydatna, gdy trzeba sprawdzić, czy parametr funkcji lub metody jest `CMFCToolBar` obiektem.

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXPRIV. h

## <a name="afxkeyboardmanager"></a><a name="afxkeyboardmanager"></a> AfxKeyboardManager

Wskaźnik do globalnego [Menedżera klawiatury](ckeyboardmanager-class.md).

### <a name="syntax"></a>Składnia

```cpp
CKeyboardManager* afxKeyboardManager;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxkeyboardmanager. h

## <a name="afxloadlibrary"></a><a name="afxloadlibrary"></a> AfxLoadLibrary

Służy `AfxLoadLibrary` do mapowania modułu dll.

```cpp
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName);
```

### <a name="parameters"></a>Parametry

*lpszModuleName*\
Wskazuje ciąg zakończony znakiem null, który zawiera nazwę modułu (a. DLL lub. Plik EXE). Określona nazwa jest nazwą pliku modułu.

Jeśli ciąg Określa ścieżkę, ale plik nie istnieje w określonym katalogu, funkcja kończy się niepowodzeniem.

Jeśli ścieżka nie zostanie określona i rozszerzenie nazwy pliku zostanie pominięte, domyślne rozszerzenie. Biblioteka DLL jest dołączana. Jednak ciąg filename może zawierać znak końcowy (.), aby wskazać, że nazwa modułu nie ma rozszerzenia. Jeśli ścieżka nie zostanie określona, funkcja używa [kolejności wyszukiwania dla aplikacji klasycznych](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications).

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana jest dojściem do modułu. W przypadku niepowodzenia wartość zwracana jest RÓWNa NULL.

### <a name="remarks"></a>Uwagi

Zwraca dojście, które może być używane w [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) w celu uzyskania adresu funkcji DLL. `AfxLoadLibrary` może również służyć do mapowania innych modułów wykonywalnych.

Każdy proces zachowuje liczbę odwołań dla każdego załadowanego modułu biblioteki. Ta liczba odwołań jest zwiększana za każdym razem, gdy jest `AfxLoadLibrary` wywoływana i jest zmniejszana za każdym razem, gdy `AfxFreeLibrary` jest wywoływana. Gdy liczba odwołań osiągnie wartość zero, moduł zostanie odmapowany z przestrzeni adresowej procesu wywołującego, a dojście nie jest już prawidłowe.

Upewnij się, że używasz `AfxLoadLibrary` i `AfxFreeLibrary` (zamiast funkcji Win32 `LoadLibrary` i `FreeLibrary` ), jeśli aplikacja używa wielu wątków, a jeśli dynamicznie ŁADUJE bibliotekę DLL rozszerzenia MFC. Za pomocą `AfxLoadLibrary` i `AfxFreeLibrary` upewnij się, że kod uruchamiania i zamykania, który jest wykonywany, gdy biblioteka DLL rozszerzenia MFC jest załadowana i zwolniona, nie powoduje uszkodzenia globalnego stanu MFC.

Używanie `AfxLoadLibrary` w aplikacji wymaga dynamicznego łączenia z biblioteką DLL MFC. Plik nagłówkowy dla `AfxLoadLibrary` , Afxdll_. h, jest uwzględniany tylko wtedy, gdy MFC jest połączone z aplikacją jako biblioteka DLL. Ten wymóg jest zaprojektowany, ponieważ należy połączyć się z biblioteką DLL MFC w celu użycia lub utworzenia bibliotek DLL rozszerzenia MFC.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_DLLUser#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]
[!code-cpp[NVC_MFC_DLLUser#2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]
[!code-cpp[NVC_MFC_DLLUser#3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDLL_. h

## <a name="afxloadlibraryex"></a><a name="afxloadlibraryex"></a> AfxLoadLibraryEx

Służy `AfxLoadLibraryEx` do mapowania modułu dll.

```cpp
HINSTANCE AFXAPI AfxLoadLibraryEx(LPCTSTR lpFileName, HANDLE hFile, DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*lpFileName*\
Wskazuje ciąg zakończony znakiem null, który zawiera nazwę modułu (a. DLL lub. Plik EXE). Określona nazwa jest nazwą pliku modułu.

Jeśli ciąg Określa ścieżkę, ale plik nie istnieje w określonym katalogu, funkcja kończy się niepowodzeniem.

Jeśli ścieżka nie zostanie określona i rozszerzenie nazwy pliku zostanie pominięte, domyślne rozszerzenie. Biblioteka DLL jest dołączana. Jednak ciąg filename może zawierać znak końcowy (.), aby wskazać, że nazwa modułu nie ma rozszerzenia. Jeśli ścieżka nie zostanie określona, funkcja używa [kolejności wyszukiwania dla aplikacji klasycznych](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications).

*hFile*\
Ten parametr jest zarezerwowany do użytku w przyszłości. Musi mieć wartość NULL.

*flagiDW*\
Akcja, która ma zostać wykonana podczas ładowania modułu. Jeśli nie określono żadnych flag, zachowanie tej funkcji jest identyczne z `AfxLoadLibrary` funkcją. Możliwe wartości tego parametru są opisane w dokumentacji [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) .

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana jest dojściem do modułu. W przypadku niepowodzenia wartość zwracana jest RÓWNa NULL.

### <a name="remarks"></a>Uwagi

`AfxLoadLibraryEx` zwraca dojście, które może być używane w funkcji [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) w celu uzyskania adresu programu dll. `AfxLoadLibraryEx` może również służyć do mapowania innych modułów wykonywalnych.

Każdy proces zachowuje liczbę odwołań dla każdego załadowanego modułu biblioteki. Ta liczba odwołań jest zwiększana za każdym razem, gdy jest `AfxLoadLibraryEx` wywoływana i jest zmniejszana za każdym razem, gdy `AfxFreeLibrary` jest wywoływana. Gdy liczba odwołań osiągnie wartość zero, moduł zostanie odmapowany z przestrzeni adresowej procesu wywołującego, a dojście nie jest już prawidłowe.

Upewnij się, że używane są `AfxLoadLibraryEx` `AfxFreeLibrary` funkcje i (zamiast funkcji Win32 `LoadLibraryEx` i), `FreeLibrary` Jeśli aplikacja używa wielu wątków i w przypadku dynamicznego ładowania biblioteki DLL rozszerzenia MFC. Przy użyciu `AfxLoadLibraryEx` i `AfxFreeLibrary` zapewnia, że kod uruchamiania i zamykania, który jest wykonywany, gdy biblioteka DLL rozszerzenia MFC jest załadowana i zwolniona, nie powoduje uszkodzenia globalnego stanu MFC.

Używanie `AfxLoadLibraryEx` w aplikacji wymaga dynamicznego łączenia z biblioteką DLL MFC. Plik nagłówkowy dla `AfxLoadLibraryEx` , Afxdll_. h, jest uwzględniany tylko wtedy, gdy MFC jest połączone z aplikacją jako biblioteka DLL. Ten wymóg jest zaprojektowany, ponieważ należy połączyć się z biblioteką DLL MFC w celu użycia lub utworzenia bibliotek DLL rozszerzenia MFC.

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDLL_. h

## <a name="afxmenutearoffmanager"></a><a name="afxmenutearoffmanager"></a> AfxMenuTearOffManager

Wskaźnik do [Menedżera menu odrywania](cmenutearoffmanager-class.md)globalnego.

### <a name="syntax"></a>Składnia

```cpp
CMenuTearOffManager* g_pTearOffMenuManager;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmenutearoffmanager. h

## <a name="afxmousemanager"></a><a name="afxmousemanager"></a> AfxMouseManager

Wskaźnik do globalnego [Menedżera myszy](cmousemanager-class.md).

### <a name="syntax"></a>Składnia

```cpp
CMouseManager* afxMouseManager;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmousemanager. h

## <a name="afxregisterclass"></a><a name="afxregisterclass"></a> AfxRegisterClass

Ta funkcja służy do rejestrowania klas okien w bibliotece DLL korzystającej z MFC.

```cpp
BOOL AFXAPI AfxRegisterClass(WNDCLASS* lpWndClass);
```

### <a name="parameters"></a>Parametry

*lpWndClass*\
Wskaźnik do struktury [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) zawierającej informacje o klasie okna, która ma zostać zarejestrowana. Aby uzyskać więcej informacji na temat tej struktury, zobacz Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli klasa została pomyślnie zarejestrowana; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli używasz tej funkcji, Klasa zostanie automatycznie wyrejestrowana, gdy biblioteka DLL zostanie zwolniona.

W kompilacjach, które nie są oparte na bibliotece DLL, `AfxRegisterClass` Identyfikator jest definiowany jako makro mapowane na funkcję systemu Windows `RegisterClass` , ponieważ klasy zarejestrowane w aplikacji są automatycznie wyrejestrowane. Jeśli używasz `AfxRegisterClass` zamiast `RegisterClass` , kod może być używany bez zmiany zarówno w aplikacji, jak i w bibliotece DLL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_DLL#3](../../atl-mfc-shared/codesnippet/cpp/application-information-and-management_10.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

## <a name="afxregisterwndclass"></a><a name="afxregisterwndclass"></a> AfxRegisterWndClass —

Umożliwia zarejestrowanie własnych klas okien.

```cpp
LPCTSTR AFXAPI AfxRegisterWndClass(
    UINT nClassStyle,
    HCURSOR hCursor = 0,
    HBRUSH hbrBackground = 0,
    HICON hIcon = 0);
```

### <a name="parameters"></a>Parametry

*nClassStyle*\
Określa styl klasy systemu Windows lub kombinację stylów utworzonych przy użyciu operatora bitowego lub (**&#124;**) dla klasy Window. Aby zapoznać się z listą stylów klasy, zapoznaj się ze strukturą [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) w Windows SDK. Jeśli wartość jest równa NULL, ustawienia domyślne są ustawiane w następujący sposób:

- Ustawia styl myszy na CS_DBLCLKS, który wysyła wiadomości dwukrotnego kliknięcia do procedury okna, gdy użytkownik kliknie dwukrotnie mysz.

- Ustawia styl kursora strzałki w standardowym IDC_ARROW systemu Windows.

- Ustawia dla pędzla tła wartość NULL, więc okno nie będzie wymazywać jego tła.

- Ustawia ikonę na ikonę standardowego, Waving flagi logo systemu Windows.

*hCursor*\
Określa dojście do zasobu kursora, który ma zostać zainstalowany w każdym oknie utworzonym z klasy Window. Jeśli używasz domyślnej wartości **0**, uzyskasz standardowy kursor IDC_ARROW.

*hbrBackground*\
Określa dojście do zasobu pędzla, który ma zostać zainstalowany w każdym oknie utworzonym z klasy Window. Jeśli używasz domyślnej wartości **0**, będziesz mieć pusty pędzel w tle, a domyślnie okno nie wymaże jego tła podczas przetwarzania [WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd).

*hIcon*\
Określa dojście do zasobu ikony, który ma zostać zainstalowany w każdym oknie utworzonym z klasy Window. Jeśli zostanie użyta wartość domyślna **0**, otrzymasz standardową ikonę logo systemu Windows z flagą Waving.

### <a name="return-value"></a>Wartość zwracana

Ciąg zakończony znakiem null zawierający nazwę klasy. Tę nazwę klasy można przekazać do `Create` funkcji składowej w `CWnd` lub innych klasach pochodnych **CWnd**, aby utworzyć okno. Nazwa jest generowana przez biblioteka MFC.

> [!NOTE]
> Wartość zwracana jest wskaźnikiem do bufora statycznego. Aby zapisać ten ciąg, przypisz go do `CString` zmiennej.

### <a name="remarks"></a>Uwagi

Biblioteka MFC automatycznie rejestruje kilka klas standardowego okna. Wywołaj tę funkcję, jeśli chcesz zarejestrować własne klasy okien.

Nazwa zarejestrowana dla klasy jest `AfxRegisterWndClass` zależna wyłącznie od parametrów. Jeśli wywołasz `AfxRegisterWndClass` wiele razy z identycznymi parametrami, rejestruje klasy tylko przy pierwszym wywołaniu. Późniejsze wywołania `AfxRegisterWndClass` z identycznymi parametrami zwracają już zarejestrowaną metodę ClassName.

Jeśli wywołasz `AfxRegisterWndClass` wiele klas pochodnych CWnd z identycznymi parametrami, zamiast uzyskać osobną klasę okna dla każdej klasy, każda klasa współużytkuje tę samą klasę okna. Takie udostępnianie może spowodować problemy, jeśli używany jest styl klasy CS_CLASSDC. Zamiast wielu CS_CLASSDC klas okien, można kończyć się tylko jedną klasą CS_CLASSDC Window. Wszystkie okna języka C++, które używają tej klasy, współużytkują ten sam kontroler domeny. Aby uniknąć tego problemu, zadzwoń do [AfxRegisterClass](#afxregisterclass) w celu zarejestrowania klasy.

Zapoznaj się z uwagami technicznymi [TN001: Rejestracja klasy okna](../../mfc/tn001-window-class-registration.md) , aby uzyskać więcej informacji na temat rejestracji klas okien i `AfxRegisterWndClass` funkcji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

## <a name="afxsetperuserregistration"></a><a name="afxsetperuserregistration"></a> AfxSetPerUserRegistration

Określa, czy aplikacja przekierowuje dostęp do rejestru do węzła **HKEY_CURRENT_USER** (**HKCU**).

```cpp
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bEnable*\
podczas Wartość TRUE wskazuje, że informacje rejestru są kierowane do węzła HKCU. Wartość FALSE oznacza, że aplikacja zapisuje informacje rejestru w domyślnym węźle. Domyślnym węzłem jest **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="remarks"></a>Uwagi

Przed systemem Windows Vista aplikacje, które uzyskały dostęp do rejestru, często używają węzła **HKEY_CLASSES_ROOT** . Jednak w systemach operacyjnych Windows Vista i nowszych należy uruchomić aplikację w trybie podniesionych uprawnień, aby zapisać w HKCR.

Ta metoda umożliwia aplikacji odczytywanie i zapisywanie w rejestrze bez uruchamiania w trybie podniesionych uprawnień. Działa przez przekierowanie dostępu rejestru z HKCR do HKCU. Aby uzyskać więcej informacji, zobacz [strony właściwości konsolidatora](../../build/reference/linker-property-pages.md).

Po włączeniu przekierowania rejestru platforma przekierowuje dostęp z HKCR do **HKEY_CURRENT_USER \software\classes**. Przekierowanie ma wpływ tylko na platformy MFC i ATL.

Domyślna implementacja uzyskuje dostęp do rejestru w obszarze HKCR.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxstat_. h

## <a name="afxsetresourcehandle"></a><a name="afxsetresourcehandle"></a> AfxSetResourceHandle

Ta funkcja służy do ustawiania uchwytu HINSTANCE, który określa, gdzie są ładowane zasoby domyślne aplikacji.

```cpp
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);
```

### <a name="parameters"></a>Parametry

*hInstResource*\
Wystąpienie lub dojście modułu do. Plik EXE lub DLL, z którego są ładowane zasoby aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#135](../../mfc/reference/codesnippet/cpp/application-information-and-management_12.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

## <a name="afxshellmanager"></a><a name="afxshellmanager"></a> AfxShellManager

Wskaźnik do [Menedżera powłoki](cshellmanager-class.md)globalnego.

### <a name="syntax"></a>Składnia

```cpp
CShellManager* afxShellManager;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxshellmanager. h

## <a name="afxsocketinit"></a><a name="afxsocketinit"></a> AfxSocketInit

Wywołaj tę funkcję w `CWinApp::InitInstance` zastąpieniu, aby zainicjować Windows Sockets.

```cpp
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);
```

### <a name="parameters"></a>Parametry

*lpwsaData*\
Wskaźnik do struktury [WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata) . Jeśli *lpwsaData* nie jest równa null, adres `WSADATA` struktury jest wypełniany przez wywołanie `WSAStartup` . Ta funkcja gwarantuje również, że `WSACleanup` jest wywoływana dla Ciebie przed zakończeniem działania aplikacji.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

W przypadku korzystania z gniazd MFC w wątkach pomocniczych w statycznie połączonej aplikacji MFC należy wywołać `AfxSocketInit` w każdym wątku, który używa gniazd do inicjowania bibliotek gniazd. Domyślnie `AfxSocketInit` jest wywoływana tylko w wątku podstawowym.

### <a name="requirements"></a>Wymagania

  **Nagłówek** AfxSock. h

## <a name="afxusertoolsmanager"></a><a name="afxusertoolsmanager"></a> AfxUserToolsManager

Wskaźnik do globalnego [Menedżera narzędzi użytkownika](cusertoolsmanager-class.md).

### <a name="syntax"></a>Składnia

```cpp
CUserToolsManager* afxUserToolsManager;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxusertoolsmanager. h

## <a name="afxwininit"></a><a name="afxwininit"></a> AfxWinInit

Ta funkcja jest wywoływana przez funkcję dostarczoną przez MFC w `WinMain` ramach inicjalizacji [CWinApp](../../mfc/reference/cwinapp-class.md) aplikacji opartej na graficznym interfejsie użytkownika w celu zainicjowania MFC.

```cpp
BOOL AFXAPI AfxWinInit(
    HINSTANCE hInstance,
    HINSTANCE hPrevInstance,
    LPTSTR lpCmdLine,
    int nCmdShow);
```

### <a name="parameters"></a>Parametry

*hInstance*\
Dojście aktualnie uruchomionego modułu.

*hPrevInstance*\
Dojście do poprzedniego wystąpienia aplikacji. W przypadku aplikacji opartych na systemie Win32 ten parametr ma zawsze **wartość null**.

*lpCmdLine*\
Wskazuje ciąg zakończony znakiem null określający wiersz polecenia dla aplikacji.

*nCmdShow*\
Określa sposób wyświetlania głównego okna aplikacji graficznego interfejsu użytkownika.

### <a name="remarks"></a>Uwagi

W przypadku aplikacji konsolowej, która nie korzysta z funkcji dostarczonej przez MFC `WinMain` , należy wywołać `AfxWinInit` bezpośrednio, aby zainicjować MFC.

Jeśli wywołujesz `AfxWinInit` siebie, należy zadeklarować wystąpienie `CWinApp` klasy. W przypadku aplikacji konsolowej można zrezygnować z wyprowadzenia własnej klasy z `CWinApp` i zamiast tego używać wystąpienia `CWinApp` bezpośredniego. Ta technika jest odpowiednia, jeśli użytkownik zdecyduje się na pozostawienie wszystkich funkcji aplikacji w implementacji **głównej**.

> [!NOTE]
> Gdy tworzy kontekst aktywacji dla zestawu, MFC używa zasobu manifestu dostarczonego przez moduł użytkownika. Kontekst aktywacji jest tworzony w `AfxWinInit` . Aby uzyskać więcej informacji, zobacz [Obsługa kontekstów aktywacji w stanie modułu MFC](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin. h

## <a name="see-also"></a>Zobacz też

[Makra i Globals](mfc-macros-and-globals.md)\
[Klasa CWinApp](cwinapp-class.md)\
[Klasa CContextMenuManager](ccontextmenumanager-class.md)\
[Klasa CWnd](cwnd-class.md)\
[Klasa CFrameWndEx](cframewndex-class.md)\
[Klasa CMFCToolBar](cmfctoolbar-class.md)\
[Klasa CKeyboardManager](ckeyboardmanager-class.md)\
[Klasa CMenuTearOffManager](cmenutearoffmanager-class.md)\
[Klasa CMouseManager](cmousemanager-class.md)\
[Klasa CShellManager](cshellmanager-class.md)\
[Klasa CUserToolsManager](cusertoolsmanager-class.md)
