---
title: Informacje o aplikacji i zarządzanie nią
description: Odwołanie do informacji o aplikacji i funkcji zarządzania biblioteką klasy Microsoft Foundation (MFC).
ms.date: 01/27/2020
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
ms.openlocfilehash: fc0b4b09f6c48da68bebe4a2825f49bcf6ab7e23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372500"
---
# <a name="application-information-and-management"></a>Informacje o aplikacji i zarządzanie nią

Podczas pisania aplikacji, należy utworzyć pojedynczy [obiekt CWinApp](../../mfc/reference/cwinapp-class.md)pochodne. Czasami można uzyskać informacje o tym obiekcie `CWinApp`spoza obiektu pochodnego. Możesz też potrzebować dostępu do innych globalnych obiektów "menedżera".

Biblioteka klas programu Microsoft Foundation udostępnia następujące funkcje globalne ułatwiające wykonywanie tych zadań:

## <a name="application-information-and-management-functions"></a>Funkcje informacji o aplikacji i zarządzania

|||
|-|-|
|[Afxbeginthread](#afxbeginthread)|Tworzy nowy wątek.|
|[AfxContextMenuManager](#afxcontextmenumanager)|Wskaźnik do globalnego [menedżera menu kontekstowego](ccontextmenumanager-class.md).|
|[AfxEndThread (AfxEndThread)](#afxendthread)|Kończy bieżący wątek.|
|[AfxFindResourceHandle](#afxfindresourcehandle)|Spacery z łańcuchem zasobów i lokalizowanie określonego zasobu według identyfikatora zasobu i typu zasobu. |
|[AfxFreeLibrary](#afxfreelibrary)|Zmniejsza liczbę odwołań modułu załadowanej biblioteki dynamicznej (DLL). Gdy liczba odwołań osiągnie zero, moduł jest odmapowany.|
|[AfxGetApp (AfxGetApp)](#afxgetapp)|Zwraca wskaźnik do pojedynczego `CWinApp` obiektu aplikacji.|
|[AfxGetAppName (Nazwa aplikacji AfxGetAppName)](#afxgetappname)|Zwraca ciąg zawierający nazwę aplikacji.|
|[AfxGetInstanceHandle (Uchwyt afxgetinstance)](#afxgetinstancehandle)|Zwraca hinstance reprezentujący to wystąpienie aplikacji.|
|[AfxGetMainWnd (AfxGetMainWnd)](#afxgetmainwnd)|Zwraca wskaźnik do bieżącego okna "głównego" aplikacji nie ole lub okna ramki w miejscu aplikacji serwera.|
|[AfxGetPerUserRegistration AfxGetPerUserRegistration AfxGetPerUserRegistration Afx](#afxgetperuserregistration)|Ta funkcja służy do określania, czy aplikacja przekierowuje dostęp rejestru do węzła **HKEY_CURRENT_USER** **(HKCU).**|
|[AfxGetResourceHandle (AfxGetResourceHandle)](#afxgetresourcehandle)|Zwraca HINSTANCE do źródła domyślnych zasobów aplikacji. Służy do bezpośredniego dostępu do zasobów aplikacji.|
|[AfxGetThread (AfxGetThread)](#afxgetthread)|Pobiera wskaźnik do bieżącego [obiektu CWinThread.](../../mfc/reference/cwinthread-class.md)|
|[AfxInitRichEdytuj](#afxinitrichedit)|Inicjuje formant edycji bogatej w wersji 1.0 dla aplikacji.|
|[AfxInitRichEdit2](#afxinitrichedit2)|Inicjuje formant edycji w wersji 2.0 i nowszej dla aplikacji.|
|[AfxIsExtendedFrameClass](#afxisextendedframeclass)|Określa, czy dane okno jest obiektem ramki rozszerzonej.|
|[Pasek AfxIsMFCToolBar](#afxismfctoolbar)|Określa, czy dane okno jest obiektem paska narzędzi.|
|[AfxKeyboardManager](#afxkeyboardmanager)|Wskaźnik do globalnego [menedżera klawiatury](ckeyboardmanager-class.md).|
|[Afxloadlibrary](#afxloadlibrary)|Mapuje moduł DLL i zwraca dojście, którego można użyć do uzyskania adresu funkcji DLL.|
|[AfxLoadLibraryEx](#afxloadlibraryex)|Mapuje moduł DLL przy użyciu określonych opcji i zwraca dojście, którego można użyć do uzyskania adresu funkcji biblioteki DLL.|
|[AfxMenuTearOffManager](#afxmenutearoffmanager)|Wskaźnik do globalnego [menedżera menu odrywać](cmenutearoffmanager-class.md).|
|[AfxMouseManager](#afxmousemanager)|Wskaźnik do globalnego [menedżera myszy](cmousemanager-class.md).|
|[AfxRegisterClass ( AfxRegisterClass )](#afxregisterclass)|Rejestruje klasę okna w biblioteki DLL, która używa MFC.|
|[Afxregisterwndclass](#afxregisterwndclass)|Rejestruje klasę okna systemu Windows w celu uzupełnienia tych zarejestrowanych automatycznie przez MFC.|
|[AfxSetPerUserRegistration](#afxsetperuserregistration)|Określa, czy aplikacja przekierowuje dostęp rejestru do węzła **HKEY_CURRENT_USER** **(HKCU).**|
|[AfxSetResourceHandle](#afxsetresourcehandle)|Ustawia uchwyt HINSTANCE, w którym są ładowane domyślne zasoby aplikacji.|
|[AfxShellManager (AfxShellManager)](#afxshellmanager)|Wskaźnik do globalnego [menedżera powłoki](cshellmanager-class.md). |
|[Afxsocketinit](#afxsocketinit)|Wywoływana `CWinApp::InitInstance` w celu zainicjowania gniazda systemu Windows.|
|[AfxUserToolsManager](#afxusertoolsmanager)|Wskaźnik do globalnego [menedżera narzędzi użytkownika](cusertoolsmanager-class.md).|
|[AfxWinInit ( AfxWinInit )](#afxwininit)|Wywoływana przez funkcję `WinMain` dostarczoną przez MFC, jako część inicjowania aplikacji opartej na interfejsie użytkownika [WWW,](../../mfc/reference/cwinapp-class.md) aby zainicjować MFC. Musi być wywoływana bezpośrednio dla aplikacji konsoli, które używają MFC.|

## <a name="afxbeginthread"></a><a name="afxbeginthread"></a>Afxbeginthread

Wywołanie tej funkcji, aby utworzyć nowy wątek.

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
Wskazuje funkcję sterującą wątku roboczego. Wskaźnik nie może mieć wartości NULL. Funkcję tę należy zadeklarować w następujący sposób:

`UINT __cdecl MyControllingFunction( LPVOID pParam );`

*pThreadClass (Klasa pThreadClass)*\
RUNTIME_CLASS obiektu pochodzącego z [CWinThread](../../mfc/reference/cwinthread-class.md).

*pParam ( pParam )*\
Parametr, który należy przekazać do funkcji sterującej.

*nPriority*\
Priorytet, aby ustawić dla wątku. Aby uzyskać pełną listę i opis dostępnych priorytetów, zobacz [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) w zestawie Windows SDK.

*rozmiar nStackSize*\
Określa rozmiar w bajtach stosu dla nowego wątku. Jeśli 0, rozmiar stosu domyślnie stosu tego samego rozmiaru jako wątku tworzenia.

*dwCreateSlags*\
Określa dodatkową flagę, która steruje tworzeniem wątku. Ta flaga może zawierać jedną z dwóch wartości:

- CREATE_SUSPENDED Rozpocznij wątek z liczbą wstrzymania jednego. Użyj CREATE_SUSPENDED, jeśli chcesz zainicjować wszelkie dane `CWinThread` członkowskie obiektu, takie jak [m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete) lub dowolnych członków klasy pochodnej, przed uruchomieniem wątku. Po zakończeniu inicjowania użyj [CWinThread::ResumeThread,](../../mfc/reference/cwinthread-class.md#resumethread) aby uruchomić wątek. Wątek nie zostanie `CWinThread::ResumeThread` wykonany, dopóki nie zostanie wywołany.

- **0** Rozpocznij wątek natychmiast po utworzeniu.

*lpSecurityAttrs*\
Wskazuje strukturę [SECURITY_ATTRIBUTES,](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) która określa atrybuty zabezpieczeń wątku. Jeśli null, te same atrybuty zabezpieczeń jako wątku tworzenia są używane. Aby uzyskać więcej informacji na temat tej struktury, zobacz Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzonego obiektu wątku lub NULL, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Pierwsza forma `AfxBeginThread` tworzy wątek roboczy. Drugi formularz tworzy wątek, który może służyć jako wątek interfejsu użytkownika lub jako wątek roboczy.

`AfxBeginThread`tworzy nowy `CWinThread` obiekt, wywołuje jego [CreateThread](../../mfc/reference/cwinthread-class.md#createthread) funkcji, aby rozpocząć wykonywanie wątku i zwraca wskaźnik do wątku. Kontrole są dokonywane w całej procedurze, aby upewnić się, że wszystkie obiekty są cofnięte alokacji poprawnie, jeśli jakakolwiek część tworzenia zakończy się niepowodzeniem. Aby zakończyć wątek, wywołać [AfxEndThread](#afxendthread) z wewnątrz wątku lub powrócić z funkcji sterującej wątku roboczego.

Aplikacja musi włączyć wielowątkowężą; w przeciwnym razie ta funkcja zakończy się niepowodzeniem. Aby uzyskać więcej informacji na temat włączania wielowątkowych, zobacz [/MD, /MT, /LD (Użyj biblioteki czasu wykonywania)](../../build/reference/md-mt-ld-use-run-time-library.md).

Aby uzyskać `AfxBeginThread`więcej informacji na temat , zobacz artykuły [Wielowątkowe: Tworzenie wątków roboczych](../../parallel/multithreading-creating-worker-threads.md) i [wielowątkowe: Tworzenie wątków interfejsu użytkownika](../../parallel/multithreading-creating-user-interface-threads.md).

### <a name="example"></a>Przykład

Zobacz przykład [CSocket::Attach](../../mfc/reference/csocket-class.md#attach).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

## <a name="afxcontextmenumanager"></a><a name="afxcontextmenumanager"></a>AfxContextMenuManager

Wskaźnik do globalnego [menedżera menu kontekstowego](ccontextmenumanager-class.md).

### <a name="syntax"></a>Składnia

```cpp
CContextMenuManager* afxContextMenuManager;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxcontextmenumanager.h

## <a name="afxendthread"></a><a name="afxendthread"></a>AfxEndThread (AfxEndThread)

Wywołanie tej funkcji, aby zakończyć aktualnie wykonywany wątek.

```cpp
void AFXAPI AfxEndThread(
    UINT nExitCode,
    BOOL bDelete  = TRUE);
```

### <a name="parameters"></a>Parametry

*Kod nExitCode*\
Określa kod zakończenia wątku.

*bDelete*\
Usuwa obiekt wątku z pamięci.

### <a name="remarks"></a>Uwagi

Musi być wywołana z wewnątrz wątku, aby zakończyć.

Aby uzyskać `AfxEndThread`więcej informacji na temat , zobacz artykuł [Wielowątkowe: Kończenie wątków](../../parallel/multithreading-terminating-threads.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

## <a name="afxfindresourcehandle"></a><a name="afxfindresourcehandle"></a>AfxFindResourceHandle

Służy `AfxFindResourceHandle` do chodzenia po łańcuchu zasobów i lokalizowania określonego zasobu według identyfikatora zasobu i typu zasobu.

### <a name="syntax"></a>Składnia

```cpp
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );
```

### <a name="parameters"></a>Parametry

*Lpszname*\
Wskaźnik do ciągu zawierającego identyfikator zasobu.
*lpszType (typ)*\
Wskaźnik do typu zasobu. Aby uzyskać listę typów zasobów, zobacz [FindResource](/windows/win32/api/winbase/nf-winbase-findresourcea) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Dojście do modułu, który zawiera zasób.

### <a name="remarks"></a>Uwagi

`AfxFindResourceHandle`znajduje określony zasób i zwraca dojście do modułu, który zawiera zasób. Zasób może znajdować się w dowolnej biblioteki DLL rozszerzenia MFC, która jest ładowana. `AfxFindResourceHandle`informuje, który z nich ma zasób.

Moduły są przeszukiwane w następującej kolejności:

1. Moduł główny, jeśli jest to biblioteka DLL rozszerzenia MFC.

1. Moduły niesystemowe.

1. Moduły specyficzne dla języka.

1. Moduł główny, jeśli jest to biblioteka DLL systemu.

1. Moduły systemowe.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="afxfreelibrary"></a><a name="afxfreelibrary"></a>AfxFreeLibrary

Zarówno `AfxFreeLibrary` `AfxLoadLibrary` i zachować liczbę odwołań dla każdego załadowanego modułu biblioteki.

```cpp
BOOL AFXAPI AfxFreeLibrary(HINSTANCE hInstLib);
```

### <a name="parameters"></a>Parametry

*hInstLib (właśc.*\
Uchwyt załadowanego modułu biblioteki. [AfxLoadLibrary](#afxloadlibrary) zwraca ten uchwyt.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli funkcja powiedzie się; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

`AfxFreeLibrary`zmniejsza liczbę odwołań załadowanego modułu biblioteki dynamicznej (DLL). Gdy liczba odwołań osiągnie zero, moduł jest odmapowany z przestrzeni adresowej procesu wywołującego, a dojście nie jest już prawidłowe. Ta liczba odwołań jest zwiększana za każdym razem, gdy `AfxLoadLibrary` jest wywoływana.

Przed odblożeniem modułu biblioteki system umożliwia biblioteki DLL odłączanie się od procesów, które go używają. Dzięki temu biblioteka DLL umożliwia oczyszczenie zasobów przydzielonych dla bieżącego procesu. Po powrocie funkcji punktu wejścia moduł biblioteki jest usuwany z przestrzeni adresowej bieżącego procesu.

Służy `AfxLoadLibrary` do mapowania modułu DLL.

Należy użyć `AfxFreeLibrary` i `AfxLoadLibrary` (zamiast funkcji `FreeLibrary` Win32 `LoadLibrary`i), jeśli aplikacja używa wielu wątków. Przy `AfxLoadLibrary` `AfxFreeLibrary` użyciu i zapewnia, że kod uruchamiania i zamykania, który jest wykonywany, gdy biblioteka DLL rozszerzenia MFC jest ładowany i zwalniane nie jest uszkodzony globalny stan MFC.

### <a name="example"></a>Przykład

Zobacz przykład [afxLoadlibrary](#afxloadlibrary).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdll_.h

## <a name="afxgetapp"></a><a name="afxgetapp"></a>AfxGetApp (AfxGetApp)

Wskaźnik zwracany przez tę funkcję może służyć do uzyskiwania dostępu do informacji o aplikacji, takich jak kod wysyłki wiadomości głównej lub okno najwyższej.

```cpp
CWinApp* AFXAPI AfxGetApp();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pojedynczego `CWinApp` obiektu dla aplikacji.

### <a name="remarks"></a>Uwagi

Jeśli ta metoda zwraca wartość NULL, może to oznaczać, że okno główne aplikacji nie zostało jeszcze w pełni zainicjowane. Może to również wskazywać na problem.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#126](../../mfc/reference/codesnippet/cpp/application-information-and-management_1.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

## <a name="afxgetappname"></a><a name="afxgetappname"></a>AfxGetAppName (Nazwa aplikacji AfxGetAppName)

Zwracany ciąg może służyć do wiadomości diagnostycznych lub jako katalog główny dla tymczasowych nazw ciągów.

```cpp
LPCTSTR AFXAPI AfxGetAppName();
```

### <a name="return-value"></a>Wartość zwracana

Ciąg zakończony z wartością null zawierający nazwę aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#127](../../mfc/reference/codesnippet/cpp/application-information-and-management_2.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

## <a name="afxgetinstancehandle"></a><a name="afxgetinstancehandle"></a>AfxGetInstanceHandle (Uchwyt afxgetinstance)

Ta funkcja umożliwia pobranie dojścia wystąpienia bieżącej aplikacji.

```cpp
HINSTANCE  AFXAPI AfxGetInstanceHandle();
```

### <a name="return-value"></a>Wartość zwracana

HINSTANCE do bieżącego wystąpienia aplikacji. Jeśli wywoływane z poziomu biblioteki DLL połączone z usrdll wersji MFC, HINSTANCE do biblioteki DLL jest zwracany.

### <a name="remarks"></a>Uwagi

`AfxGetInstanceHandle`zawsze zwraca HINSTANCE pliku wykonywalnego (. EXE), chyba że jest wywoływana z poziomu biblioteki DLL połączonej z wersją USRDLL MFC. W takim przypadku zwraca HINSTANCE do biblioteki DLL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

## <a name="afxgetmainwnd"></a><a name="afxgetmainwnd"></a>AfxGetMainWnd (AfxGetMainWnd)

Jeśli aplikacja jest serwerem OLE, należy wywołać tę funkcję, aby pobrać wskaźnik do aktywnego okna głównego aplikacji. Użyj tego wyniku zamiast bezpośrednio odwoływać się do [m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd) elementu członkowskiego obiektu aplikacji.

```cpp
CWnd* AFXAPI AfxGetMainWnd();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do obiektu okna ramki, który zawiera aktywny dokument w miejscu, jeśli serwer ma obiekt, który jest aktywny w miejscu wewnątrz aktywnego kontenera.

Jeśli nie ma żadnego obiektu, który jest aktywny w miejscu w kontenerze lub aplikacja nie jest serwerem OLE, ta funkcja zwraca *m_pMainWnd* obiektu aplikacji.

Jeśli `AfxGetMainWnd` jest wywoływana z wątku podstawowego aplikacji, zwraca główne okno aplikacji zgodnie z powyższymi regułami. Jeśli funkcja jest wywoływana z wątku pomocniczego w aplikacji, funkcja zwraca okno główne skojarzone z wątku, który dokonał wywołania.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja nie jest serwerem OLE, wywołanie tej funkcji jest równoznaczne bezpośrednio odwołując się do *m_pMainWnd* członka obiektu aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#129](../../mfc/reference/codesnippet/cpp/application-information-and-management_4.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

## <a name="afxgetperuserregistration"></a><a name="afxgetperuserregistration"></a>AfxGetPerUserRegistration AfxGetPerUserRegistration AfxGetPerUserRegistration Afx

Ta funkcja służy do określania, czy aplikacja przekierowuje dostęp rejestru do węzła **HKEY_CURRENT_USER** **(HKCU).**

```cpp
BOOL AFXAPI AfxGetPerUserRegistration();
```

### <a name="return-value"></a>Wartość zwracana

WARTOŚĆ TRUE wskazuje, że informacje o rejestrze są kierowane do węzła HKCU. FALSE wskazuje, że aplikacja zapisuje informacje rejestru w węźle domyślnym. Domyślnym węzłem jest **HKEY_CLASSES_ROOT** **(HKCR).**

### <a name="remarks"></a>Uwagi

Jeśli włączysz przekierowanie rejestru, struktura przekierowuje dostęp z **HKCR** do **HKEY_CURRENT_USER\Software\Classes**. Przekierowanie dotyczy tylko struktur MFC i ATL.

Aby zmienić, czy aplikacja przekierowuje dostęp do rejestru, użyj [afxSetPerUserRegistration](#afxsetperuserregistration).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxstat_.h

## <a name="afxgetresourcehandle"></a><a name="afxgetresourcehandle"></a>AfxGetResourceHandle (AfxGetResourceHandle)

Użyj dojścia HINSTANCE zwróconego przez tę funkcję, aby uzyskać bezpośredni dostęp `FindResource`do zasobów aplikacji, na przykład w wywołaniach funkcji systemu Windows .

```cpp
extern HINSTANCE  AfxGetResourceHandle();
```

### <a name="return-value"></a>Wartość zwracana

Dojście HINSTANCE, w którym są ładowane domyślne zasoby aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

## <a name="afxgetthread"></a><a name="afxgetthread"></a>AfxGetThread (AfxGetThread)

Wywołanie tej funkcji, aby uzyskać wskaźnik do [CWinThread](../../mfc/reference/cwinthread-class.md) obiektu reprezentującego aktualnie wykonywany wątek.

```cpp
CWinThread* AfxGetThread();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do aktualnie wykonywanego wątku; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Musi być wywołana z wewnątrz wątku.

> [!NOTE]
> Jeśli przenosisz projekt MFC `AfxGetThread` wywołujący z programu Visual C++ w wersji 4.2, 5.0 lub 6.0, wywołuje `AfxGetThread` [AfxGetApp,](#afxgetapp) jeśli nie znaleziono wątku. W nowszych wersjach `AfxGetThread` kompilatora zwraca wartość NULL, jeśli nie znaleziono wątku. Jeśli chcesz wątku aplikacji, `AfxGetApp`należy wywołać .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

## <a name="afxinitrichedit"></a><a name="afxinitrichedit"></a>AfxInitRichEdytuj

Wywołanie tej funkcji, aby zainicjować formant edycji bogatej (wersja 1.0) dla aplikacji.

```cpp
BOOL AFXAPI AfxInitRichEdit();
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest dostępna dla zgodności z powrotem. Nowe aplikacje powinny używać [AfxInitRichEdit2](#afxinitrichedit2).

`AfxInitRichEdit`ładunki RICHED32. DLL, aby zainicjować wersję 1.0 formantu edycji bogatej. Aby użyć wersji 2.0 i 3.0 formantu edycji bogatej, RICHED20. DLL musi zostać załadowany. Jest ładowany przez wywołanie [AfxInitRichEdit2](#afxinitrichedit2).

Aby zaktualizować zaawansowane kontrolki edycji w istniejących aplikacjach Visual C++ do wersji 2.0, otwórz plik . RC jako tekst, zmień nazwę klasy każdego formantu edycji rich z "RICHEDIT" na "RichEdit20a". Następnie zastąp połączenie na `AfxInitRichEdit` . `AfxInitRichEdit2`

Ta funkcja inicjuje również bibliotekę typowych kontrolek, jeśli biblioteka nie została jeszcze zainicjowana dla procesu. Jeśli używasz formantu edycji bogatej bezpośrednio z aplikacji MFC, wywołanie tej funkcji, aby upewnić się, że MFC poprawnie zainicjował rich edit control runtime. Jeśli wywołasz `Create` metodę [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md)lub [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), zazwyczaj nie trzeba wywoływać tej funkcji, ale w niektórych przypadkach może być konieczne.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

## <a name="afxinitrichedit2"></a><a name="afxinitrichedit2"></a>AfxInitRichEdit2

Wywołanie tej funkcji, aby zainicjować formant edycji bogatej (wersja 2.0 i nowsze) dla aplikacji.

```cpp
BOOL AFXAPI AfxInitRichEdit2();
```

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby załadować RICHED20. DLL i zainicjować wersję 2.0 formantu edycji bogatej. Jeśli wywołasz `Create` metodę [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md)lub [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), zazwyczaj nie trzeba wywoływać tej funkcji, ale w niektórych przypadkach może być konieczne.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

## <a name="afxisextendedframeclass"></a><a name="afxisextendedframeclass"></a>AfxIsExtendedFrameClass

Określa, czy dane okno jest obiektem ramki rozszerzonej.

### <a name="syntax"></a>Składnia

```cpp
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );
```

### <a name="parameters"></a>Parametry

*Pwnd*\
[w] Wskaźnik do obiektu, który pochodzi `CWnd`od .

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli podane okno jest obiektem rozszerzonej ramki; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość TRUE, jeśli *pWnd* pochodzi z jednej z następujących klas:

- `CFrameWndEx`

- `CMDIFrameWndEx`

- `COleIPFrameWndEx`

- `COleDocIPFrameWndEx`

- `CMDIChildWndEx`

Ta metoda jest przydatna, gdy trzeba sprawdzić, czy parametr funkcji lub metody jest rozszerzonym oknem ramki.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxpriv.h

## <a name="afxismfctoolbar"></a><a name="afxismfctoolbar"></a>Pasek AfxIsMFCToolBar

Określa, czy dane okno jest obiektem paska narzędzi.

### <a name="syntax"></a>Składnia

```cpp
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*Pwnd*\
[w] Wskaźnik do obiektu, który pochodzi `CWnd`od .

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli podane okno jest obiektem paska narzędzi; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda `TRUE` zwraca, jeśli *pWnd* pochodzi od `CMFCToolBar`. Ta metoda jest przydatna, gdy trzeba sprawdzić, czy `CMFCToolBar` funkcja lub metoda parametr jest obiektem.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxpriv.h

## <a name="afxkeyboardmanager"></a><a name="afxkeyboardmanager"></a>AfxKeyboardManager

Wskaźnik do globalnego [menedżera klawiatury](ckeyboardmanager-class.md).

### <a name="syntax"></a>Składnia

```cpp
CKeyboardManager* afxKeyboardManager;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxkeyboardmanager.h

## <a name="afxloadlibrary"></a><a name="afxloadlibrary"></a>Afxloadlibrary

Służy `AfxLoadLibrary` do mapowania modułu DLL.

```cpp
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName);
```

### <a name="parameters"></a>Parametry

*lpszModuleName*\
Wskazuje ciąg zakończony zerem, który zawiera nazwę modułu (albo a . DLL lub . EXE). Określona nazwa jest nazwą pliku modułu.

Jeśli ciąg określa ścieżkę, ale plik nie istnieje w określonym katalogu, funkcja kończy się niepowodzeniem.

Jeśli ścieżka nie zostanie określona, a rozszerzenie nazwy pliku zostanie pominięte, domyślne rozszerzenie . Biblioteka DLL jest dołączana. Jednak ciąg nazwy pliku może zawierać znak punktu końcowego (.), aby wskazać, że nazwa modułu nie ma rozszerzenia. Jeśli nie określono żadnej ścieżki, funkcja używa [kolejności wyszukiwania dla aplikacji klasycznych](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications).

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się, zwracana wartość jest dojściem do modułu. W przypadku awarii zwracana wartość to NULL.

### <a name="remarks"></a>Uwagi

Zwraca dojście, który może służyć w [GetProcAddress,](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) aby uzyskać adres funkcji DLL. `AfxLoadLibrary`może być również używany do mapowania innych modułów wykonywalnych.

Każdy proces zachowuje liczbę odwołań dla każdego załadowanego modułu biblioteki. Ta liczba odwołań jest zwiększana za każdym razem `AfxLoadLibrary` jest `AfxFreeLibrary` wywoływana i jest zmniejszana za każdym razem jest wywoływana. Gdy liczba odwołań osiągnie zero, moduł jest odmapowany z przestrzeni adresowej procesu wywołującego, a dojście nie jest już prawidłowe.

Należy użyć `AfxLoadLibrary` i `AfxFreeLibrary` (zamiast funkcji `LoadLibrary` Win32 `FreeLibrary`i), jeśli aplikacja używa wielu wątków i jeśli dynamicznie ładuje DLL rozszerzenia MFC. Przy `AfxLoadLibrary` `AfxFreeLibrary` użyciu i zapewnia, że kod uruchamiania i zamykania, który wykonuje, gdy biblioteka DLL rozszerzenia MFC jest ładowany i zwalniane nie uszkadza globalnego stanu MFC.

Korzystanie `AfxLoadLibrary` z aplikacji wymaga dynamicznego łączenia z wersją DLL MFC. Plik nagłówka `AfxLoadLibrary`dla , Afxdll_.h, jest uwzględniany tylko wtedy, gdy MFC jest połączony z aplikacją jako biblioteka DLL. To wymaganie jest zgodnie z projektem, ponieważ trzeba połączyć się z wersją DLL MFC do użycia lub utworzenia bibliotek DLL rozszerzenia MFC.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_DLLUser#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]
[!code-cpp[NVC_MFC_DLLUser#2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]
[!code-cpp[NVC_MFC_DLLUser#3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdll_.h

## <a name="afxloadlibraryex"></a><a name="afxloadlibraryex"></a>AfxLoadLibraryEx

Służy `AfxLoadLibraryEx` do mapowania modułu DLL.

```cpp
HINSTANCE AFXAPI AfxLoadLibraryEx(LPCTSTR lpFileName, HANDLE hFile, DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*lpFileName*\
Wskazuje ciąg zakończony zerem, który zawiera nazwę modułu (albo a . DLL lub . EXE). Określona nazwa jest nazwą pliku modułu.

Jeśli ciąg określa ścieżkę, ale plik nie istnieje w określonym katalogu, funkcja kończy się niepowodzeniem.

Jeśli ścieżka nie zostanie określona, a rozszerzenie nazwy pliku zostanie pominięte, domyślne rozszerzenie . Biblioteka DLL jest dołączana. Jednak ciąg nazwy pliku może zawierać znak punktu końcowego (.), aby wskazać, że nazwa modułu nie ma rozszerzenia. Jeśli nie określono żadnej ścieżki, funkcja używa [kolejności wyszukiwania dla aplikacji klasycznych](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications).

*hFile (plik)*\
Ten parametr jest zarezerwowany do użytku w przyszłości. Musi być null.

*Dwflags*\
Akcja, która ma zostać podjęta podczas ładowania modułu. Jeśli nie flagi są określone, zachowanie tej `AfxLoadLibrary` funkcji jest identyczna z funkcją. Możliwe wartości tego parametru są opisane w dokumentacji [LoadLibraryEx.](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się, zwracana wartość jest dojściem do modułu. W przypadku awarii zwracana wartość to NULL.

### <a name="remarks"></a>Uwagi

`AfxLoadLibraryEx`zwraca dojście, który może służyć w [GetProcAddress,](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) aby uzyskać adres funkcji DLL. `AfxLoadLibraryEx`może być również używany do mapowania innych modułów wykonywalnych.

Każdy proces zachowuje liczbę odwołań dla każdego załadowanego modułu biblioteki. Ta liczba odwołań jest zwiększana za każdym razem `AfxLoadLibraryEx` jest `AfxFreeLibrary` wywoływana i jest zmniejszana za każdym razem jest wywoływana. Gdy liczba odwołań osiągnie zero, moduł jest odmapowany z przestrzeni adresowej procesu wywołującego, a dojście nie jest już prawidłowe.

Należy użyć `AfxLoadLibraryEx` i `AfxFreeLibrary` (zamiast funkcji `LoadLibraryEx` Win32 `FreeLibrary`i), jeśli aplikacja używa wielu wątków i jeśli dynamicznie ładuje DLL rozszerzenia MFC. Przy `AfxLoadLibraryEx` `AfxFreeLibrary` użyciu i zapewnia, że kod uruchamiania i zamykania, który jest wykonywany, gdy biblioteka DLL rozszerzenia MFC jest ładowany i zwalniane nie jest uszkodzony globalny stan MFC.

Korzystanie `AfxLoadLibraryEx` z aplikacji wymaga dynamicznego łączenia z wersją DLL MFC. Plik nagłówka `AfxLoadLibraryEx`dla , Afxdll_.h, jest uwzględniany tylko wtedy, gdy MFC jest połączony z aplikacją jako biblioteka DLL. To wymaganie jest zgodnie z projektem, ponieważ trzeba połączyć się z wersją DLL MFC do użycia lub utworzenia bibliotek DLL rozszerzenia MFC.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdll_.h

## <a name="afxmenutearoffmanager"></a><a name="afxmenutearoffmanager"></a>AfxMenuTearOffManager

Wskaźnik do globalnego [menedżera menu odrywać](cmenutearoffmanager-class.md).

### <a name="syntax"></a>Składnia

```cpp
CMenuTearOffManager* g_pTearOffMenuManager;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmenutearoffmanager.h

## <a name="afxmousemanager"></a><a name="afxmousemanager"></a>AfxMouseManager

Wskaźnik do globalnego [menedżera myszy](cmousemanager-class.md).

### <a name="syntax"></a>Składnia

```cpp
CMouseManager* afxMouseManager;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmousemanager.h

## <a name="afxregisterclass"></a><a name="afxregisterclass"></a>AfxRegisterClass ( AfxRegisterClass )

Ta funkcja służy do rejestrowania klas okien w biblioteki DLL, która używa MFC.

```cpp
BOOL AFXAPI AfxRegisterClass(WNDCLASS* lpWndClass);
```

### <a name="parameters"></a>Parametry

*lpWndClass*\
Wskaźnik do struktury [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) zawierający informacje o klasie okna, która ma zostać zarejestrowana. Aby uzyskać więcej informacji na temat tej struktury, zobacz Windows SDK.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli klasa została pomyślnie zarejestrowana; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli używasz tej funkcji, klasa jest automatycznie wyrejestrowany, gdy biblioteka DLL jest zwalniana.

W kompilacjach innych niż `AfxRegisterClass` DLL identyfikator jest zdefiniowany jako makro, które mapuje do funkcji `RegisterClass`systemu Windows, ponieważ klasy zarejestrowane w aplikacji są automatycznie wyrejestrowane. Jeśli używasz `AfxRegisterClass` zamiast `RegisterClass`, kod może być używany bez zmian zarówno w aplikacji, jak i w dll.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_DLL#3](../../atl-mfc-shared/codesnippet/cpp/application-information-and-management_10.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

## <a name="afxregisterwndclass"></a><a name="afxregisterwndclass"></a>Afxregisterwndclass

Umożliwia rejestrację własnych klas okiennych.

```cpp
LPCTSTR AFXAPI AfxRegisterWndClass(
    UINT nClassStyle,
    HCURSOR hCursor = 0,
    HBRUSH hbrBackground = 0,
    HICON hIcon = 0);
```

### <a name="parameters"></a>Parametry

*styl nClassStyle*\
Określa styl klasy systemu Windows lub kombinację stylów utworzonych przy użyciu operatora bitowego OR** (&#124;**) dla klasy okna. Aby uzyskać listę stylów klas, zobacz strukturę [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) w zestawie Windows SDK. Jeśli null, wartości domyślne są ustawione w następujący sposób:

- Ustawia styl myszy na CS_DBLCLKS, który wysyła wiadomości dwukrotnego kliknięcia do procedury okna, gdy użytkownik kliknie dwukrotnie myszą.

- Ustawia styl kursora strzałki na standardowy IDC_ARROW systemu Windows.

- Ustawia pędzel tła na NULL, dzięki czemu okno nie będzie wymazać jego tła.

- Ustawia ikonę na standardową ikonę logo systemu Windows z flagą machającą flagą.

*hCursor (własno)-do*\
Określa dojście do zasobu kursora, które ma być zainstalowane w każdym oknie utworzonym z klasy okna. Jeśli używasz domyślnego **0,** otrzymasz standardowy kursor IDC_ARROW.

*hbrBackground (ziemia)*\
Określa dojście do zasobu pędzla, które ma być zainstalowane w każdym oknie utworzonym z klasy okna. Jeśli używasz domyślnego **0**, będziesz mieć pędzel tła NULL i domyślnie okno nie będzie wymazać jego tła podczas przetwarzania [WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd).

*hIcon (własówce)*\
Określa dojście do zasobu ikony, które ma być zainstalowane w każdym oknie utworzonym z klasy okna. Jeśli używasz domyślnie **0**, otrzymasz standardową, machającą flagę logo Windows ikonę.

### <a name="return-value"></a>Wartość zwracana

Ciąg zakończony z wartością null zawierający nazwę klasy. Można przekazać tę nazwę `Create` klasy do `CWnd` funkcji elementu członkowskiego w lub innych klas **pochodnych CWnd,** aby utworzyć okno. Nazwa jest generowana przez bibliotekę klas Programu Microsoft Foundation.

> [!NOTE]
> Zwracana wartość jest wskaźnikiem do buforu statycznego. Aby zapisać ten ciąg, `CString` przypisz go do zmiennej.

### <a name="remarks"></a>Uwagi

Biblioteka klas programu Microsoft Foundation automatycznie rejestruje kilka standardowych klas okien. Wywołanie tej funkcji, jeśli chcesz zarejestrować własne klasy okna.

Nazwa zarejestrowana dla `AfxRegisterWndClass` klasy przez zależy wyłącznie od parametrów. Jeśli wywołasz `AfxRegisterWndClass` wiele razy z identycznymi parametrami, rejestruje tylko klasę przy pierwszym wywołaniu. Późniejsze `AfxRegisterWndClass` wywołania z identycznymi parametrami zwracają już zarejestrowaną klasę.

Jeśli wywołasz `AfxRegisterWndClass` dla wielu klas pochodnych CWnd z identycznymi parametrami, zamiast uzyskiwania oddzielnej klasy okna dla każdej klasy, każda klasa współużytkuje tę samą klasę okna. To udostępnianie może powodować problemy, jeśli używany jest styl klasy CS_CLASSDC. Zamiast wielu klas CS_CLASSDC okna, kończy się tylko jedną CS_CLASSDC klasę okna. Wszystkie okna języka C++, które używają tej klasy współużytkują ten sam kontroler domeny. Aby uniknąć tego problemu, wywołaj [AfxRegisterClass,](#afxregisterclass) aby zarejestrować klasę.

Zobacz uwaga techniczna [TN001: Rejestracja klasy okna, aby](../../mfc/tn001-window-class-registration.md) uzyskać więcej informacji na temat rejestracji klasy okna i `AfxRegisterWndClass` funkcji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

## <a name="afxsetperuserregistration"></a><a name="afxsetperuserregistration"></a>AfxSetPerUserRegistration

Określa, czy aplikacja przekierowuje dostęp rejestru do węzła **HKEY_CURRENT_USER** **(HKCU).**

```cpp
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bWłaszą*\
[w] WARTOŚĆ TRUE wskazuje, że informacje o rejestrze są kierowane do węzła HKCU. FALSE wskazuje, że aplikacja zapisuje informacje rejestru w węźle domyślnym. Domyślnym węzłem jest **HKEY_CLASSES_ROOT** **(HKCR).**

### <a name="remarks"></a>Uwagi

Przed systemem Windows Vista aplikacje, które uzyskały dostęp do rejestru, często używały **węzła HKEY_CLASSES_ROOT.** Jednak w systemach operacyjnych Windows Vista lub nowszych należy uruchomić aplikację w trybie podwyższonego poziomu, aby zapisać do HKCR.

Ta metoda umożliwia aplikacji do odczytu i zapisu w rejestrze bez uruchamiania w trybie podwyższonego poziomu. Działa poprzez przekierowanie dostępu do rejestru z HKCR do HKCU. Aby uzyskać więcej informacji, zobacz [Strony właściwości konsoli .](../../build/reference/linker-property-pages.md)

Jeśli włączysz przekierowanie rejestru, struktura przekierowuje dostęp z HKCR do **HKEY_CURRENT_USER\Software\Classes**. Przekierowanie dotyczy tylko struktur MFC i ATL.

Domyślna implementacja uzyskuje dostęp do rejestru w obszarze HKCR.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxstat_.h

## <a name="afxsetresourcehandle"></a><a name="afxsetresourcehandle"></a>AfxSetResourceHandle

Ta funkcja służy do ustawiania dojścia HINSTANCE, który określa, gdzie są ładowane domyślne zasoby aplikacji.

```cpp
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);
```

### <a name="parameters"></a>Parametry

*hInstResource (Źródło)*\
Wystąpienie lub dojście modułu do . EXE lub DLL, z którego są ładowane zasoby aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#135](../../mfc/reference/codesnippet/cpp/application-information-and-management_12.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

## <a name="afxshellmanager"></a><a name="afxshellmanager"></a>AfxShellManager (AfxShellManager)

Wskaźnik do globalnego [menedżera powłoki](cshellmanager-class.md).

### <a name="syntax"></a>Składnia

```cpp
CShellManager* afxShellManager;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxshellmanager.h

## <a name="afxsocketinit"></a><a name="afxsocketinit"></a>Afxsocketinit

Wywołanie tej `CWinApp::InitInstance` funkcji w zastąpienie zainicjować gniazda systemu Windows.

```cpp
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);
```

### <a name="parameters"></a>Parametry

*lpwsaData*\
Wskaźnik do struktury [WSADATA.](/windows/win32/api/winsock2/ns-winsock2-wsadata) Jeśli *lpwsaData* nie jest równa NULL, adres `WSADATA` struktury jest wypełniany `WSAStartup`przez wywołanie . Ta funkcja zapewnia `WSACleanup` również, że jest wywoływana przed zakończeniem aplikacji.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Podczas korzystania z gniazd MFC w wątkach pomocniczych w statycznie połączonej aplikacji MFC, należy wywołać `AfxSocketInit` w każdym wątku, który używa gniazd do inicjowania bibliotek gniazd. Domyślnie `AfxSocketInit` jest wywoływana tylko w wątku podstawowym.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxsock.h

## <a name="afxusertoolsmanager"></a><a name="afxusertoolsmanager"></a>AfxUserToolsManager

Wskaźnik do globalnego [menedżera narzędzi użytkownika](cusertoolsmanager-class.md).

### <a name="syntax"></a>Składnia

```cpp
CUserToolsManager* afxUserToolsManager;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxusertoolsmanager.h

## <a name="afxwininit"></a><a name="afxwininit"></a>AfxWinInit ( AfxWinInit )

Ta funkcja jest wywoływana przez `WinMain` funkcję dostarczoną przez MFC, jako część inicjowania aplikacji opartej na interfejsie użytkownika [CWinApp,](../../mfc/reference/cwinapp-class.md) aby zainicjować MFC.

```cpp
BOOL AFXAPI AfxWinInit(
    HINSTANCE hInstance,
    HINSTANCE hPrevInstance,
    LPTSTR lpCmdLine,
    int nCmdShow);
```

### <a name="parameters"></a>Parametry

*hInstance (Nieumieja)*\
Uchwyt aktualnie uruchomionego modułu.

*hPrevInstance*\
Dojście do poprzedniego wystąpienia aplikacji. W przypadku aplikacji opartej na win32 ten parametr jest zawsze **null**.

*lpCmdLine (linia lpCmdLine)*\
Wskazuje ciąg zakończony zerem określający wiersz polecenia dla aplikacji.

*nCmdShow*\
Określa sposób pokazywanych głównego okna aplikacji graficznej.

### <a name="remarks"></a>Uwagi

Dla aplikacji konsoli, która nie używa funkcji `WinMain` dostarczonej przez `AfxWinInit` MFC, należy wywołać bezpośrednio, aby zainicjować MFC.

Jeśli wywołasz `AfxWinInit` siebie, należy zadeklarować `CWinApp` wystąpienie klasy. W przypadku aplikacji konsoli można nie czerpać z `CWinApp` własnej klasy i `CWinApp` zamiast tego użyć wystąpienia bezpośrednio. Ta technika jest odpowiednia, jeśli zdecydujesz się pozostawić wszystkie funkcje dla aplikacji w implementacji **main**.

> [!NOTE]
> Gdy tworzy kontekst aktywacji dla zestawu, MFC używa zasobu manifestu dostarczonego przez moduł użytkownika. Kontekst aktywacji jest `AfxWinInit`tworzony w pliku . Aby uzyskać więcej informacji, zobacz [Obsługa kontekstów aktywacji w stanie modułu MFC](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxwin.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](mfc-macros-and-globals.md)\
[Klasa CWinApp](cwinapp-class.md)\
[CContextMenuManager, klasa](ccontextmenumanager-class.md)\
[Klasa CWnd](cwnd-class.md)\
[Klasa CFrameWndEx](cframewndex-class.md)\
[Klasa CMFCToolBar](cmfctoolbar-class.md)\
[Klasa CKeyboardManager](ckeyboardmanager-class.md)\
[Klasa CMenuTearOffManager](cmenutearoffmanager-class.md)\
[Klasa CMouseManager](cmousemanager-class.md)\
[Klasa CShellManager](cshellmanager-class.md)\
[Klasa CUserToolsManager](cusertoolsmanager-class.md)
