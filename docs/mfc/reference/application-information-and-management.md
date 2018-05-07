---
title: Informacje o aplikacji i zarządzania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41b6aa602956c6dcdeda8f6b8c24c1be48c58ce2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="application-information-and-management"></a>Informacje o aplikacji i zarządzanie nią
Podczas pisania aplikacji, Utwórz jeden [CWinApp](../../mfc/reference/cwinapp-class.md)-pochodzi z obiektu. W czasie, może zajść potrzeba uzyskania informacji na temat tego obiektu wynikające ze poza `CWinApp`-pochodzi z obiektu. Lub może być wymagany dostęp do innych obiektów globalnych "mananger".
  
 Microsoft Foundation Class Library zapewnia następujące funkcje globalne ułatwiają wykonanie tych zadań:  
  
### <a name="application-information-and-management-functions"></a>Informacje o aplikacji i funkcji zarządzania  
  
|||  
|-|-|  
|[Afxbeginthread —](#afxbeginthread)|Tworzy nowego wątku.|  
|[Afxcontextmenumanager —](#afxcontextmenumanager)|Wskaźnik do globalnej [Menedżera menu kontekstowe](ccontextmenumanager-class.md).|
|[AfxEndThread](#afxendthread)|Kończy bieżącego wątku.|  
|[Afxfindresourcehandle —](#afxfindresourcehandle)|Zawiera opis łańcucha zasobów i Znajdź określony identyfikator zasobu przez zasobów i typu zasobu. |
|[AfxFreeLibrary](#afxfreelibrary)|Zmniejsza odwołanie liczba modułu załadować biblioteki dołączanej (dynamicznie DLL); Jeśli liczba odwołań do zera, moduł jest Niemapowane.|  
|[Afxgetapp —](#afxgetapp)|Zwraca wskaźnik do aplikacji przez jednego `CWinApp` obiektu.|  
|[Afxgetappname —](#afxgetappname)|Zwraca ciąg zawierający nazwę aplikacji.|  
|[Afxgetinstancehandle —](#afxgetinstancehandle)|Zwraca `HINSTANCE` reprezentujący to wystąpienie aplikacji.|  
|[Afxgetmainwnd —](#afxgetmainwnd)|Zwraca wskaźnik do bieżącego okna "main" z aplikacji innych niż OLE lub okno ramowe w miejscu aplikacji serwera.|  
|[Afxgetperuserregistration —](#afxgetperuserregistration)|Ta funkcja służy do określenia, czy aplikacja przekierowuje dostęp do rejestru **HKEY_CURRENT_USER** ( **HKCU**) węzła.|  
|[Afxgetresourcehandle —](#afxgetresourcehandle)|Zwraca `HINSTANCE` w źródle aplikacji domyślnych zasobów. Umożliwia dostęp do zasobów aplikacji bezpośrednio.|  
|[Afxgetthread —](#afxgetthread)|Pobiera wskaźnik do bieżącego [cwinthread —](../../mfc/reference/cwinthread-class.md) obiektu.|  
|[Afxinitrichedit —](#afxinitrichedit)|Inicjuje w wersji 1.0 zaawansowanej edycji dla aplikacji.|  
|[Afxinitrichedit2 —](#afxinitrichedit2)|Inicjuje kontroli aplikacji edycji wzbogaconej 2.0 lub nowszej wersji.| 
|[Afxisextendedframeclass —](#afxisextendedframeclass)|Określa, czy okno danego obiektu rozszerzonej ramki.|
|[Afxismfctoolbar —](#afxismfctoolbar)|Określa, czy dany okna jest obiektem paska narzędzi.|
|[Afxkeyboardmanager —](#afxkeyboardmanager)|Wskaźnik do globalnej [Menedżera klawiatury](ckeyboardmanager-class.md).|
|[AfxLoadLibrary](#afxloadlibrary)|Mapuje modułu DLL i zwraca uchwyt może zostać użyty do uzyskania adresu funkcji DLL.|  
|[Afxmenutearoffmanager —](#afxmenutearoffmanager)|Wskaźnik do globalnej [odrywania menu Menedżera](cmenutearoffmanager-class.md).|
|[Afxmousemanager —](#afxmousemanager)|Wskaźnik do globalnej [Menedżera myszy](cmousemanager-class.md).|
|[Afxregisterclass —](#afxregisterclass)|Rejestruje klasę okna w bibliotece DLL, która używa MFC.|  
|[AfxRegisterWndClass](#afxregisterwndclass)|Rejestruje klasę okna Windows uzupełnienie tych automatycznie zarejestrowane przez MFC.|  
|[Afxsetperuserregistration —](#afxsetperuserregistration)|Określa, czy aplikacja przekierowuje dostęp do rejestru **HKEY_CURRENT_USER** ( **HKCU**) węzła.|  
|[Afxsetresourcehandle —](#afxsetresourcehandle)|Ustawia `HINSTANCE` dojście załadunku domyślnych zasobów aplikacji.|  
|[Afxshellmanager —](#afxshellmanager)|Wskaźnik do globalnej [shell manager](cshellmanager-class.md). |
|[Afxsocketinit —](#afxsocketinit)|Wywołuje się `CWinApp::InitInstance` należy przesłonić, aby zainicjować usługi Windows Sockets.|  
|[Afxusertoolsmanager —](#afxusertoolsmanager)|Wskaźnik do globalnej [użytkownika narzędzia menedżera](cusertoolsmanager-class.md).|
|[Afxwininit —](#afxwininit)|Wywoływane przez podany MFC `WinMain` funkcji jako część [CWinApp](../../mfc/reference/cwinapp-class.md) inicjowania aplikacji Graficznym interfejsem użytkownika, można zainicjować biblioteki MFC. Musi zostać wywołany bezpośrednio do aplikacji konsoli, które używają MFC.|  
  

  
##  <a name="afxbeginthread"></a>  Afxbeginthread —  
 Wywołanie tej funkcji można utworzyć nowego wątku.  
  
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
 `pfnThreadProc`  
 Punkty do kontrolowania funkcji wątku roboczego. Nie może być **NULL**. Ta funkcja musi być zadeklarowana w następujący sposób:  
  
 `UINT __cdecl MyControllingFunction( LPVOID pParam );`  
  
 *pThreadClass*  
 Runtime_class — obiektu pochodną [cwinthread —](../../mfc/reference/cwinthread-class.md).  
  
 *pParam*  
 Parametr przekazywany do kontrolowania funkcji, jak pokazano w deklaracji funkcji w parametrze `pfnThreadProc`.  
  
 `nPriority`  
 Żądany priorytet wątku. Pełną listę i opis dostępnych priorytetów, zobacz [wykonanie funkcji SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) w zestawie Windows SDK.  
  
 `nStackSize`  
 Określa rozmiar w bajtach stosu dla nowego wątku. Jeśli jest to 0, rozmiar stosu domyślnie sam stos rozmiar jako Tworzenie wątku.  
  
 `dwCreateFlags`  
 Określa dodatkowe flagi, który kontroluje Tworzenie wątku. Ta flaga może zawierać jedną z dwóch wartości:  
  
- **CREATE_SUSPENDED** uruchomić wraz z liczbą Wstrzymaj jednego wątku. Użyj **CREATE_SUSPENDED** Jeśli chcesz zainicjować żadnych danych elementu członkowskiego `CWinThread` obiektów, takich jak [m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete) lub członków klasy pochodnej, zanim uruchomienie wątku. Po zakończeniu inicjowania użytkownika, użyj [CWinThread::ResumeThread](../../mfc/reference/cwinthread-class.md#resumethread) można uruchomić wątku uruchomiona. Wątek nie zostanie wykonany, dopóki `CWinThread::ResumeThread` jest wywoływana.  
  
- **0** uruchomić wątku natychmiast po utworzeniu.  
  
 `lpSecurityAttrs`  
 Wskazuje [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) strukturę, która określa atrybuty zabezpieczeń dla wątku. Jeśli **NULL**, takimi samymi zabezpieczeniami atrybuty jak tworzenie wątku, który będzie używany. Aby uzyskać więcej informacji na tej struktury zobacz zestaw Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do obiektu nowo utworzony wątku lub **NULL** Jeśli wystąpi błąd.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy formę `AfxBeginThread` tworzy wątku roboczego. Drugi formularz tworzy wątku, który może służyć jako wątku interfejsu użytkownika lub wątku roboczego.  
  
 `AfxBeginThread` Tworzy nowy `CWinThread` obiektu, wywołania jego [CreateThread](../../mfc/reference/cwinthread-class.md#createthread) funkcji można uruchomić na wykonywaniu wątku i zwraca wskaźnik do wątku. Testy zostały wprowadzone w całej procedury upewnij się, że wszystkie obiekty są deallocated prawidłowo w przypadku dowolnej części Tworzenie nie. Aby zakończyć wątek, należy wywołać [AfxEndThread](#afxendthread) z wątku lub powrót z kontrolowanie funkcji wątku roboczego.  
  
 Wielowątkowość muszą być włączone przez aplikacji; w przeciwnym razie ta funkcja nie powiedzie się. Aby uzyskać więcej informacji na temat włączania wielowątkowość dotyczą [/ / MD, / MT, /LD (Użyj biblioteki wykonawczej)](../../build/reference/md-mt-ld-use-run-time-library.md) w obszarze *opcje kompilatora języka Visual C++*.  
  
 Aby uzyskać więcej informacji na temat `AfxBeginThread`, zobacz artykuły [Multithreading: Tworzenie wątków roboczych](../../parallel/multithreading-creating-worker-threads.md) i [Multithreading: Tworzenie wątków interfejsu użytkownika](../../parallel/multithreading-creating-user-interface-threads.md).  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CSocket::Attach](../../mfc/reference/csocket-class.md#attach).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxwin.h  

## <a name="afxcontextmenumanager"></a> Afxcontextmenumanager —
Wskaźnik do globalnej [Menedżera menu kontekstowe](ccontextmenumanager-class.md).  
   
### <a name="syntax"></a>Składnia    
```  
CContextMenuManager* afxContextMenuManager;  
```     
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcontextmenumanager.h     

### <a name="see-also"></a>Zobacz też   
 [Klasa CContextMenuManager](ccontextmenumanager-class.md)

  
##  <a name="afxendthread"></a>  AfxEndThread  
 Wywołanie tej funkcji zakończenie wątku aktualnie wykonywane.  
  
```   
void AFXAPI AfxEndThread(
    UINT nExitCode,  
    BOOL bDelete  = TRUE); 
```  
  
### <a name="parameters"></a>Parametry  
 *nExitCode*  
 Określa kod zakończenia wątku.  
  
 *bUsuń*  
 Usuwa obiekt wątku z pamięci.  
  
### <a name="remarks"></a>Uwagi  
 Musi zostać wywołany z w wątku, który ma zostać zakończony.  
  
 Aby uzyskać więcej informacji na temat `AfxEndThread`, zapoznaj się z artykułem [Multithreading: przerywanie wątków](../../parallel/multithreading-terminating-threads.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxwin.h  

  ## <a name="afxfindresourcehandle"></a>AfxFindResourceHandle
Użyj `AfxFindResourceHandle` zaprezentuje łańcucha zasobów i Znajdź określonych zasobów przez identyfikator i zasobów typu zasobu.  
   
### <a name="syntax"></a>Składnia    
```
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );  
```
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Wskaźnik do ciąg zawierający identyfikator zasobu.    
 *lpszType*  
 Wskaźnik do typu zasobu. Aby uzyskać listę typów zasobów, zobacz [FindResource](http://msdn.microsoft.com/library/windows/desktop/ms648042) w zestawie Windows SDK.  
   
### <a name="return-value"></a>Wartość zwracana  
 Dojście do modułu, który zawiera zasób.  
   
### <a name="remarks"></a>Uwagi  
 `AfxFindResourceHandle` znajduje określony zasób i zwraca uchwyt do modułu, który zawiera zasób. Zasób może być dowolnego rozszerzenia MFC DLL zostały załadowane. `AfxFindResourceHandle` informuje, które z nich ma zasobu.  
  
 Moduły są przeszukiwane w następującej kolejności:  
  
1.  Moduł główny (jeśli jest bibliotekę DLL rozszerzenia MFC).  
  
2.  Moduły nie systemu.  
  
3.  Moduły specyficzny dla języka.  
  
4.  Moduł główny (jeśli jest systemowej biblioteki DLL).  
  
5.  Moduły systemowych.  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
   
### <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](mfc-macros-and-globals.md)   
  
##  <a name="afxfreelibrary"></a>  AfxFreeLibrary  
 Zarówno `AfxFreeLibrary` i `AfxLoadLibrary` Obsługa licznika odwołań dla każdego modułu załadować biblioteki.  
  
```   
BOOL AFXAPI AfxFreeLibrary(HINSTANCE hInstLib); 
```  
  
### <a name="parameters"></a>Parametry  
 *hInstLib*  
 Uchwyt moduł załadować biblioteki. [AfxLoadLibrary](#afxloadlibrary) zwraca ta dojścia.  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** Jeśli funkcja zakończy się pomyślnie; w przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 `AfxFreeLibrary` zmniejsza odwołanie liczba modułu załadować biblioteki dołączanej (dynamicznie DLL). Jeśli liczba odwołań do zera, moduł jest usunięte przestrzeni adresowej procesu wywołującego i dojście nie jest już prawidłowy. Ten licznik odwołania jest zwiększany po każdej `AfxLoadLibrary` jest wywoływana.  
  
 Przed usuwania mapowania modułu biblioteki, system umożliwia DLL można odłączyć od procesów przy jej użyciu. Dzięki temu daje możliwość wyczyścić zasoby przydzielone imieniu bieżącego procesu biblioteki DLL. Gdy funkcja punktu wejścia modułu biblioteki zostaną usunięte z przestrzeni adresowej bieżącego procesu.  
  
 Użyj `AfxLoadLibrary` do mapowania modułu biblioteki DLL.  
  
 Należy użyć `AfxFreeLibrary` i `AfxLoadLibrary` (zamiast funkcji Win32 **FreeLibrary** i **LoadLibrary**) Jeśli aplikacja używa wielu wątków. Przy użyciu `AfxLoadLibrary` i `AfxFreeLibrary` upewnia się, że uruchamiania i wyłączania kod, który wykonuje się, gdy rozszerzenie MFC DLL jest załadowany i zwolniony nieuszkodzone stan globalny MFC.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [AfxLoadLibrary](#afxloadlibrary).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdll_.h  
  
##  <a name="afxgetapp"></a>  Afxgetapp —  
 Wskaźnik zwracane przez tę funkcję można uzyskiwać dostęp do informacji aplikacji, takie jak kod głównego wysyłania wiadomości lub oknie.  
  
```   
CWinApp* AFXAPI AfxGetApp(); 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do jednego `CWinApp` obiektu aplikacji.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ta metoda zwraca wartość NULL, może to oznaczać, że okno główne aplikacji nie pełni zainicjowano jeszcze. Może też wskazywać problem.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#126](../../mfc/reference/codesnippet/cpp/application-information-and-management_1.cpp)]  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxwin.h  
  
##  <a name="afxgetappname"></a>  Afxgetappname —  
 Długość ciągu zwróconego przez tę funkcję można komunikaty diagnostyczne lub jako katalog główny dla nazwy ciągu tymczasowego.  
  
```   
LPCTSTR AFXAPI AfxGetAppName(); 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zerem ciągu zawierającego nazwę aplikacji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#127](../../mfc/reference/codesnippet/cpp/application-information-and-management_2.cpp)]  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxwin.h  
  
##  <a name="afxgetinstancehandle"></a>  Afxgetinstancehandle —  
 Ta funkcja umożliwia pobieranie dojście wystąpienia bieżącej aplikacji.  
  
```   
HINSTANCE  AFXAPI AfxGetInstanceHandle(); 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `HINSTANCE` Do bieżącego wystąpienia aplikacji. Jeśli wywołany z poziomu biblioteki DLL połączone z wersją USRDLL MFC, `HINSTANCE` plik dll, który jest zwracany.  
  
### <a name="remarks"></a>Uwagi  
 `AfxGetInstanceHandle` zawsze zwraca `HINSTANCE` pliku wykonywalnego (. Wywołanie pliku EXE), chyba że jest ona wywoływana z poziomu biblioteki DLL połączone z wersją USRDLL MFC. W takim przypadku zwraca `HINSTANCE` do pliku DLL.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxwin.h  
  
##  <a name="afxgetmainwnd"></a>  Afxgetmainwnd —  
 Jeśli aplikacja serwera OLE, wywołanie tej funkcji można pobrać wskaźnik do aktywne główne okno aplikacji zamiast bezpośrednio odwołujących się do [m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd) element członkowski obiektu aplikacji.  
  
```   
CWnd* AFXAPI AfxGetMainWnd(); 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli serwer ma obiekt, który jest w miejscu aktywny wewnątrz kontenera i ten kontener jest aktywna, funkcja zwraca wskaźnik do obiektu okna ramki, który zawiera aktywny dokument w miejscu.  
  
 Jeśli nie ma żadnego obiektu, który jest aktywny w miejscu w kontenerze lub aplikacja nie jest serwerem OLE, ta funkcja po prostu zwraca `m_pMainWnd` obiektu aplikacji.  
  
 Jeśli `AfxGetMainWnd` jest wywoływana z wątku głównej aplikacji, zwraca głównego okna aplikacji zgodnie z regułami powyżej. Jeśli funkcja jest wywoływana z wątku dodatkowej w aplikacji, funkcja zwraca okno główne skojarzone z wątku, który zgłosił wywołania.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli aplikacja nie jest serwerem OLE, a następnie podczas wywoływania tej funkcji jest odpowiednikiem bezpośrednio odwołujących się do `m_pMainWnd` element członkowski obiektu aplikacji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#129](../../mfc/reference/codesnippet/cpp/application-information-and-management_4.cpp)]  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxwin.h  
  
##  <a name="afxgetperuserregistration"></a>  Afxgetperuserregistration —  
 Ta funkcja służy do określenia, czy aplikacja przekierowuje dostęp do rejestru **HKEY_CURRENT_USER** ( **HKCU**) węzła.  
  
```  
BOOL AFXAPI AfxGetPerUserRegistration();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Wskazuje, że informacje rejestru jest kierowany do **HKCU** węzła; `FALSE` wskazuje, że aplikacja zapisuje informacje rejestru do domyślnego węzła. Domyślny węzeł jest **wpisów z HKEY_CLASSES_ROOT** ( **HKCR**).  
  
### <a name="remarks"></a>Uwagi  
 Po włączeniu przekierowania rejestru platformę przekierowuje dostęp z **HKCR** do **HKEY_CURRENT_USER\Software\Classes**. Dotyczy tylko struktury MFC i ATL przekierowania.  
  
 Aby określić, czy aplikacja przekierowuje dostępu do rejestru, użyj [afxsetperuserregistration —](#afxsetperuserregistration).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxstat_.h    
  
##  <a name="afxgetresourcehandle"></a>  Afxgetresourcehandle —  
 Użyj `HINSTANCE` zwracane przez tę funkcję bezpośredni dostęp do zasobów aplikacji, na przykład w wywołaniach funkcji systemu Windows dojście **FindResource**.  
  
```   
extern HINSTANCE  AfxGetResourceHandle(); 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `HINSTANCE` Dojście załadunku domyślnych zasobów aplikacji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxwin.h  
  
##  <a name="afxgetthread"></a>  Afxgetthread —  
 Wywołanie tej funkcji, aby uzyskać wskaźnik do [cwinthread —](../../mfc/reference/cwinthread-class.md) obiekt reprezentujący aktualnie wykonywane wątku.  
  
```   
CWinThread* AfxGetThread(); 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do wątku aktualnie wykonywane; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Musi zostać wywołany z w żądanej wątku.  
  
> [!NOTE]
>  Jeśli są eksportowanie wywołania projektu MFC `AfxGetThread` z języka Visual C++ w wersji 4.2, 5.0 lub 6.0, `AfxGetThread` wywołania [afxgetapp —](#afxgetapp) przypadku nieznalezienia żadnego wątku. W nowszych wersjach kompilatora `AfxGetThread` zwraca **NULL** Jeśli wątek nie został znaleziony. Jeśli chcesz wątku aplikacji, należy wywołać `AfxGetApp`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxwin.h  
  
##  <a name="afxinitrichedit"></a>  Afxinitrichedit —  
 Wywołanie tej funkcji, aby zainicjować kontrolki zaawansowanej edycji (w wersji 1.0) dla aplikacji.  
  
```   
BOOL AFXAPI AfxInitRichEdit(); 
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest dostępne w celu zgodności z poprzednimi wersjami. Nowe aplikacje powinny używać [afxinitrichedit2 —](#afxinitrichedit2).  
  
 `AfxInitRichEdit` ładuje RICHED32. Biblioteki DLL w celu zainicjowania wersji 1.0 kontrolki zaawansowanej edycji. Aby użyć wersji 2.0 i 3.0 kontrolki zaawansowanej edycji RICHED20. Biblioteki DLL muszą zostać załadowane. Jest to realizowane za pomocą wywołania [afxinitrichedit2 —](#afxinitrichedit2).  
  
 Aby zaktualizować kontrolki zaawansowanej edycji w istniejących aplikacji Visual C++ w wersji 2.0, należy otworzyć. RC plik jako tekst, zmienić nazwę klasy każdej kontrolki zaawansowanej edycji z "RICHEDIT" do "RichEdit20a". Następnie zastąp wywołanie `AfxInitRichEdit` z `AfxInitRichEdit2`.  
  
 Ta funkcja także inicjuje Biblioteka formantów standardowych, jeśli biblioteka nie zostało zainicjowane już dla procesu. Jeśli używasz kontrolki zaawansowanej edycji bezpośrednio z aplikacji MFC, należy wywołać tę funkcję, aby upewnić się, że czy MFC została prawidłowo zainicjalizowana środowiska uruchomieniowego kontrolki zaawansowanej edycji. Jeśli należy wywołać metody Create [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [cricheditview —](../../mfc/reference/cricheditview-class.md), lub [cricheditdoc —](../../mfc/reference/cricheditdoc-class.md), zwykle nie trzeba wywoływać tej funkcji, ale w niektórych przypadkach może być niezbędne.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxwin.h  
  
##  <a name="afxinitrichedit2"></a>  Afxinitrichedit2 —  
 Wywołanie tej funkcji, aby zainicjować kontrolki zaawansowanej edycji (w wersji 2.0 lub nowszy) dla aplikacji.  
  
```   
BOOL AFXAPI AfxInitRichEdit2(); 
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby załadować RICHED20. Biblioteki DLL i zainicjować wersji 2.0 zaawansowanej edycji. Jeśli należy wywołać metody Create [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [cricheditview —](../../mfc/reference/cricheditview-class.md), lub [cricheditdoc —](../../mfc/reference/cricheditdoc-class.md), zwykle nie trzeba wywoływać tej funkcji, ale w niektórych przypadkach może być niezbędne.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxwin.h  

  ## <a name="afxisextendedframeclass"></a>  Afxisextendedframeclass —
Określa, czy okno danego obiektu rozszerzonej ramki.  
   
### <a name="syntax"></a>Składnia    
```  
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );  
```
### <a name="parameters"></a>Parametry  
 [in] `pWnd`  
 Wskaźnik do obiektu, który jest pochodną `CWnd`.  
   
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli podany okna jest obiektem ramki rozszerzonych; w przeciwnym razie `FALSE`.  
   
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca `TRUE` Jeśli `pWnd` pochodzi z jednego z następujących klas:  
  
-   `CFrameWndEx`  
  
-   `CMDIFrameWndEx`  
  
-   `COleIPFrameWndEx`  
  
-   `COleDocIPFrameWndEx`  
  
-   `CMDIChildWndEx`  
  
 Ta metoda jest przydatna, gdy trzeba sprawdzić, czy parametr metody lub funkcji jest rozszerzona ramkę okna.  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxpriv.h  
   
### <a name="see-also"></a>Zobacz też  
 [Klasa CWnd](cwnd-class.md)   
 [Klasa CFrameWndEx](cframewndex-class.md)   

## <a name="afxismfctoolbar"></a> Afxismfctoolbar —
Określa, czy dany okna jest obiektem paska narzędzi.  
   
### <a name="syntax"></a>Składnia    
```  
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);  
```
### <a name="parameters"></a>Parametry  
 [in] `pWnd`  
 Wskaźnik do obiektu, który jest pochodną `CWnd`.  
   
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli okno podana jest obiektem paska narzędzi w przeciwnym razie `FALSE`.  
   
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca `TRUE` Jeśli `pWnd` pochodną `CMFCToolBar`. Ta metoda jest przydatna, gdy trzeba sprawdzić, czy parametr metody lub funkcji jest `CMFCToolBar` obiektu.  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxpriv.h  
   
### <a name="see-also"></a>Zobacz też  
 [Klasa CWnd](cwnd-class.md)   
 [Klasa CMFCToolBar](cmfctoolbar-class.md)

 
## <a name="afxkeyboardmanager"></a> Afxkeyboardmanager —
Wskaźnik do globalnej [Menedżera klawiatury](ckeyboardmanager-class.md).  
   
### <a name="syntax"></a>Składnia    
```  
CKeyboardManager* afxKeyboardManager;  
```  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxkeyboardmanager.h  
   
### <a name="see-also"></a>Zobacz też  

 [Makra, funkcje globalne i zmienne globalne](mfc-macros-and-globals.md)   
 [Klasa CKeyboardManager](ckeyboardmanager-class.md)


##  <a name="afxloadlibrary"></a>  AfxLoadLibrary  
 Użyj `AfxLoadLibrary` do mapowania modułu biblioteki DLL.  
  
```   
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName); 
```  
  
### <a name="parameters"></a>Parametry  
 *lpszModuleName*  
 Wskazuje zerem ciąg, który zawiera nazwę modułu (albo. Biblioteki DLL lub. Plik EXE). Podana nazwa jest nazwą pliku modułu.  
  
 Jeśli ciąg Określa ścieżkę, ale plik nie istnieje w określonym katalogu, funkcja kończy się niepowodzeniem.  
  
 Jeśli ścieżka nie zostanie określona, a rozszerzenie nazwy pliku jest pominięta, rozszerzenie domyślne. Biblioteka DLL jest dołączany. Jednak ciąg nazwy pliku może zawierać końcowego znaku punktu (.) wskazująca, że nazwa modułu nie ma rozszerzenia. Ścieżka nie zostanie określona, funkcja szuka pliku w następującej kolejności:  
  
-   Katalog, z którego ładowany aplikacji.  
  
-   Bieżący katalog.  
  
- **Windows 95/98:** katalog systemu Windows. **Windows NT:** katalog 32-bitowego systemu Windows. Nazwa tego katalogu jest SYSTEM32.  
  
- **Tylko system Windows NT:** katalogu systemu 16-bitowego systemu Windows. Nie jest Brak funkcji Win32, które uzyskuje ścieżki tego katalogu, ale przeszukiwany jest. Nazwa tego katalogu jest systemu.  
  
-   Katalog systemu Windows.  
  
-   Katalogi, które są wymienione w zmiennej środowiskowej PATH.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja zakończy się powodzeniem, wartość zwracana jest dojścia do modułu. Jeśli funkcja nie powiedzie się, wartość zwracana jest wartość NULL.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca dojście, które mogą być używane w [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212) można pobrać adresu funkcji DLL. `AfxLoadLibrary` można również mapować inne moduły pliku wykonywalnego.  
  
 Każdy proces zachowuje licznika odwołań dla każdego modułu załadować biblioteki. Ten licznik odwołania jest zwiększany po każdej `AfxLoadLibrary` nosi nazwę i jest zmniejszana za każdym razem `AfxFreeLibrary` jest wywoływana. Jeśli liczba odwołań do zera, moduł jest usunięte przestrzeni adresowej procesu wywołującego i dojście nie jest już prawidłowy.  
  
 Należy użyć `AfxLoadLibrary` i `AfxFreeLibrary` (zamiast funkcji Win32 **LoadLibrary** i **FreeLibrary**) Jeśli aplikacja używa wielu wątków i dynamicznie ładuje MFC Biblioteka DLL rozszerzenia. Przy użyciu `AfxLoadLibrary` i `AfxFreeLibrary` temu, że uruchamiania i wyłączania kod, który wykonuje się, gdy ładowany i zwalnianie biblioteki DLL rozszerzenia MFC nie doprowadzić do uszkodzenia globalne MFC.  
  
 Przy użyciu `AfxLoadLibrary` w aplikacji wymaga dynamiczne łącze do wersji biblioteki DLL MFC; plik nagłówka `AfxLoadLibrary`, Afxdll_.h, jest tylko włączone, jeśli MFC jest połączony z aplikacji jako biblioteki DLL. To jest celowe, ponieważ należy połączyć się z wersją biblioteki DLL MFC lub utworzeniu biblioteki DLL rozszerzeń MFC.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_DLLUser#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]  
[!code-cpp[NVC_MFC_DLLUser#2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]  
[!code-cpp[NVC_MFC_DLLUser#3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdll_.h  
   
## <a name="afxmenutearoffmanager"></a> Afxmenutearoffmanager —
Wskaźnik do globalnej [odrywania menu Menedżera](cmenutearoffmanager-class.md).  
   
### <a name="syntax"></a>Składnia    
```  
CMenuTearOffManager* g_pTearOffMenuManager;  
```  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxmenutearoffmanager.h  
   
### <a name="see-also"></a>Zobacz też     
 [Klasa CMenuTearOffManager](cmenutearoffmanager-class.md)
 
## <a name="afxmousemanager"></a>  Afxmousemanager —
Wskaźnik do globalnej [Menedżera myszy](cmousemanager-class.md).  
   
### <a name="syntax"></a>Składnia  
  ```  
CMouseManager* afxMouseManager;  
```  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxmousemanager.h  
   
### <a name="see-also"></a>Zobacz też  
 [Klasa CMouseManager](cmousemanager-class.md)
 

  
##  <a name="afxregisterclass"></a>  Afxregisterclass —  
 Ta funkcja umożliwia rejestrowanie klas okien w bibliotece DLL, która używa MFC.  
  
```   
BOOL AFXAPI AfxRegisterClass(WNDCLASS* lpWndClass); 
```  
  
### <a name="parameters"></a>Parametry  
 *lpWndClass*  
 Wskaźnik do [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) struktury zawierającej informacje o klasie okno ma zostać zarejestrowany. Aby uzyskać więcej informacji na tej struktury zobacz zestaw Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** Jeśli klasa jest pomyślnie zarejestrowane; w przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja ta klasa jest automatycznie wyrejestrować po zwolnić biblioteki DLL.  
  
 W kompilacjach-DLL `AfxRegisterClass` identyfikator jest zdefiniowany jako makra, który jest mapowany na funkcję Windows **RegisterClass**, ponieważ są automatycznie wyrejestrować klasy zarejestrowany w aplikacji. Jeśli używasz `AfxRegisterClass` zamiast **RegisterClass**, kod może być używany bez zmiany zarówno w aplikacji, jak i w bibliotece DLL.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_DLL#3](../../atl-mfc-shared/codesnippet/cpp/application-information-and-management_10.cpp)]  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxwin.h  
  
##  <a name="afxregisterwndclass"></a>  AfxRegisterWndClass  
 Pozwala na rejestrowanie własnych klas okna.  
  
```  
LPCTSTR AFXAPI AfxRegisterWndClass(
    UINT nClassStyle,  
    HCURSOR hCursor = 0,  
    HBRUSH hbrBackground = 0,  
    HICON hIcon = 0);  
```  
  
### <a name="parameters"></a>Parametry  
 *nClassStyle*  
 Określa styl klasy systemu Windows lub kombinacja style, utworzony przy użyciu wartości bitowe lub ( **&#124;**) — operator dla klasy okna. Lista style klasa, zobacz [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) struktury w zestawie Windows SDK. Jeśli **NULL**, wartości domyślne zostaną ustawione w następujący sposób:  
  
-   Ustawia styl myszy **CS_DBLCLKS**, które wysyła kliknij dwukrotnie wiadomości do procedury okna, gdy użytkownik kliknie dwukrotnie myszy.  
  
-   Ustawia styl strzałki kursor na system Windows standard **IDC_ARROW**.  
  
-   Ustawia pędzel tła **NULL**, więc okna nie spowoduje usunięcie jego tła.  
  
-   Ustawia ikonę na standardowy, Flaga wymachują ikonę logo systemu Windows.  
  
 `hCursor`  
 Określa dojścia do zasobu kursora do zainstalowania w każdym oknie utworzone na podstawie klasy okna. Jeśli używasz domyślnego **0**, zostanie wyświetlony standardowy **IDC_ARROW** kursora.  
  
 *hbrBackground*  
 Określa dojścia do zasobu pędzla do zainstalowania w każdym oknie utworzone na podstawie klasy okna. Jeśli używasz domyślnego **0**, konieczne będzie **NULL** pędzel tła i sieci będą okna, domyślnie usunie jego tła podczas przetwarzania [WM_ERASEBKGND](http://msdn.microsoft.com/library/windows/desktop/ms648055).  
  
 `hIcon`  
 Określa dojścia do zasobu ikony do zainstalowania w każdym oknie utworzone na podstawie klasy okna. Jeśli używasz domyślnego **0**, zostanie wyświetlony standardowy, Flaga wymachują ikony logo systemu Windows.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zerem ciągu zawierającego nazwę klasy. Można przekazać tę nazwę klasy, aby **Utwórz** funkcji członkowskiej we `CWnd` lub innych **CWnd -** pochodzi z klasy można utworzyć okna. Nazwa jest generowany przez Microsoft Foundation Class Library.  
  
> [!NOTE]
>  Wartość zwracana jest wskaźnik do statycznego buforu. Aby zapisać ten ciąg, przypisz go do `CString` zmiennej.  
  
### <a name="remarks"></a>Uwagi  
 Microsoft Foundation Class Library automatycznie rejestruje kilka klas standardowego okna. Wywołanie tej funkcji, jeśli chcesz zarejestrować swoje własne klasy okna.  
  
 Nazwa zarejestrowanej klasy przez `AfxRegisterWndClass` wyłącznie zależy od parametrów. Jeśli należy wywołać `AfxRegisterWndClass` wiele razy z identycznymi parametrami są rejestrowane tylko klasy przy pierwszym wywołaniu. Kolejne wywołania `AfxRegisterWndClass` z identycznymi parametrami powrócić po prostu classname już zarejestrowany.  
  
 Jeśli należy wywołać `AfxRegisterWndClass` dla wielu klas pochodnych CWnd z identycznymi parametrami, zamiast pobierania klasie osobnym oknie dla każdej klasy, każda klasa udostępnia tej samej klasy okna. Może to powodować problemy, jeśli **CS_CLASSDC** stylu klasy jest używany. Zamiast wielu **CS_CLASSDC** klasy okien na końcu jedną **CS_CLASSDC** klasy okna oraz wszystkich windows w języku C++ używających, że klasa nie współużytkują tego samego kontrolera domeny. Aby uniknąć tego problemu, należy wywołać [afxregisterclass —](#afxregisterclass) można zarejestrować klasy.  
  
 Dotyczą Uwaga techniczna [TN001: Rejestracja klas okien](../../mfc/tn001-window-class-registration.md) Aby uzyskać więcej informacji na temat rejestrowanie klasy okna i `AfxRegisterWndClass` funkcji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxwin.h  
  
##  <a name="afxsetperuserregistration"></a>  Afxsetperuserregistration —  
 Określa, czy aplikacja przekierowuje dostęp do rejestru **HKEY_CURRENT_USER** ( **HKCU**) węzła.  
  
```  
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `bEnable`  
 `TRUE` Wskazuje, że informacje rejestru jest kierowany do **HKCU** węzła; `FALSE` wskazuje, że aplikacja zapisuje informacje rejestru do domyślnego węzła. Domyślny węzeł jest **wpisów z HKEY_CLASSES_ROOT** ( **HKCR**).  
  
### <a name="remarks"></a>Uwagi  

Przed Windows Vista, aplikacje, które uzyskiwały dostęp do rejestru zwykle używany **wpisów z HKEY_CLASSES_ROOT** węzła. Jednak w z systemu Windows Vista lub nowszych systemów operacyjnych w trybie podniesionych uprawnień do zapisu należy uruchomić aplikację **HKCR**.  
  
 Ta metoda umożliwia obsługę aplikacji na odczytywanie i zapisywanie do rejestru bez uruchamiania w trybie podniesionych uprawnień przez przekierowywanie dostępu do rejestru z **HKCR** do **HKCU**. Aby uzyskać więcej informacji, zobacz [strony właściwości konsolidatora](../../ide/linker-property-pages.md).  
  
 Po włączeniu przekierowania rejestru platformę przekierowuje dostęp z **HKCR** do **HKEY_CURRENT_USER\Software\Classes**. Dotyczy tylko struktury MFC i ATL przekierowania.  
  
 Domyślna implementacja uzyskuje dostęp do rejestru, w obszarze **HKCR**.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxstat_.h    
  
##  <a name="afxsetresourcehandle"></a>  Afxsetresourcehandle —  
 Użyj tej funkcji, aby ustawić `HINSTANCE` uchwytu, który określa, gdzie są ładowane domyślnych zasobów aplikacji.  
  
```  
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);  
```  
  
### <a name="parameters"></a>Parametry  
 `hInstResource`  
 Dojście wystąpienia lub modułu do. Plik EXE lub DLL z której są ładowane zasoby aplikacji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#135](../../mfc/reference/codesnippet/cpp/application-information-and-management_12.cpp)]  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxwin.h  

## <a name="afxshellmanager"></a>  Afxshellmanager —
Wskaźnik do globalnej [shell manager](cshellmanager-class.md).  
   
### <a name="syntax"></a>Składnia    
```  
CShellManager* afxShellManager;  
```  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxshellmanager.h  
   
### <a name="see-also"></a>Zobacz też  
 [Klasa CShellManager](cshellmanager-class.md)
  
##  <a name="afxsocketinit"></a>  Afxsocketinit —  
 Wywołanie tej funkcji Twojej `CWinApp::InitInstance` należy przesłonić, aby zainicjować usługi Windows Sockets.  
  
```  
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);  
```  
  
### <a name="parameters"></a>Parametry  
 `lpwsaData`  
 Wskaźnik do [WSADATA](../../mfc/reference/wsadata-structure.md) struktury. Jeśli `lpwsaData` nie jest równa `NULL`, następnie adres `WSADATA` struktury jest wypełniony przez wywołanie `WSAStartup`. Ta funkcja także upewnia się, że `WSACleanup` jest wywoływana dla Ciebie, zanim zakończy aplikacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Korzystając z gniazda MFC w dodatkowej wątków w aplikacji statycznie połączone MFC, należy wywołać `AfxSocketInit` w każdym wątku, który używa sockets zainicjować biblioteki gniazd. Domyślnie `AfxSocketInit` jest wywoływany tylko w podstawowym wątku.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxsock.h  

## <a name="afxusertoolsmanager"></a>  Afxusertoolsmanager —
Wskaźnik do globalnej [użytkownika narzędzia menedżera](cusertoolsmanager-class.md).  
   
### <a name="syntax"></a>Składnia    
```  
CUserToolsManager* afxUserToolsManager;  
```  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxusertoolsmanager.h  
   
### <a name="see-also"></a>Zobacz też  
 [Klasa CUserToolsManager](cusertoolsmanager-class.md)
 
  
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
 `hInstance`  
 Dojście moduł aktualnie uruchomione.  
  
 *hPrevInstance*  
 Dojście do poprzedniego wystąpienia aplikacji. W przypadku aplikacji z Win32 ten parametr jest zawsze **NULL**.  
  
 `lpCmdLine`  
 Wskazuje zerem ciąg określający wiersz polecenia dla aplikacji.  
  
 `nCmdShow`  
 Określa, jak zostaną pokazane w głównym oknie aplikacji graficznego interfejsu użytkownika.  
  
### <a name="remarks"></a>Uwagi  
 Dla aplikacji konsoli, która nie używa dostarczony MFC `WinMain` funkcji, należy wywołać `AfxWinInit` bezpośrednio do zainicjowania MFC.  
  
 Jeśli należy wywołać `AfxWinInit` samodzielnie, należy zadeklarować wystąpienia `CWinApp` klasy. Dla aplikacji konsoli, można wybrać nie pochodzi z klasy z `CWinApp` i zamiast tego użyć wystąpienia `CWinApp` bezpośrednio. Ta technika jest odpowiednie, jeśli chcesz pozostawić wszystkie funkcje aplikacji w implementacji **głównego**.  
  
> [!NOTE]
>  Podczas tworzenia kontekstu aktywacji dla zestawu, MFC używa zasobu manifestu podana przez moduł użytkownika. Kontekst aktywacji jest tworzony w `AfxWinInit`. Aby uzyskać więcej informacji, zobacz [Obsługa kontekstów aktywacji w stanie modułu MFC](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]  

### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxwin.h  
    
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)   
 [Klasa CWinApp](../../mfc/reference/cwinapp-class.md)
