---
title: Klasa CWinApp
ms.date: 07/15/2019
f1_keywords:
- CWinApp
- AFXWIN/CWinApp
- AFXWIN/CWinApp::CWinApp
- AFXWIN/CWinApp::AddDocTemplate
- AFXWIN/CWinApp::AddToRecentFileList
- AFXWIN/CWinApp::ApplicationRecoveryCallback
- AFXWIN/CWinApp::CloseAllDocuments
- AFXWIN/CWinApp::CreatePrinterDC
- AFXWIN/CWinApp::DelRegTree
- AFXWIN/CWinApp::DoMessageBox
- AFXWIN/CWinApp::DoWaitCursor
- AFXWIN/CWinApp::EnableD2DSupport
- AFXWIN/CWinApp::EnableHtmlHelp
- AFXWIN/CWinApp::EnableTaskbarInteraction
- AFXWIN/CWinApp::ExitInstance
- AFXWIN/CWinApp::GetApplicationRecoveryParameter
- AFXWIN/CWinApp::GetApplicationRecoveryPingInterval
- AFXWIN/CWinApp::GetApplicationRestartFlags
- AFXWIN/CWinApp::GetAppRegistryKey
- AFXWIN/CWinApp::GetDataRecoveryHandler
- AFXWIN/CWinApp::GetFirstDocTemplatePosition
- AFXWIN/CWinApp::GetHelpMode
- AFXWIN/CWinApp::GetNextDocTemplate
- AFXWIN/CWinApp::GetPrinterDeviceDefaults
- AFXWIN/CWinApp::GetProfileBinary
- AFXWIN/CWinApp::GetProfileInt
- AFXWIN/CWinApp::GetProfileString
- AFXWIN/CWinApp::GetSectionKey
- AFXWIN/CWinApp::HideApplication
- AFXWIN/CWinApp::HtmlHelp
- AFXWIN/CWinApp::InitInstance
- AFXWIN/CWinApp::IsTaskbarInteractionEnabled
- AFXWIN/CWinApp::LoadCursor
- AFXWIN/CWinApp::LoadIcon
- AFXWIN/CWinApp::LoadOEMCursor
- AFXWIN/CWinApp::LoadOEMIcon
- AFXWIN/CWinApp::LoadStandardCursor
- AFXWIN/CWinApp::LoadStandardIcon
- AFXWIN/CWinApp::OnDDECommand
- AFXWIN/CWinApp::OnIdle
- AFXWIN/CWinApp::OpenDocumentFile
- AFXWIN/CWinApp::ParseCommandLine
- AFXWIN/CWinApp::PreTranslateMessage
- AFXWIN/CWinApp::ProcessMessageFilter
- AFXWIN/CWinApp::ProcessShellCommand
- AFXWIN/CWinApp::ProcessWndProcException
- AFXWIN/CWinApp::Register
- AFXWIN/CWinApp::RegisterWithRestartManager
- AFXWIN/CWinApp::ReopenPreviousFilesAtRestart
- AFXWIN/CWinApp::RestartInstance
- AFXWIN/CWinApp::RestoreAutosavedFilesAtRestart
- AFXWIN/CWinApp::Run
- AFXWIN/CWinApp::RunAutomated
- AFXWIN/CWinApp::RunEmbedded
- AFXWIN/CWinApp::SaveAllModified
- AFXWIN/CWinApp::SelectPrinter
- AFXWIN/CWinApp::SetHelpMode
- AFXWIN/CWinApp::SupportsApplicationRecovery
- AFXWIN/CWinApp::SupportsAutosaveAtInterval
- AFXWIN/CWinApp::SupportsAutosaveAtRestart
- AFXWIN/CWinApp::SupportsRestartManager
- AFXWIN/CWinApp::Unregister
- AFXWIN/CWinApp::WinHelp
- AFXWIN/CWinApp::WriteProfileBinary
- AFXWIN/CWinApp::WriteProfileInt
- AFXWIN/CWinApp::WriteProfileString
- AFXWIN/CWinApp::EnableShellOpen
- AFXWIN/CWinApp::LoadStdProfileSettings
- AFXWIN/CWinApp::OnContextHelp
- AFXWIN/CWinApp::OnFileNew
- AFXWIN/CWinApp::OnFileOpen
- AFXWIN/CWinApp::OnFilePrintSetup
- AFXWIN/CWinApp::OnHelp
- AFXWIN/CWinApp::OnHelpFinder
- AFXWIN/CWinApp::OnHelpIndex
- AFXWIN/CWinApp::OnHelpUsing
- AFXWIN/CWinApp::RegisterShellFileTypes
- AFXWIN/CWinApp::SetAppID
- AFXWIN/CWinApp::SetRegistryKey
- AFXWIN/CWinApp::UnregisterShellFileTypes
- AFXWIN/CWinApp::m_bHelpMode
- AFXWIN/CWinApp::m_eHelpType
- AFXWIN/CWinApp::m_hInstance
- AFXWIN/CWinApp::m_lpCmdLine
- AFXWIN/CWinApp::m_nCmdShow
- AFXWIN/CWinApp::m_pActiveWnd
- AFXWIN/CWinApp::m_pszAppID
- AFXWIN/CWinApp::m_pszAppName
- AFXWIN/CWinApp::m_pszExeName
- AFXWIN/CWinApp::m_pszHelpFilePath
- AFXWIN/CWinApp::m_pszProfileName
- AFXWIN/CWinApp::m_pszRegistryKey
- AFXWIN/CWinApp::m_dwRestartManagerSupportFlags
- AFXWIN/CWinApp::m_nAutosaveInterval
- AFXWIN/CWinApp::m_pDataRecoveryHandler
helpviewer_keywords:
- CWinApp [MFC], CWinApp
- CWinApp [MFC], AddDocTemplate
- CWinApp [MFC], AddToRecentFileList
- CWinApp [MFC], ApplicationRecoveryCallback
- CWinApp [MFC], CloseAllDocuments
- CWinApp [MFC], CreatePrinterDC
- CWinApp [MFC], DelRegTree
- CWinApp [MFC], DoMessageBox
- CWinApp [MFC], DoWaitCursor
- CWinApp [MFC], EnableD2DSupport
- CWinApp [MFC], EnableHtmlHelp
- CWinApp [MFC], EnableTaskbarInteraction
- CWinApp [MFC], ExitInstance
- CWinApp [MFC], GetApplicationRecoveryParameter
- CWinApp [MFC], GetApplicationRecoveryPingInterval
- CWinApp [MFC], GetApplicationRestartFlags
- CWinApp [MFC], GetAppRegistryKey
- CWinApp [MFC], GetDataRecoveryHandler
- CWinApp [MFC], GetFirstDocTemplatePosition
- CWinApp [MFC], GetHelpMode
- CWinApp [MFC], GetNextDocTemplate
- CWinApp [MFC], GetPrinterDeviceDefaults
- CWinApp [MFC], GetProfileBinary
- CWinApp [MFC], GetProfileInt
- CWinApp [MFC], GetProfileString
- CWinApp [MFC], GetSectionKey
- CWinApp [MFC], HideApplication
- CWinApp [MFC], HtmlHelp
- CWinApp [MFC], InitInstance
- CWinApp [MFC], IsTaskbarInteractionEnabled
- CWinApp [MFC], LoadCursor
- CWinApp [MFC], LoadIcon
- CWinApp [MFC], LoadOEMCursor
- CWinApp [MFC], LoadOEMIcon
- CWinApp [MFC], LoadStandardCursor
- CWinApp [MFC], LoadStandardIcon
- CWinApp [MFC], OnDDECommand
- CWinApp [MFC], OnIdle
- CWinApp [MFC], OpenDocumentFile
- CWinApp [MFC], ParseCommandLine
- CWinApp [MFC], PreTranslateMessage
- CWinApp [MFC], ProcessMessageFilter
- CWinApp [MFC], ProcessShellCommand
- CWinApp [MFC], ProcessWndProcException
- CWinApp [MFC], Register
- CWinApp [MFC], RegisterWithRestartManager
- CWinApp [MFC], ReopenPreviousFilesAtRestart
- CWinApp [MFC], RestartInstance
- CWinApp [MFC], RestoreAutosavedFilesAtRestart
- CWinApp [MFC], Run
- CWinApp [MFC], RunAutomated
- CWinApp [MFC], RunEmbedded
- CWinApp [MFC], SaveAllModified
- CWinApp [MFC], SelectPrinter
- CWinApp [MFC], SetHelpMode
- CWinApp [MFC], SupportsApplicationRecovery
- CWinApp [MFC], SupportsAutosaveAtInterval
- CWinApp [MFC], SupportsAutosaveAtRestart
- CWinApp [MFC], SupportsRestartManager
- CWinApp [MFC], Unregister
- CWinApp [MFC], WinHelp
- CWinApp [MFC], WriteProfileBinary
- CWinApp [MFC], WriteProfileInt
- CWinApp [MFC], WriteProfileString
- CWinApp [MFC], EnableShellOpen
- CWinApp [MFC], LoadStdProfileSettings
- CWinApp [MFC], OnContextHelp
- CWinApp [MFC], OnFileNew
- CWinApp [MFC], OnFileOpen
- CWinApp [MFC], OnFilePrintSetup
- CWinApp [MFC], OnHelp
- CWinApp [MFC], OnHelpFinder
- CWinApp [MFC], OnHelpIndex
- CWinApp [MFC], OnHelpUsing
- CWinApp [MFC], RegisterShellFileTypes
- CWinApp [MFC], SetAppID
- CWinApp [MFC], SetRegistryKey
- CWinApp [MFC], UnregisterShellFileTypes
- CWinApp [MFC], m_bHelpMode
- CWinApp [MFC], m_eHelpType
- CWinApp [MFC], m_hInstance
- CWinApp [MFC], m_lpCmdLine
- CWinApp [MFC], m_nCmdShow
- CWinApp [MFC], m_pActiveWnd
- CWinApp [MFC], m_pszAppID
- CWinApp [MFC], m_pszAppName
- CWinApp [MFC], m_pszExeName
- CWinApp [MFC], m_pszHelpFilePath
- CWinApp [MFC], m_pszProfileName
- CWinApp [MFC], m_pszRegistryKey
- CWinApp [MFC], m_dwRestartManagerSupportFlags
- CWinApp [MFC], m_nAutosaveInterval
- CWinApp [MFC], m_pDataRecoveryHandler
ms.assetid: e426a3cd-0d15-40d6-bd55-beaa5feb2343
ms.openlocfilehash: 946de5768829330f84b826a1fc9b2f6278847357
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366837"
---
# <a name="cwinapp-class"></a>Klasa CWinApp

Klasa podstawowa, z której pochodzi obiekt aplikacji systemu Windows.

## <a name="syntax"></a>Składnia

```
class CWinApp : public CWinThread
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinApp::CWinApp](#cwinapp)|Konstruuje `CWinApp` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinApp::AddDocTemplate](#adddoctemplate)|Dodaje szablon dokumentu do listy dostępnych szablonów dokumentów aplikacji.|
|[CWinApp::Lista plików AddToRecentFile](#addtorecentfilelist)|Dodaje nazwę pliku do listy ostatnio używanych plików (MRU).|
|[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)|Wywoływane przez strukturę, gdy aplikacja nieoczekiwanie kończy działanie.|
|[CWinApp::Zamknij WszystkieDocuments](#closealldocuments)|Zamyka wszystkie otwarte dokumenty.|
|[CWinApp::CreatePrinterDC](#createprinterdc)|Tworzy kontekst urządzenia drukarki.|
|[CWinApp::DelRegTree](#delregtree)|Usuwa określony klucz i wszystkie jego podklu skróty.|
|[CWinApp::DoMessageBox](#domessagebox)|Implementuje [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) dla aplikacji.|
|[CWinApp::DoWaitCursor](#dowaitcursor)|Włącza i wyłącza kursor oczekiwania.|
|[CWinApp::Włącz obsługęD2DSupport](#enabled2dsupport)|Włącza obsługę aplikacji D2D. Wywołanie tej metody przed zainicjowaniem okna głównego.|
|[CWinApp::EnableHtmlHelp](#enablehtmlhelp)|Implementuje HTMLHelp dla aplikacji, a nie WinHelp.|
|[CWinApp::EnableTaskbarInteraction](#enabletaskbarinteraction)|Włącza interakcję na pasku zadań.|
|[CWinApp::Zakończ nienasyk](#exitinstance)|Zastądnąć, aby wyczyścić po zakończeniu aplikacji.|
|[CWinApp::GetApplicationRecoveryParameter](#getapplicationrecoveryparameter)|Pobiera parametr wejściowy dla metody odzyskiwania aplikacji.|
|[CWinApp::GetApplicationRecoveryPingInterval](#getapplicationrecoverypinginterval)|Zwraca czas oczekiwania menedżera ponownego uruchamiania na powrót funkcji wywołania zwrotnego odzyskiwania.|
|[CWinApp::GetApplicationRestartFlags](#getapplicationrestartflags)|Zwraca flagi menedżera ponownego uruchamiania.|
|[CWinApp::GetAppRegistryKey](#getappregistrykey)|Zwraca klucz dla HKEY_CURRENT_USER\\"Oprogramowanie"\RegistryKey\ProfileName.|
|[CWinApp::GetDataRecoveryHandler](#getdatarecoveryhandler)|Pobiera program obsługi odzyskiwania danych dla tego wystąpienia aplikacji.|
|[CWinApp::GetFirstDocTemplatePosition](#getfirstdoctemplateposition)|Pobiera położenie pierwszego szablonu dokumentu.|
|[CWinApp::GetHelpMode](#gethelpmode)|Pobiera typ pomocy używanej przez aplikację.|
|[CWinApp::GetNextDocTemplate](#getnextdoctemplate)|Pobiera położenie szablonu dokumentu. Może być używany rekurencyjnie.|
|[CWinApp::GetPrinterDeviceDefaults](#getprinterdevicedefaults)|Pobiera domyślne ustawienia urządzenia drukarki.|
|[CWinApp::GetProfileBinary](#getprofilebinary)|Pobiera dane binarne z wpisu w aplikacji . ini.|
|[CWinApp::GetProfileInt](#getprofileint)|Pobiera ć całkowitej z wpisu w aplikacji . ini.|
|[CWinApp::GetProfileStrowanie](#getprofilestring)|Pobiera ciąg z wpisu w aplikacji . ini.|
|[CWinApp::GetSectionKey](#getsectionkey)|Zwraca klucz dla HKEY_CURRENT_USER\\"Oprogramowanie"\RegistryKey\AppName\lpszSection.|
|[CWinApp::HideApplication](#hideapplication)|Ukrywa aplikację przed zamknięciem wszystkich dokumentów.|
|[CWinApp::HtmlHelp](#htmlhelp)|Wywołuje `HTMLHelp` funkcję systemu Windows.|
|[CWinApp::InitInstance](#initinstance)|Zastądeń, aby wykonać inicjowanie wystąpienia systemu Windows, takie jak tworzenie obiektów okna.|
|[CWinApp::IsTaskbarInteractionEnabled](#istaskbarinteractionenabled)|Informuje, czy interakcja na pasku zadań systemu Windows 7 jest włączona.|
|[CWinApp::LoadCursor](#loadcursor)|Ładuje zasób kursora.|
|[CWinApp::LoadIcon](#loadicon)|Ładuje zasób ikony.|
|[CWinApp::LoadOEMCursor](#loadoemcursor)|Ładuje wstępnie zdefiniowany kursor OEM systemu Windows, który **OCR_** stałe określają w systemie WINDOWS. H.|
|[CWinApp::LoadOEMIcon](#loadoemicon)|Ładuje wstępnie zdefiniowaną ikonę OEM systemu Windows, którą **OIC_** stałe określają w systemie WINDOWS. H.|
|[CWinApp::LoadStandardCursor](#loadstandardcursor)|Ładuje wstępnie zdefiniowany kursor systemu Windows, który **IDC_** stałe określają w systemie WINDOWS. H.|
|[CWinApp::LoadStandardicon](#loadstandardicon)|Ładuje wstępnie zdefiniowaną ikonę systemu Windows określoną w **systemie WINDOWS przez IDI_** stałe. H.|
|[CWinApp::OnDDECommand](#onddecommand)|Wywoływane przez platformę w odpowiedzi na polecenie dynamicznej wymiany danych (DDE).|
|[CWinApp::OnIdle](#onidle)|Zastąrpnąć, aby wykonać przetwarzanie w czasie bezczynnia specyficzne dla aplikacji.|
|[CWinApp::OpenDocumentFile](#opendocumentfile)|Wywoływana przez strukturę, aby otworzyć dokument z pliku.|
|[CWinApp::ParseCommandLine](#parsecommandline)|Analizuje poszczególne parametry i flagi w wierszu polecenia.|
|[CWinApp::PretranslateMessage](#pretranslatemessage)|Filtruje wiadomości przed wysłaniem ich do funkcji systemu Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).|
|[CWinApp::Pprotwofiltr](#processmessagefilter)|Przechwytuje niektóre komunikaty, zanim dotrą do aplikacji.|
|[CWinApp::ProcessShellCommand](#processshellcommand)|Obsługuje argumenty wiersza polecenia i flagi.|
|[CWinApp::ProcessWndProcException](#processwndprocexception)|Przechwytuje wszystkie nieobsługiwane wyjątki generowane przez komunikat aplikacji i programy obsługi poleceń.|
|[CWinApp::Zarejestruj się](#register)|Wykonuje niestandardową rejestrację.|
|[CWinApp::RegisterWithRestartManager](#registerwithrestartmanager)|Rejestruje aplikację za pomocą menedżera ponownego uruchamiania.|
|[CWinApp::ReopenPreviousFilesAtRestart](#reopenpreviousfilesatrestart)|Określa, czy menedżer ponownego uruchamiania ponownie otwiera pliki, które były otwarte po nieoczekiwanym zamknięciu aplikacji.|
|[CWinApp::Ponowne instance](#restartinstance)|Obsługuje ponowne uruchomienie aplikacji zainicjowane przez menedżera ponownego uruchamiania.|
|[CWinApp::RestoreAutosavedFilesAtRestart](#restoreautosavedfilesatrestart)|Określa, czy menedżer ponownego uruchamiania przywraca automatycznie odpisane pliki po ponownym uruchomieniu aplikacji.|
|[CWinApp::Uruchom](#run)|Uruchamia domyślną pętlę komunikatów. Zastąd, aby dostosować pętlę wiadomości.|
|[CWinApp::UruchomAutoma](#runautomated)|Testuje wiersz polecenia aplikacji dla opcji **/Automation.** Nieaktualne. Zamiast tego należy użyć wartości w [CCommandLineInfo::m_bRunAutomated](../../mfc/reference/ccommandlineinfo-class.md#m_brunautomated) po wywołaniu [ParseCommandLine](#parsecommandline).|
|[CWinApp::RunEmbedded](#runembedded)|Testuje wiersz polecenia aplikacji dla opcji **/Embedding.** Nieaktualne. Zamiast tego należy użyć wartości w [CCommandLineInfo::m_bRunEmbedded](../../mfc/reference/ccommandlineinfo-class.md#m_brunembedded) po wywołaniu [ParseCommandLine](#parsecommandline).|
|[CWinApp::SaveAllModified](#saveallmodified)|Monituje użytkownika o zapisanie wszystkich zmodyfikowanych dokumentów.|
|[CWinApp::Wybierajprinter](#selectprinter)|Wybiera drukarkę wcześniej wskazaną przez użytkownika za pomocą okna dialogowego drukowania.|
|[CWinApp::SetHelpMode](#sethelpmode)|Ustawia i inicjuje typ pomocy używanej przez aplikację.|
|[CWinApp::SupportsApplicationRecovery](#supportsapplicationrecovery)|Określa, czy menedżer ponownego uruchamiania odzyskuje aplikację, która nieoczekiwanie została zakończona.|
|[CWinApp::SupportsAutosaveAtInterval](#supportsautosaveatinterval)|Określa, czy menedżer ponownego uruchamiania automatycznie otwiera otwarte dokumenty w regularnych odstępach czasu.|
|[CWinApp::SupportsAutosaveAtRestart](#supportsautosaveatrestart)|Określa, czy menedżer ponownego uruchamiania automatycznie automatycznie uruchamia otwarte dokumenty po ponownym uruchomieniu aplikacji.|
|[CWinApp::SupportsRestartManager](#supportsrestartmanager)|Określa, czy aplikacja obsługuje menedżera ponownego uruchamiania.|
|[CWinApp::Wyrejestrowanie](#unregister)|Wyrejestruje wszystko, co `CWinApp` wiadomo, że są zarejestrowane przez obiekt.|
|[CWinApp::WinHelp](#winhelp)|Wywołuje `WinHelp` funkcję systemu Windows.|
|[CWinApp::WriteProfileBinary](#writeprofilebinary)|Zapisuje dane binarne do wpisu w aplikacji . ini.|
|[CWinApp::WriteProfileInt](#writeprofileint)|Zapisuje całkowitą ą do wpisu w aplikacji . ini.|
|[CWinApp::WriteProfileString](#writeprofilestring)|Zapisuje ciąg do wpisu w aplikacji . ini.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CWinApp::EnableShellOpen](#enableshellopen)|Umożliwia użytkownikowi otwieranie plików danych z Menedżera plików systemu Windows.|
|[CWinApp::LoadStdProfileSettings](#loadstdprofilesettings)|Ładuje standardowo . INI i włącza funkcję listy plików MRU.|
|[CWinApp::OnContextHelp](#oncontexthelp)|Obsługuje pomoc SHIFT+F1 w aplikacji.|
|[CWinApp::OnFileNowy](#onfilenew)|Implementuje polecenie ID_FILE_NEW.|
|[CWinApp::OnFileOpen](#onfileopen)|Implementuje polecenie ID_FILE_OPEN.|
|[CWinApp::OnFilePrintSetup](#onfileprintsetup)|Implementuje polecenie ID_FILE_PRINT_SETUP.|
|[CWinApp::OnHelp](#onhelp)|Obsługuje Pomoc F1 w aplikacji (przy użyciu bieżącego kontekstu).|
|[CWinApp::OnHelpFinder](#onhelpfinder)|Obsługuje polecenia ID_HELP_FINDER i ID_DEFAULT_HELP.|
|[CWinApp::OnHelpIndex](#onhelpindex)|Obsługuje polecenie ID_HELP_INDEX i udostępnia domyślny temat Pomocy.|
|[CWinApp::OnHelpUżywanie](#onhelpusing)|Obsługuje polecenie ID_HELP_USING.|
|[CWinApp::RegisterShellFileTypes](#registershellfiletypes)|Rejestruje wszystkie typy dokumentów aplikacji w Menedżerze plików systemu Windows.|
|[CWinApp::SetAppID](#setappid)|Jawnie ustawia identyfikator modelu użytkownika aplikacji dla aplikacji. Ta metoda powinna być wywoływana przed każdym interfejsem użytkownika jest przedstawiony użytkownikowi (najlepszym miejscem jest konstruktor aplikacji).|
|[CWinApp::SetRegistryKey](#setregistrykey)|Powoduje, że ustawienia aplikacji mają być przechowywane w rejestrze zamiast . pliki INI.|
|[CWinApp::Wyrejestrowanie plików Plików](#unregistershellfiletypes)|Wyrejestrowanie wszystkich typów dokumentów aplikacji za pomocą Menedżera plików systemu Windows.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CWinApp::m_bHelpMode](#m_bhelpmode)|Wskazuje, czy użytkownik znajduje się w trybie kontekstowym Pomocy (zwykle wywoływany za pomocą klawiszy SHIFT+F1).|
|[CWinApp::m_eHelpType](#m_ehelptype)|Określa typ pomocy używanej przez aplikację.|
|[CWinApp::m_hInstance](#m_hinstance)|Identyfikuje bieżące wystąpienie aplikacji.|
|[CWinApp::m_lpCmdLine](#m_lpcmdline)|Wskazuje ciąg zakończony zerem, który określa wiersz polecenia dla aplikacji.|
|[CWinApp::m_nCmdShow](#m_ncmdshow)|Określa, jak okno ma być wyświetlane początkowo.|
|[CWinApp::m_pActiveWnd](#m_pactivewnd)|Wskaźnik do głównego okna aplikacji kontenera, gdy serwer OLE jest aktywny w miejscu.|
|[CWinApp::m_pszAppID](#m_pszappid)|Identyfikator modelu użytkownika aplikacji.|
|[CWinApp::m_pszAppName](#m_pszappname)|Określa nazwę aplikacji.|
|[CWinApp::m_pszExeName](#m_pszexename)|Nazwa modułu aplikacji.|
|[CWinApp::m_pszHelpFilePath](#m_pszhelpfilepath)|Ścieżka do pliku Pomocy aplikacji.|
|[CWinApp::m_pszProfileName](#m_pszprofilename)|Aplikacja jest . nazwa pliku INI.|
|[CWinApp::m_pszRegistryKey](#m_pszregistrykey)|Służy do określania pełnego klucza rejestru do przechowywania ustawień profilu aplikacji.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CWinApp::m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags)|Flagi, które określają, jak zachowuje się menedżer ponownego uruchamiania.|
|[CWinApp::m_nAutosaveInterval](#m_nautosaveinterval)|Czas w milisekundach między autosaves.|
|[CWinApp::m_pDataRecoveryHandler](#m_pdatarecoveryhandler)|Wskaźnik do programu obsługi odzyskiwania danych dla aplikacji.|

## <a name="remarks"></a>Uwagi

Obiekt aplikacji udostępnia funkcje członkowskie do inicjowania aplikacji (i każdego wystąpienia) i uruchamiania aplikacji.

Każda aplikacja, która używa klas programu Microsoft Foundation, `CWinApp`może zawierać tylko jeden obiekt pochodzący z programu . Ten obiekt jest konstruowany, gdy inne obiekty globalne języka C++ są konstruowane i jest już dostępna, gdy system Windows wywołuje `WinMain` funkcję, która jest dostarczana przez bibliotekę klas Microsoft Foundation. Zadeklaruj obiekt pochodny `CWinApp` na poziomie globalnym.

Po wyprowadzeniu klasy `CWinApp`aplikacji z , zastąpić [initinstance](#initinstance) funkcji elementu członkowskiego, aby utworzyć obiekt okna głównego aplikacji.

Oprócz funkcji `CWinApp` członkowskich biblioteka klas programu Microsoft Foundation udostępnia następujące `CWinApp` funkcje globalne, aby uzyskać dostęp do obiektu i innych informacji globalnych:

- [AfxGetApp (AfxGetApp)](application-information-and-management.md#afxgetapp) Uzyskuje wskaźnik do `CWinApp` obiektu.

- [AfxGetInstanceHandle (Uchwyt afxgetinstance)](application-information-and-management.md#afxgetinstancehandle) Uzyskuje dojście do bieżącego wystąpienia aplikacji.

- [AfxGetResourceHandle (AfxGetResourceHandle)](application-information-and-management.md#afxgetresourcehandle) Uzyskuje dojście do zasobów aplikacji.

- [AfxGetAppName (Nazwa aplikacji AfxGetAppName)](application-information-and-management.md#afxgetappname) Uzyskuje wskaźnik do ciągu zawierającego nazwę aplikacji. Alternatywnie, jeśli masz wskaźnik `CWinApp` do obiektu, użyj, `m_pszExeName` aby uzyskać nazwę aplikacji.

Zobacz [CWinApp: Klasa aplikacji,](../../mfc/cwinapp-the-application-class.md) `CWinApp` aby uzyskać więcej informacji na temat klasy, w tym przegląd następujących czynności:

- `CWinApp`-pochodny kod napisany przez Kreatora aplikacji.

- `CWinApp`'s rolę w sekwencji wykonywania aplikacji.

- `CWinApp`'s domyślne implementacje funkcji elementu członkowskiego.

- `CWinApp`'s klucz overridables.

Element `m_hPrevInstance` członkowski danych już nie istnieje. Aby ustalić, czy inne wystąpienie aplikacji jest uruchomione, należy użyć nazwanego obiektu mutex. Jeśli otwarcie obiektu mutex nie powiedzie się, nie ma żadnych innych wystąpień uruchomionej aplikacji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwinthread](../../mfc/reference/cwinthread-class.md)

`CWinApp`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cwinappadddoctemplate"></a><a name="adddoctemplate"></a>CWinApp::AddDocTemplate

Wywołanie tej funkcji elementu członkowskiego, aby dodać szablon dokumentu do listy dostępnych szablonów dokumentów, które przechowuje aplikacja.

```
void AddDocTemplate(CDocTemplate* pTemplate);
```

### <a name="parameters"></a>Parametry

*pTemplate*<br/>
Wskaźnik do `CDocTemplate` dodania.

### <a name="remarks"></a>Uwagi

Przed wywołaniem programu [RegisterShellFileTypes](#registershellfiletypes)należy dodać wszystkie szablony dokumentów do aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#35](../../mfc/reference/codesnippet/cpp/cwinapp-class_1.cpp)]

## <a name="cwinappaddtorecentfilelist"></a><a name="addtorecentfilelist"></a>CWinApp::Lista plików AddToRecentFile

Wywołanie tej funkcji elementu członkowskiego, aby dodać *lpszPathName* do listy plików MRU.

```
virtual void AddToRecentFileList(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parametry

*lpszPathName (nazwa lpszPathName)*<br/>
Ścieżka pliku.

### <a name="remarks"></a>Uwagi

Należy wywołać [LoadStdProfileSettings](#loadstdprofilesettings) funkcji członkowskiej, aby załadować bieżącą listę plików MRU przed użyciem tej funkcji elementu członkowskiego.

Struktura wywołuje tę funkcję elementu członkowskiego, gdy otwiera plik lub wykonuje polecenie Zapisz jako, aby zapisać plik o nowej nazwie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#36](../../mfc/reference/codesnippet/cpp/cwinapp-class_2.cpp)]

## <a name="cwinappapplicationrecoverycallback"></a><a name="applicationrecoverycallback"></a>CWinApp::ApplicationRecoveryCallback

Wywoływane przez strukturę, gdy aplikacja nieoczekiwanie kończy działanie.

```
virtual DWORD ApplicationRecoveryCallback(LPVOID lpvParam);
```

### <a name="parameters"></a>Parametry

*lpvParam*<br/>
[w] Zarezerwowane do wykorzystania w przyszłości.

### <a name="return-value"></a>Wartość zwracana

0, jeśli ta metoda zakończy się powodzeniem; nonzero, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja obsługuje menedżera ponownego uruchamiania, struktura wywołuje tę funkcję, gdy aplikacja nieoczekiwanie kończy działanie.

Domyślna implementacja `ApplicationRecoveryCallback` używa `CDataRecoveryHandler` do zapisania listy aktualnie otwartych dokumentów w rejestrze. Ta metoda nie powoduje automatycznego wypisywu żadnych plików.

Aby dostosować zachowanie, należy zastąpić tę funkcję w pochodnej [klasie CWinApp](../../mfc/reference/cwinapp-class.md) lub przekazać własną metodę odzyskiwania aplikacji jako parametr do [CWinApp::RegisterWithRestartManager](#registerwithrestartmanager).

## <a name="cwinappclosealldocuments"></a><a name="closealldocuments"></a>CWinApp::Zamknij WszystkieDocuments

Wywołanie tej funkcji elementu członkowskiego, aby zamknąć wszystkie otwarte dokumenty przed zamknięciem.

```
void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>Parametry

*bEndSession (Niesienie)*<br/>
Określa, czy sesja systemu Windows jest zakończona. Jest prawda, jeśli sesja jest zakończona; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Zadzwoń [hideApplication](#hideapplication) `CloseAllDocuments`przed wywołaniem .

## <a name="cwinappcreateprinterdc"></a><a name="createprinterdc"></a>CWinApp::CreatePrinterDC

Wywołanie tej funkcji elementu członkowskiego, aby utworzyć kontekst urządzenia drukarki (DC) z wybranej drukarki.

```
BOOL CreatePrinterDC(CDC& dc);
```

### <a name="parameters"></a>Parametry

*Dc*<br/>
Odwołanie do kontekstu urządzenia drukarki.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli kontekst urządzenia drukarki został utworzony pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`CreatePrinterDC`inicjuje kontekst urządzenia, który przechodzisz przez odniesienie, dzięki czemu można go użyć do drukowania.

Jeśli funkcja zakończy się pomyślnie, po zakończeniu drukowania należy zniszczyć kontekst urządzenia. Można pozwolić destruktora obiektu [CDC](../../mfc/reference/cdc-class.md) to zrobić, lub można to zrobić jawnie, wywołując [CDC::DeleteDC](../../mfc/reference/cdc-class.md#deletedc).

## <a name="cwinappcwinapp"></a><a name="cwinapp"></a>CWinApp::CWinApp

Konstruuje `CWinApp` obiekt i przekazuje *lpszAppName* do przechowywania jako nazwa aplikacji.

```
CWinApp(LPCTSTR lpszAppName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszAppName*<br/>
Ciąg zakończony z wartością null, który zawiera nazwę aplikacji używaną przez system Windows. Jeśli ten argument nie jest `CWinApp` podany lub ma wartość NULL, używa ciągu zasobu AFX_IDS_APP_TITLE lub nazwy pliku wykonywalnego.

### <a name="remarks"></a>Uwagi

Należy skonstruować jeden obiekt `CWinApp`globalny klasy pochodnej. W aplikacji może `CWinApp` być tylko jeden obiekt. Konstruktor przechowuje wskaźnik `CWinApp` do `WinMain` obiektu, dzięki czemu można wywołać funkcje członkowskie obiektu, aby zainicjować i uruchomić aplikację.

## <a name="cwinappdelregtree"></a><a name="delregtree"></a>CWinApp::DelRegTree

Usuwa określony klucz rejestru i wszystkie jego podkluczy.

```
LONG DelRegTree(
    HKEY hParentKey,
    const CString& strKeyName);

LONG DelRegTree(
    HKEY hParentKey,
    const CString& strKeyName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*hParentKey (Klucz)*<br/>
Obsługa klucza rejestru.

*nazwa_klucza strKey*<br/>
Nazwa klucza rejestru do usunięcia.

*Ptm*<br/>
Wskaźnik do obiektu CAtlTransactionManager.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się, zwracana wartość jest ERROR_SUCCESS. Jeśli funkcja nie powiedzie się, zwracana wartość jest kodem błędu niezerowego zdefiniowanym w Winerror.h.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby usunąć określony klucz i jego podklunia.

## <a name="cwinappdomessagebox"></a><a name="domessagebox"></a>CWinApp::DoMessageBox

Struktura wywołuje tę funkcję elementu członkowskiego, aby zaimplementować okno komunikatu dla funkcji globalnej [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox).

```
virtual int DoMessageBox(
    LPCTSTR lpszPrompt,
    UINT nType,
    UINT nIDPrompt);
```

### <a name="parameters"></a>Parametry

*lpszPrompt*<br/>
Adres tekstu w oknie komunikatu.

*nTyp*<br/>
[Styl](../../mfc/reference/styles-used-by-mfc.md#message-box-styles)okna komunikatu .

*nIDPrompt ( nIDPrompt )*<br/>
Indeks do ciągu kontekstu Pomocy.

### <a name="return-value"></a>Wartość zwracana

Zwraca te same `AfxMessageBox`wartości co .

### <a name="remarks"></a>Uwagi

Nie należy wywoływać tej funkcji elementu członkowskiego, aby otworzyć okno komunikatu; zamiast `AfxMessageBox` tego użyć.

Zastąpozuj tę funkcję elementu członkowskiego, `AfxMessageBox` aby dostosować przetwarzanie wywołań w całej aplikacji.

## <a name="cwinappdowaitcursor"></a><a name="dowaitcursor"></a>CWinApp::DoWaitCursor

Ta funkcja elementu członkowskiego jest wywoływana przez platformę do implementacji [CWaitCursor](../../mfc/reference/cwaitcursor-class.md), [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)i [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor).

```
virtual void DoWaitCursor(int nCode);
```

### <a name="parameters"></a>Parametry

*kod n*<br/>
Jeśli ten parametr wynosi 1, pojawi się kursor oczekiwania. Jeśli 0, kursor oczekiwania zostanie przywrócony bez zwiększania liczby odwołań. Jeśli -1, kursor oczekiwania kończy się.

### <a name="remarks"></a>Uwagi

Domyślnie implementuje kursor klepsydry. `DoWaitCursor`utrzymuje liczbę odwołań. Gdy jest dodatni, wyświetlany jest kursor klepsydry.

Chociaż zwykle nie można `DoWaitCursor` wywołać bezpośrednio, można zastąpić tę funkcję elementu członkowskiego, aby zmienić kursor oczekiwania lub wykonać dodatkowe przetwarzanie, gdy wyświetlany jest kursor oczekiwania.

Aby uzyskać łatwiejszy, usprawniony sposób zaimplementowania `CWaitCursor`kursora oczekiwania, użyj programu .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#37](../../mfc/reference/codesnippet/cpp/cwinapp-class_3.cpp)]

## <a name="cwinappenabled2dsupport"></a><a name="enabled2dsupport"></a>CWinApp::Włącz obsługęD2DSupport

Wymagany jest dodatek SP1 dla programu Visual Studio 2010.

Włącza obsługę aplikacji D2D. Wywołanie tej metody przed zainicjowaniem okna głównego.

```
BOOL EnableD2DSupport(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>Parametry

*d2dFaktoryp*<br/>
Model wątków fabryki D2D i zasobów, które tworzy.

*writeFactoryType (Typ danych)*<br/>
Wartość określająca, czy obiekt fabryczny zapisu będzie współużytkowany, czy izolowany

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli obsługa D2D została włączona, FALSE - w przeciwnym razie

## <a name="cwinappenablehtmlhelp"></a><a name="enablehtmlhelp"></a>CWinApp::EnableHtmlHelp

Wywołanie tej funkcji elementu członkowskiego `CWinApp`z wewnątrz konstruktora klasy pochodnej do korzystania z HTMLHelp dla aplikacji pomocy.

```
void EnableHtmlHelp();
```

### <a name="remarks"></a>Uwagi

## <a name="cwinappenableshellopen"></a><a name="enableshellopen"></a>CWinApp::EnableShellOpen

Wywołanie tej funkcji, `InitInstance` zazwyczaj z zastąpienia, aby umożliwić użytkownikom aplikacji, aby otworzyć pliki danych po dwukrotnym kliknięciu plików z poziomu Menedżera plików systemu Windows.

```
void EnableShellOpen();
```

### <a name="remarks"></a>Uwagi

Wywołanie `RegisterShellFileTypes` funkcji elementu członkowskiego w połączeniu z tą funkcją lub podaj plik . REG z aplikacją do ręcznej rejestracji typów dokumentów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#38](../../mfc/reference/codesnippet/cpp/cwinapp-class_4.cpp)]

## <a name="cwinappenabletaskbarinteraction"></a><a name="enabletaskbarinteraction"></a>CWinApp::EnableTaskbarInteraction

Włącza interakcję na pasku zadań.

```
BOOL EnableTaskbarInteraction(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
Określa, czy interakcja z paskiem zadań systemu Windows 7 powinna być włączona (PRAWDA), czy wyłączona (FAŁSZ).

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli interakcja na pasku zadań może być włączona lub wyłączona.

### <a name="remarks"></a>Uwagi

Ta metoda musi być wywoływana przed utworzeniem okna głównego, w przeciwnym razie potwierdza i zwraca FALSE.

## <a name="cwinappexitinstance"></a><a name="exitinstance"></a>CWinApp::Zakończ nienasyk

Wywoływane przez strukturę `Run` z wewnątrz funkcji elementu członkowskiego, aby zakończyć to wystąpienie aplikacji.

```
virtual int ExitInstance();
```

### <a name="return-value"></a>Wartość zwracana

Kod zakończenia aplikacji; 0 oznacza brak błędów, a wartości większe niż 0 wskazują błąd. Ta wartość jest używana jako `WinMain`wartość zwracana z .

### <a name="remarks"></a>Uwagi

Nie należy wywoływać tej funkcji `Run` elementu członkowskiego z dowolnego miejsca, ale w ramach funkcji elementu członkowskiego.

Domyślna implementacja tej funkcji zapisuje opcje struktury do aplikacji . ini. Zastąd w tej funkcji należy wyczyścić po zakończeniu działania aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#39](../../mfc/reference/codesnippet/cpp/cwinapp-class_5.cpp)]

## <a name="cwinappgetapplicationrecoveryparameter"></a><a name="getapplicationrecoveryparameter"></a>CWinApp::GetApplicationRecoveryParameter

Pobiera parametr wejściowy dla metody odzyskiwania aplikacji.

```
virtual LPVOID GetApplicationRecoveryParameter();
```

### <a name="return-value"></a>Wartość zwracana

Domyślny parametr wejściowy dla metody odzyskiwania aplikacji.

### <a name="remarks"></a>Uwagi

Domyślne zachowanie tej funkcji zwraca wartość NULL.

Aby uzyskać więcej informacji, zobacz [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).

## <a name="cwinappgetapplicationrecoverypinginterval"></a><a name="getapplicationrecoverypinginterval"></a>CWinApp::GetApplicationRecoveryPingInterval

Zwraca czas oczekiwania menedżera ponownego uruchamiania na powrót funkcji wywołania zwrotnego odzyskiwania.

```
virtual DWORD GetApplicationRecoveryPingInterval();
```

### <a name="return-value"></a>Wartość zwracana

Czas w milisekundach.

### <a name="remarks"></a>Uwagi

Gdy aplikacja, która jest zarejestrowana w menedżerze ponownego uruchamiania nieoczekiwanie, aplikacja próbuje zapisać otwarte dokumenty i wywołuje funkcję wywołania zwrotnego odzyskiwania. Domyślną funkcją wywołania zwrotnego odzyskiwania jest [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).

Czas oczekiwania na powrót funkcji wywołania zwrotnego odzyskiwania jest interwałem pingu. Interwał pingu można dostosować, `CWinApp::GetApplicationRecoveryPingInterval` zastępując lub udostępniając `RegisterWithRestartManager`wartość niestandardową do pliku .

## <a name="cwinappgetapplicationrestartflags"></a><a name="getapplicationrestartflags"></a>CWinApp::GetApplicationRestartFlags

Zwraca flagi menedżera ponownego uruchamiania.

```
virtual DWORD GetApplicationRestartFlags();
```

### <a name="return-value"></a>Wartość zwracana

Flagi menedżera ponownego uruchamiania. Domyślna implementacja zwraca wartość 0.

### <a name="remarks"></a>Uwagi

Flagi menedżera ponownego uruchamiania nie mają wpływu na domyślną implementację. Są one przeznaczone do wykorzystania w przyszłości.

Flagi można ustawić podczas rejestrowania aplikacji w menedżerze ponownego uruchamiania przy użyciu [CWinApp::RegisterWithRestartManager](#registerwithrestartmanager).

Możliwe wartości flag menedżera ponownego uruchamiania są następujące:

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

## <a name="cwinappgetappregistrykey"></a><a name="getappregistrykey"></a>CWinApp::GetAppRegistryKey

Zwraca klucz HKEY_CURRENT_USER\\"Oprogramowanie"\RegistryKey\ProfileName.

```
HKEY GetAppRegistryKey(CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*Ptm*<br/>
Wskaźnik do `CAtlTransactionManager` obiektu.

### <a name="return-value"></a>Wartość zwracana

Klucz aplikacji, jeśli funkcja powiedzie się; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

## <a name="cwinappgetdatarecoveryhandler"></a><a name="getdatarecoveryhandler"></a>CWinApp::GetDataRecoveryHandler

Pobiera program obsługi odzyskiwania danych dla tego wystąpienia aplikacji.

```
virtual CDataRecoveryHandler *GetDataRecoveryHandler();
```

### <a name="return-value"></a>Wartość zwracana

Program obsługi odzyskiwania danych dla tego wystąpienia aplikacji.

### <a name="remarks"></a>Uwagi

Każda aplikacja, która używa menedżera ponownego uruchamiania musi mieć jedno wystąpienie [CDataRecoveryHandler Klasy](../../mfc/reference/cdatarecoveryhandler-class.md). Ta klasa jest odpowiedzialna za monitorowanie otwartych dokumentów i automatycznego łatania plików. Zachowanie `CDataRecoveryHandler` zależy od konfiguracji menedżera ponownego uruchamiania. Aby uzyskać więcej informacji, zobacz [CDataRecoveryHandler Class](../../mfc/reference/cdatarecoveryhandler-class.md).

Ta metoda zwraca wartość NULL w systemach operacyjnych wcześniejszych niż Windows Vista. Menedżer ponownego uruchamiania nie jest obsługiwany w systemach operacyjnych wcześniej niż Windows Vista.

Jeśli aplikacja nie ma obecnie obsługi odzyskiwania danych, ta metoda tworzy jeden i zwraca wskaźnik do niego.

## <a name="cwinappgetfirstdoctemplateposition"></a><a name="getfirstdoctemplateposition"></a>CWinApp::GetFirstDocTemplatePosition

Pobiera pozycję pierwszego szablonu dokumentu w aplikacji.

```
POSITION GetFirstDocTemplatePosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość POSITION, która może służyć do iteracji lub pobierania wskaźnika obiektu; NULL, jeśli lista jest pusta.

### <a name="remarks"></a>Uwagi

Użyj wartości POSITION zwróconej w wywołaniu [GetNextDocTemplate,](#getnextdoctemplate) aby uzyskać pierwszy obiekt [CDocTemplate.](../../mfc/reference/cdoctemplate-class.md)

## <a name="cwinappgethelpmode"></a><a name="gethelpmode"></a>CWinApp::GetHelpMode

Pobiera typ pomocy używanej przez aplikację.

```
AFX_HELP_TYPE GetHelpMode();
```

### <a name="return-value"></a>Wartość zwracana

Typ pomocy używany przez aplikację. Aby uzyskać więcej informacji, zobacz [CWinApp::m_eHelpType.](#m_ehelptype)

## <a name="cwinappgetnextdoctemplate"></a><a name="getnextdoctemplate"></a>CWinApp::GetNextDocTemplate

Pobiera szablon dokumentu identyfikowany przez *poz,* a następnie ustawia *wartość pos* na wartość POSITION.

```
CDocTemplate* GetNextDocTemplate(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Odwołanie do wartości POSITION zwróconej przez `GetNextDocTemplate` poprzednie wywołanie do lub [GetFirstDocTemplatePosition](#getfirstdoctemplateposition). Wartość jest aktualizowana do następnej pozycji przez to wywołanie.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [CDocTemplate.](../../mfc/reference/cdoctemplate-class.md)

### <a name="remarks"></a>Uwagi

Można użyć `GetNextDocTemplate` w pętli iteracji do przodu, jeśli ustalisz pozycję początkową za pomocą wywołania `GetFirstDocTemplatePosition`.

Należy upewnić się, że wartość POSITION jest prawidłowa. Jeśli jest nieprawidłowa, wersja debugowania biblioteki klas programu Microsoft Foundation potwierdza.

Jeśli pobrany szablon dokumentu jest ostatnim dostępnym, nowa wartość *pos* jest ustawiona na wartość NULL.

## <a name="cwinappgetprinterdevicedefaults"></a><a name="getprinterdevicedefaults"></a>CWinApp::GetPrinterDeviceDefaults

Wywołanie tej funkcji elementu członkowskiego, aby przygotować kontekst urządzenia drukarki do drukowania.

```
BOOL GetPrinterDeviceDefaults(struct tagPDA* pPrintDlg);
```

### <a name="parameters"></a>Parametry

*pPrintDlg (DrukDlg)*<br/>
Wskaźnik do struktury [PRINTDLG.](/windows/win32/api/commdlg/ns-commdlg-printdlga)

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pobiera bieżące ustawienia domyślne drukarki z systemu Windows . W razie potrzeby lub używa ostatniej konfiguracji drukarki ustawionej przez użytkownika w Instalatorze wydruku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#40](../../mfc/reference/codesnippet/cpp/cwinapp-class_6.cpp)]

## <a name="cwinappgetprofilebinary"></a><a name="getprofilebinary"></a>CWinApp::GetProfileBinary

Wywołanie tej funkcji elementu członkowskiego w celu pobrania danych binarnych z wpisu w określonej sekcji rejestru aplikacji lub . ini.

```
BOOL GetProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE* ppData,
    UINT* pBytes);
```

### <a name="parameters"></a>Parametry

*lpszSekcja*<br/>
Wskazuje ciąg zakończony zerem, który określa sekcję zawierającą wpis.

*lpszEntry*<br/>
Wskazuje ciąg zakończony zerem, który zawiera wpis, którego wartość ma zostać pobrana.

*ppData (dane)*<br/>
Wskazuje wskaźnik, który otrzyma adres danych.

*p Bajty*<br/>
Wskazuje UINT, który otrzyma rozmiar danych (w bajtach).

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

W tej funkcji elementu członkowskiego nie jest rozróżniana wielkość liter, więc ciągi w parametrach *lpszSection* i *lpszEntry* mogą się różnić w przypadku.

> [!NOTE]
> `GetProfileBinary`przydziela bufor i zwraca jego \* adres w *ppData*. Osoba dzwoniąca jest odpowiedzialna za zwalnianie buforu za pomocą **delete []**.

> [!IMPORTANT]
> Dane zwracane przez tę funkcję nie musi być zakończone wartością NULL, a wywołujący musi wykonać sprawdzanie poprawności. Aby uzyskać więcej informacji, zobacz [Unikanie przekroczenia buforu](/windows/win32/SecBP/avoiding-buffer-overruns).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#41](../../mfc/reference/codesnippet/cpp/cwinapp-class_7.cpp)]

Aby uzyskać dodatkowy przykład, zobacz [CWinApp::WriteProfileBinary](#writeprofilebinary).

## <a name="cwinappgetprofileint"></a><a name="getprofileint"></a>CWinApp::GetProfileInt

Wywołanie tej funkcji elementu członkowskiego w celu pobrania wartości liczby całkowitej z wpisu w określonej sekcji rejestru aplikacji lub . ini.

```
UINT GetProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nDefault);
```

### <a name="parameters"></a>Parametry

*lpszSekcja*<br/>
Wskazuje ciąg zakończony zerem, który określa sekcję zawierającą wpis.

*lpszEntry*<br/>
Wskazuje ciąg zakończony zerem, który zawiera wpis, którego wartość ma zostać pobrana.

*nDefault (Domyślne)*<br/>
Określa wartość domyślną do zwrócenia, jeśli struktura nie może znaleźć wpisu.

### <a name="return-value"></a>Wartość zwracana

Wartość całkowita ciągu, który następuje po określonym wpisie, jeśli funkcja zakończy się pomyślnie. Zwracana wartość jest wartością parametru *nDefault,* jeśli funkcja nie znajduje wpisu. Zwracana wartość wynosi 0, jeśli wartość odpowiadająca określonemu wpisowi nie jest całkowitej liczby.

Ta funkcja elementu członkowskiego obsługuje notację szesnastkową dla wartości w pliku . ini. Podczas pobierania podpisanej liczby całkowitej należy przelać ją na **int**.

### <a name="remarks"></a>Uwagi

W tej funkcji elementu członkowskiego nie jest rozróżniana wielkość liter, więc ciągi w parametrach *lpszSection* i *lpszEntry* mogą się różnić w przypadku.

> [!IMPORTANT]
> Dane zwracane przez tę funkcję nie musi być zakończone wartością NULL, a wywołujący musi wykonać sprawdzanie poprawności. Aby uzyskać więcej informacji, zobacz [Unikanie przekroczenia buforu](/windows/win32/SecBP/avoiding-buffer-overruns).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#42](../../mfc/reference/codesnippet/cpp/cwinapp-class_8.cpp)]

Aby uzyskać dodatkowy przykład, zobacz [CWinApp::WriteProfileInt](#writeprofileint).

## <a name="cwinappgetprofilestring"></a><a name="getprofilestring"></a>CWinApp::GetProfileStrowanie

Wywołanie tej funkcji elementu członkowskiego w celu pobrania ciągu skojarzonego z wpisem w określonej sekcji w rejestrze aplikacji lub . ini.

```
CString GetProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszDefault = NULL);
```

### <a name="parameters"></a>Parametry

*lpszSekcja*<br/>
Wskazuje ciąg zakończony zerem, który określa sekcję zawierającą wpis.

*lpszEntry*<br/>
Wskazuje ciąg zakończony zerem, który zawiera wpis, którego ciąg ma zostać pobrany. Ta wartość nie może być null.

*lpszDefault (ł.*<br/>
Wskazuje domyślną wartość ciągu dla danego wpisu, jeśli nie można znaleźć wpisu w pliku inicjowania.

### <a name="return-value"></a>Wartość zwracana

Zwracana wartość jest ciągiem z aplikacji . INI lub *lpszDefault,* jeśli nie można odnaleźć ciągu. Maksymalna długość ciągu obsługiwane przez ramy jest _MAX_PATH. Jeśli *lpszDefault* ma wartość NULL, zwracana wartość jest pustym ciągiem.

### <a name="remarks"></a>Uwagi

> [!IMPORTANT]
> Dane zwracane przez tę funkcję nie musi być zakończone wartością NULL, a wywołujący musi wykonać sprawdzanie poprawności. Aby uzyskać więcej informacji, zobacz [Unikanie przekroczenia buforu](/windows/win32/SecBP/avoiding-buffer-overruns).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

Inny przykład można znaleźć w przykładzie [aplikacji CWinApp::GetProfileInt](#getprofileint).

## <a name="cwinappgetsectionkey"></a><a name="getsectionkey"></a>CWinApp::GetSectionKey

Zwraca klucz HKEY_CURRENT_USER\\"Oprogramowanie"\RegistryKey\AppName\lpszSection.

```
HKEY GetSectionKey(
    LPCTSTR lpszSection,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*lpszSekcja*<br/>
Nazwa klucza, który ma zostać uzyskany.

*Ptm*<br/>
Wskaźnik do `CAtlTransactionManager` obiektu.

### <a name="return-value"></a>Wartość zwracana

Klucz przekroju, jeśli funkcja powiedzie się; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

## <a name="cwinapphideapplication"></a><a name="hideapplication"></a>CWinApp::HideApplication

Wywołanie tej funkcji elementu członkowskiego, aby ukryć aplikację przed zamknięciem otwartych dokumentów.

```
void HideApplication();
```

## <a name="cwinapphtmlhelp"></a><a name="htmlhelp"></a>CWinApp::HtmlHelp

Wywołanie tej funkcji elementu członkowskiego, aby wywołać aplikację HTMLHelp.

```
virtual void HtmlHelp(
    DWORD_PTR dwData,
    UINT nCmd = 0x000F);
```

### <a name="parameters"></a>Parametry

*dwData (dane)*<br/>
Określa dodatkowe dane. Używana wartość zależy od wartości parametru *nCmd.* Wartości domyślne, co `0x000F` oznacza [HH_HELP_CONTEXT](/previous-versions/windows/desktop/htmlhelp/hh-help-context-command).

*nCmd (wł.)*<br/>
Określa typ żądanej pomocy. Aby uzyskać listę możliwych wartości i ich wpływ na parametr *dwData,* zobacz parametr *uCommand* opisany w funkcji interfejsu API [HtmlHelpW](/windows/win32/api/htmlhelp/nf-htmlhelp-htmlhelpw) lub [HtmlHelpA](/windows/win32/api/htmlhelp/nf-htmlhelp-htmlhelpa) w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Struktura również wywołuje tę funkcję, aby wywołać aplikację HTMLHelp.

Struktura automatycznie zamknie aplikację HTMLHelp po zakończeniu aplikacji.

## <a name="cwinappinitinstance"></a><a name="initinstance"></a>CWinApp::InitInstance

System Windows umożliwia uruchamianie kilku kopii tego samego programu w tym samym czasie.

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli inicjowanie zakończy się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Inicjowanie aplikacji jest koncepcyjnie podzielone na dwie sekcje: jednorazowa inicjalizacja aplikacji, która jest wykonywana po raz pierwszy uruchamia program, i inicjowanie wystąpienia, które jest uruchamiane za każdym razem, gdy jest uruchamiana kopia programu, w tym po raz pierwszy. Implementacja ram nazywa `WinMain` tę funkcję.

Zastąrpnąć, aby zainicjować każde nowe wystąpienie `InitInstance` aplikacji uruchomionej w systemie Windows. Zazwyczaj należy zastąpić `InitInstance` do konstruowania obiektu okna `CWinThread::m_pMainWnd` głównego i ustawić element członkowski danych, aby wskazać to okno. Aby uzyskać więcej informacji na temat zastępowania tej funkcji elementu członkowskiego, zobacz [CWinApp: Klasa aplikacji](../../mfc/cwinapp-the-application-class.md).

> [!NOTE]
> Aplikacje MFC muszą być inicjowane jako jednowątkowy apartament (STA). Jeśli wywołasz [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) w przesłonie, `InitInstance` określ COINIT_APARTMENTTHREADED (a nie COINIT_MULTITHREADED).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCListView#9](../../atl/reference/codesnippet/cpp/cwinapp-class_10.cpp)]

## <a name="cwinappistaskbarinteractionenabled"></a><a name="istaskbarinteractionenabled"></a>CWinApp::IsTaskbarInteractionEnabled

Informuje, czy interakcja na pasku zadań systemu Windows 7 jest włączona.

```
virtual BOOL IsTaskbarInteractionEnabled();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość `EnableTaskbarInteraction` PRAWDA, jeśli został wywołany, a system operacyjny to Windows 7 lub nowsze.

### <a name="remarks"></a>Uwagi

Interakcja na pasku zadań oznacza, że aplikacja MDI wyświetla zawartość wiązek podrzędnych MDI w oddzielnych miniaturach z kartami, które pojawiają się, gdy wskaźnik myszy znajduje się nad przyciskiem paska zadań aplikacji.

## <a name="cwinapploadcursor"></a><a name="loadcursor"></a>CWinApp::LoadCursor

Ładuje zasób kursora nazwany przez *lpszResourceName* lub określony przez *nIDResource* z bieżącego pliku wykonywalnego.

```
HCURSOR LoadCursor(LPCTSTR lpszResourceName) const;  HCURSOR LoadCursor(UINT nIDResource) const;
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Wskazuje ciąg zakończony z wartością null, który zawiera nazwę zasobu kursora. Można użyć `CString` dla tego argumentu.

*nIDSerwród*<br/>
Identyfikator zasobu kursora. Aby uzyskać listę zasobów, zobacz [LoadCursor](/windows/win32/api/winuser/nf-winuser-loadcursorw) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Dojście do kursora, jeśli zakończy się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

`LoadCursor`ładuje kursor do pamięci tylko wtedy, gdy nie został wcześniej załadowany; w przeciwnym razie pobiera dojście istniejącego zasobu.

Użyj funkcji [członkowskiej LoadStandardCursor](#loadstandardcursor) lub [LoadOEMCursor,](#loadoemcursor) aby uzyskać dostęp do wstępnie zdefiniowanych kursorów systemu Windows.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#44](../../mfc/reference/codesnippet/cpp/cwinapp-class_11.cpp)]

## <a name="cwinapploadicon"></a><a name="loadicon"></a>CWinApp::LoadIcon

Ładuje zasób ikony nazwany przez *lpszResourceName* lub określony przez *nIDResource* z pliku wykonywalnego.

```
HICON LoadIcon(LPCTSTR lpszResourceName) const;  HICON LoadIcon(UINT nIDResource) const;
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Wskazuje ciąg zakończony z wartością null, który zawiera nazwę zasobu ikony. Można również użyć `CString` dla tego argumentu.

*nIDSerwród*<br/>
Numer identyfikatora zasobu ikony.

### <a name="return-value"></a>Wartość zwracana

Uchwyt do ikony, jeśli się powiedzie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

`LoadIcon`ładuje ikonę tylko wtedy, gdy nie została wcześniej załadowana; w przeciwnym razie pobiera dojście istniejącego zasobu.

Można użyć funkcji elementu członkowskiego [LoadStandardIcon](#loadstandardicon) lub [LoadOEMIcon,](#loadoemicon) aby uzyskać dostęp do wstępnie zdefiniowanych ikon systemu Windows.

> [!NOTE]
> Ta funkcja elementu członkowskiego wywołuje funkcję interfejsu API Win32 [LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw), która może załadować tylko ikonę, której rozmiar jest zgodny z wartościami metryk SM_CXICON i SM_CYICON systemu.

## <a name="cwinapploadoemcursor"></a><a name="loadoemcursor"></a>CWinApp::LoadOEMCursor

Ładuje wstępnie zdefiniowany zasób kursora systemu Windows określony przez *nIDCursor*.

```
HCURSOR LoadOEMCursor(UINT nIDCursor) const;
```

### <a name="parameters"></a>Parametry

*nIDCursor*<br/>
OCR_ **OCR_** identyfikator stałej manifestu, który określa wstępnie zdefiniowany kursor systemu Windows. Musisz mieć `#define OEMRESOURCE` `#include \<afxwin.h>` przed, aby uzyskać dostęp do **stałych OCR_** w systemie WINDOWS. H.

### <a name="return-value"></a>Wartość zwracana

Dojście do kursora, jeśli zakończy się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Użyj `LoadOEMCursor` funkcji elementu członkowskiego [lub LoadStandardCursor,](#loadstandardcursor) aby uzyskać dostęp do wstępnie zdefiniowanych kursorów systemu Windows.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#45](../../mfc/reference/codesnippet/cpp/cwinapp-class_12.h)]

[!code-cpp[NVC_MFCWindowing#46](../../mfc/reference/codesnippet/cpp/cwinapp-class_13.cpp)]

## <a name="cwinapploadoemicon"></a><a name="loadoemicon"></a>CWinApp::LoadOEMIcon

Ładuje wstępnie zdefiniowany zasób ikony systemu Windows określony przez *nIDIcon*.

```
HICON LoadOEMIcon(UINT nIDIcon) const;
```

### <a name="parameters"></a>Parametry

*nIDIcon (IDA)*<br/>
OIC_ **OIC_** identyfikator stałej manifestu, który określa wstępnie zdefiniowaną ikonę systemu Windows. Musisz mieć `#define OEMRESOURCE` `#include \<afxwin.h>` przed dostępem do **stałych OIC_** w systemie WINDOWS. H.

### <a name="return-value"></a>Wartość zwracana

Uchwyt do ikony, jeśli się powiedzie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Użyj `LoadOEMIcon` funkcji elementu członkowskiego [LoadStandardIcon,](#loadstandardicon) aby uzyskać dostęp do wstępnie zdefiniowanych ikon systemu Windows.

## <a name="cwinapploadstandardcursor"></a><a name="loadstandardcursor"></a>CWinApp::LoadStandardCursor

Ładuje wstępnie zdefiniowany zasób kursora systemu Windows określony *przez lpszCursorName.*

```
HCURSOR LoadStandardCursor(LPCTSTR lpszCursorName) const;
```

### <a name="parameters"></a>Parametry

*lpszCursorName*<br/>
IDC_ **IDC_** identyfikator stałej manifestu, który określa wstępnie zdefiniowany kursor systemu Windows. Identyfikatory te są zdefiniowane w systemie WINDOWS. H. Na poniższej liście przedstawiono możliwe wstępnie zdefiniowane wartości i znaczenia *dla lpszCursorName*:

- IDC_ARROW Standardowy kursor strzałek

- IDC_IBEAM Standardowy kursor wstawiania tekstu

- IDC_WAIT kursor klepsydry używany podczas wykonywania czasochłonnego zadania przez system Windows

- IDC_CROSS Kursor krzyżowy do wyboru

- strzałka IDC_UPARROW, która wskazuje prosto w górę

- IDC_SIZE przestarzałe i nieobsługiwały; używać IDC_SIZEALL

- IDC_SIZEALL Czteroramienna strzałka. Kursor służy do ponownego rozmiaru okna.

- IDC_ICON Przestarzałe i nieobsługiwały. Użyj IDC_ARROW.

- IDC_SIZENWSE strzałka z dwoma grotami z końcami w lewym górnym i prawym dolnym rogu

- IDC_SIZENESW strzałka z dwoma grotami z końcami w prawym górnym i lewym dolnym rogu

- IDC_SIZEWE Pozioma strzałka z dwoma grotami

- IDC_SIZENS Pionowa strzałka z dwoma grotami

### <a name="return-value"></a>Wartość zwracana

Dojście do kursora, jeśli zakończy się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Użyj `LoadStandardCursor` funkcji elementu członkowskiego [loadoemcursor,](#loadoemcursor) aby uzyskać dostęp do wstępnie zdefiniowanych kursorów systemu Windows.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#47](../../mfc/reference/codesnippet/cpp/cwinapp-class_14.cpp)]

## <a name="cwinapploadstandardicon"></a><a name="loadstandardicon"></a>CWinApp::LoadStandardicon

Ładuje wstępnie zdefiniowany zasób ikony systemu Windows określony *przez lpszIconName.*

```
HICON LoadStandardIcon(LPCTSTR lpszIconName) const;
```

### <a name="parameters"></a>Parametry

*lpszIconName*<br/>
Identyfikator stałej manifestu, który określa wstępnie zdefiniowaną ikonę systemu Windows. Identyfikatory te są zdefiniowane w systemie WINDOWS. H. Aby uzyskać listę możliwych wstępnie zdefiniowanych wartości i ich opisów, zobacz parametr *lpIconName* w [LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Uchwyt do ikony, jeśli się powiedzie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Użyj `LoadStandardIcon` funkcji elementu członkowskiego [LoadOEMIcon,](#loadoemicon) aby uzyskać dostęp do wstępnie zdefiniowanych ikon systemu Windows.

## <a name="cwinapploadstdprofilesettings"></a><a name="loadstdprofilesettings"></a>CWinApp::LoadStdProfileSettings

Wywołanie tej funkcji elementu członkowskiego z wewnątrz [initinstance](#initinstance) funkcji elementu członkowskiego, aby włączyć i załadować listę ostatnio używanych plików (MRU) i stan ostatniego podglądu.

```
void LoadStdProfileSettings(UINT nMaxMRU = _AFX_MRU_COUNT);
```

### <a name="parameters"></a>Parametry

*nMaxMRU*<br/>
Liczba ostatnio używanych plików do śledzenia.

### <a name="remarks"></a>Uwagi

Jeśli *nMaxMRU* wynosi 0, nie zostanie zachowana żadna lista MRU.

## <a name="cwinappm_bhelpmode"></a><a name="m_bhelpmode"></a>CWinApp::m_bHelpMode

PRAWDA, jeśli aplikacja znajduje się w trybie kontekstowym Pomocy (konwencjonalnie wywoływana z SHIFT + F1); w przeciwnym razie FALSE.

```
BOOL m_bHelpMode;
```

### <a name="remarks"></a>Uwagi

W trybie kontekstu Pomocy kursor staje się znakiem zapytania, a użytkownik może przenieść go na ekranie. Sprawdź tę flagę, jeśli chcesz zaimplementować specjalną obsługę w trybie Pomocy. `m_bHelpMode`jest zmienną publiczną typu BOOL.

## <a name="cwinappm_dwrestartmanagersupportflags"></a><a name="m_dwrestartmanagersupportflags"></a>CWinApp::m_dwRestartManagerSupportFlags

Flagi, które określają, jak zachowuje się menedżer ponownego uruchamiania.

```
DWORD m_dwRestartManagerSupportFlags;
```

### <a name="remarks"></a>Uwagi

Aby włączyć menedżera ponownego `m_dwRestartManagerSupportFlags` uruchamiania, ustaw zachowanie, które chcesz. W poniższej tabeli przedstawiono flagi, które są dostępne.

|||
|-|-|
|Flaga|Opis|
|AFX_RESTART_MANAGER_SUPPORT_RESTART|Aplikacja jest rejestrowana przy użyciu [CWinApp::RegisterWithRestartManager](#registerwithrestartmanager). Menedżer ponownego uruchamiania jest odpowiedzialny za ponowne uruchomienie aplikacji, jeśli nieoczekiwanie zakończy działanie.|
|- AFX_RESTART_MANAGER_SUPPORT_RECOVERY|Aplikacja jest zarejestrowana w menedżerze ponownego uruchamiania, a menedżer ponownego uruchamiania wywołuje funkcję wywołania zwrotnego odzyskiwania po ponownym uruchomieniu aplikacji. Domyślną funkcją wywołania zwrotnego odzyskiwania jest [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).|
|- AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART|Automatyczny program "Zapisz" jest włączony, a menedżer ponownego uruchamiania automatycznie włącza otwarte dokumenty po ponownym uruchomieniu aplikacji.|
|- AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL|Automatyczny program "Zapisz" jest włączony, a menedżer ponownego uruchamiania automatycznie automatycznie wysuwa wszystkie otwarte dokumenty w regularnych odstępach czasu. Interwał jest zdefiniowany przez [CWinApp::m_nAutosaveInterval](#m_nautosaveinterval).|
|- AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES|Menedżer ponownego uruchamiania otwiera wcześniej otwarte dokumenty po ponownym uruchomieniu aplikacji z nieoczekiwanego wyjścia. [CDataRecoveryHandler Klasa](../../mfc/reference/cdatarecoveryhandler-class.md) obsługuje przechowywanie listy otwartych dokumentów i przywracanie ich.|
|- AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES|Menedżer ponownego uruchamiania monituje użytkownika o przywrócenie automatycznie zainstalanych plików po ponownym uruchomieniu aplikacji. Klasa `CDataRecoveryHandler` wysyła zapytanie do użytkownika.|
|- AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE|Związek AFX_RESTART_MANAGER_SUPPORT_RESTART, AFX_RESTART_MANAGER_SUPPORT_RECOVER i AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES.|
|- AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS|Związek AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART, AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL i AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|
|- AFX_RESTART_MANAGER_SUPPORT_RESTART_ASPECTS|Związek AFX_RESTART_MANAGER_SUPPORT_RESTART, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES i AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|
|- AFX_RESTART_MANAGER_SUPPORT_RECOVERY_ASPECTS|Związek ofAFX_RESTART_MANAGER_SUPPORT_RECOVERY, AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES i AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|

## <a name="cwinappm_ehelptype"></a><a name="m_ehelptype"></a>CWinApp::m_eHelpType

Typ tego elementu członkowskiego danych jest wyliczonym typem AFX_HELP_TYPE, `CWinApp` który jest zdefiniowany w klasie.

```
AFX_HELP_TYPE m_eHelpType;
```

### <a name="remarks"></a>Uwagi

Wyliczenie AFX_HELP_TYPE jest zdefiniowane w następujący sposób:

```
enum AFX_HELP_TYPE {
    afxWinHelp = 0,
    afxHTMLHelp = 1
    };
```

- Aby ustawić pomoc aplikacji na Pomoc HTML, zadzwoń do `afxHTMLHelp` [SetHelpMode](#sethelpmode) i określ .

- Aby ustawić pomoc aplikacji na WinHelp, `SetHelpMode` `afxWinHelp`zadzwoń i określ .

## <a name="cwinappm_hinstance"></a><a name="m_hinstance"></a>CWinApp::m_hInstance

Odpowiada parametrowi *hInstance* przekazywanym przez system Windows do `WinMain`.

```
HINSTANCE m_hInstance;
```

### <a name="remarks"></a>Uwagi

Element `m_hInstance` członkowski danych jest dojściem do bieżącego wystąpienia aplikacji działającej w systemie Windows. Jest to zwracane przez globalną funkcję [AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle). `m_hInstance`jest zmienną publiczną typu HINSTANCE.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#55](../../mfc/reference/codesnippet/cpp/cwinapp-class_15.cpp)]

## <a name="cwinappm_lpcmdline"></a><a name="m_lpcmdline"></a>CWinApp::m_lpCmdLine

Odpowiada parametrowi *lpCmdLine* przekazywanym przez system Windows do `WinMain`.

```
LPTSTR m_lpCmdLine;
```

### <a name="remarks"></a>Uwagi

Wskazuje ciąg zakończony zerem, który określa wiersz polecenia dla aplikacji. Służy `m_lpCmdLine` do uzyskiwania dostępu do argumentów wiersza polecenia wprowadzonych przez użytkownika podczas uruchamiania aplikacji. `m_lpCmdLine`jest zmienną publiczną typu LPTSTR.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

## <a name="cwinappm_nautosaveinterval"></a><a name="m_nautosaveinterval"></a>CWinApp::m_nAutosaveInterval

Czas w milisekundach między autosaves.

```
int m_nAutosaveInterval;
```

### <a name="remarks"></a>Uwagi

Menedżera ponownego uruchamiania można skonfigurować do automatycznego wstawiania otwartych dokumentów w określonych odstępach czasu. Jeśli aplikacja nie automatycznie zapisze pliki, ten parametr nie ma wpływu.

## <a name="cwinappm_ncmdshow"></a><a name="m_ncmdshow"></a>CWinApp::m_nCmdShow

Odpowiada parametrowi *nCmdShow* przekazywanym przez system Windows do `WinMain`.

```
int m_nCmdShow;
```

### <a name="remarks"></a>Uwagi

Należy przekazać `m_nCmdShow` jako argument podczas wywoływania [CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow) dla głównego okna aplikacji. `m_nCmdShow`jest publiczną zmienną typu **int**.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#56](../../mfc/reference/codesnippet/cpp/cwinapp-class_17.cpp)]

## <a name="cwinappm_pactivewnd"></a><a name="m_pactivewnd"></a>CWinApp::m_pActiveWnd

Ten element członkowski danych służy do przechowywania wskaźnika do głównego okna aplikacji kontenera OLE, w której aktywowano aplikację serwera OLE w miejscu.

### <a name="remarks"></a>Uwagi

Jeśli ten element członkowski danych ma wartość NULL, aplikacja nie jest aktywna w miejscu.

Struktura ustawia tę zmienną elementu członkowskiego, gdy okno ramki jest w miejscu aktywowane przez aplikację kontenera OLE.

## <a name="cwinappm_pdatarecoveryhandler"></a><a name="m_pdatarecoveryhandler"></a>CWinApp::m_pDataRecoveryHandler

Wskaźnik do programu obsługi odzyskiwania danych dla aplikacji.

```
CDataRecoveryHandler* m_pDataRecoveryHandler;
```

### <a name="remarks"></a>Uwagi

Program obsługi odzyskiwania danych aplikacji monitoruje otwarte dokumenty i automatycznie je przesyła. Struktura używa programu obsługi odzyskiwania danych do przywracania automatycznieaved plików, gdy aplikacja jest uruchamiana ponownie po nieoczekiwanym zamknięciu. Aby uzyskać więcej informacji, zobacz [CDataRecoveryHandler Class](../../mfc/reference/cdatarecoveryhandler-class.md).

## <a name="cwinappm_pszappname"></a><a name="m_pszappname"></a>CWinApp::m_pszAppName

Określa nazwę aplikacji.

```
LPCTSTR m_pszAppName;
```

### <a name="remarks"></a>Uwagi

Nazwa aplikacji może pochodzić z parametru przekazanego do konstruktora [CWinApp](#cwinapp) lub, jeśli nie określono, do ciągu zasobu o identyfikatorze AFX_IDS_APP_TITLE. Jeśli nazwa aplikacji nie zostanie znaleziona w zasobie, pochodzi ona od programu . nazwa pliku EXE.

Zwrócona przez globalną funkcję [AfxGetAppName](application-information-and-management.md#afxgetappname). `m_pszAppName`jest zmienną publiczną typu **const char**<strong>\*</strong>.

> [!NOTE]
> Jeśli do niego `m_pszAppName`przypisano wartość, musi ona być dynamicznie alokowana na stercie. Destruktor `CWinApp` wywołuje **za darmo**( ) za pomocą tego wskaźnika. Wiele osób chce `_tcsdup`użyć () funkcji biblioteki wyładunkowej do przydzielania. Ponadto zwolnić pamięć skojarzoną z bieżącym wskaźnikiem przed przypisaniem nowej wartości. Przykład:

[!code-cpp[NVC_MFCWindowing#57](../../mfc/reference/codesnippet/cpp/cwinapp-class_18.cpp)]

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#65](../../mfc/reference/codesnippet/cpp/cwinapp-class_19.cpp)]

## <a name="cwinappm_pszexename"></a><a name="m_pszexename"></a>CWinApp::m_pszExeName

Zawiera nazwę pliku wykonywalnego aplikacji bez rozszerzenia.

```
LPCTSTR m_pszExeName;
```

### <a name="remarks"></a>Uwagi

W odróżnieniu od [m_pszAppName](#m_pszappname)nazwa ta nie może zawierać pustych miejsc. `m_pszExeName`jest zmienną publiczną typu **const char**<strong>\*</strong>.

> [!NOTE]
> Jeśli do niego `m_pszExeName`przypisano wartość, musi ona być dynamicznie alokowana na stercie. Destruktor `CWinApp` wywołuje **za darmo**( ) za pomocą tego wskaźnika. Wiele osób chce `_tcsdup`użyć () funkcji biblioteki wyładunkowej do przydzielania. Ponadto zwolnić pamięć skojarzoną z bieżącym wskaźnikiem przed przypisaniem nowej wartości. Przykład:

[!code-cpp[NVC_MFCWindowing#58](../../mfc/reference/codesnippet/cpp/cwinapp-class_20.cpp)]

## <a name="cwinappm_pszhelpfilepath"></a><a name="m_pszhelpfilepath"></a>CWinApp::m_pszHelpFilePath

Zawiera ścieżkę do pliku Pomocy aplikacji.

```
LPCTSTR m_pszHelpFilePath;
```

### <a name="remarks"></a>Uwagi

Domyślnie struktura inicjuje `m_pszHelpFilePath` nazwę aplikacji z ". HLP" . Aby zmienić nazwę pliku pomocy, ustaw, `m_pszHelpFilePath` aby wskazać ciąg zawierający pełną nazwę żądanego pliku pomocy. Dogodnym miejscem do tego jest funkcja [InitInstance](#initinstance) aplikacji. `m_pszHelpFilePath`jest zmienną publiczną typu **const char**<strong>\*</strong>.

> [!NOTE]
> Jeśli do niego `m_pszHelpFilePath`przypisano wartość, musi ona być dynamicznie alokowana na stercie. Destruktor `CWinApp` wywołuje **za darmo**( ) za pomocą tego wskaźnika. Wiele osób chce `_tcsdup`użyć () funkcji biblioteki wyładunkowej do przydzielania. Ponadto zwolnić pamięć skojarzoną z bieżącym wskaźnikiem przed przypisaniem nowej wartości. Przykład:

[!code-cpp[NVC_MFCWindowing#59](../../mfc/reference/codesnippet/cpp/cwinapp-class_21.cpp)]

## <a name="cwinappm_pszprofilename"></a><a name="m_pszprofilename"></a>CWinApp::m_pszProfileName

Zawiera nazwę aplikacji . ini.

```
LPCTSTR m_pszProfileName;
```

### <a name="remarks"></a>Uwagi

`m_pszProfileName`jest zmienną publiczną typu **const char**<strong>\*</strong>.

> [!NOTE]
> Jeśli do niego `m_pszProfileName`przypisano wartość, musi ona być dynamicznie alokowana na stercie. Destruktor `CWinApp` wywołuje **za darmo**( ) za pomocą tego wskaźnika. Wiele osób chce `_tcsdup`użyć () funkcji biblioteki wyładunkowej do przydzielania. Ponadto zwolnić pamięć skojarzoną z bieżącym wskaźnikiem przed przypisaniem nowej wartości. Przykład:

[!code-cpp[NVC_MFCWindowing#60](../../mfc/reference/codesnippet/cpp/cwinapp-class_22.cpp)]

## <a name="cwinappm_pszregistrykey"></a><a name="m_pszregistrykey"></a>CWinApp::m_pszRegistryKey

Służy do określania, gdzie w rejestrze lub pliku INI są przechowywane ustawienia profilu aplikacji.

```
LPCTSTR m_pszRegistryKey;
```

### <a name="remarks"></a>Uwagi

Zwykle ten element członkowski danych jest traktowany jako tylko do odczytu.

- Wartość jest przechowywana w kluczu rejestru. Nazwa ustawienia profilu aplikacji jest dołączana do następującego klucza rejestru: HKEY_CURRENT_USER/Software/LocalAppWizard-Generated/.

Jeśli do niego `m_pszRegistryKey`przypisano wartość, musi ona być dynamicznie alokowana na stercie. Destruktor `CWinApp` wywołuje **za darmo**( ) za pomocą tego wskaźnika. Wiele osób chce `_tcsdup`użyć () funkcji biblioteki wyładunkowej do przydzielania. Ponadto zwolnić pamięć skojarzoną z bieżącym wskaźnikiem przed przypisaniem nowej wartości. Przykład:

[!code-cpp[NVC_MFCWindowing#61](../../mfc/reference/codesnippet/cpp/cwinapp-class_23.cpp)]

## <a name="cwinappm_pszappid"></a><a name="m_pszappid"></a>CWinApp::m_pszAppID

Identyfikator modelu użytkownika aplikacji.

```
LPCTSTR m_pszAppID;
```

### <a name="remarks"></a>Uwagi

## <a name="cwinapponcontexthelp"></a><a name="oncontexthelp"></a>CWinApp::OnContextHelp

Obsługuje pomoc SHIFT+F1 w aplikacji.

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>Uwagi

Należy dodać `ON_COMMAND( ID_CONTEXT_HELP, OnContextHelp )` instrukcję `CWinApp` do mapy komunikatów klasy, a także dodać wpis tabeli akceleratora, zazwyczaj SHIFT + F1, aby włączyć tę funkcję elementu członkowskiego.

`OnContextHelp`przełącza aplikację w tryb Pomocy. Kursor zmienia się w strzałkę i znak zapytania, a użytkownik może następnie przesunąć wskaźnik myszy i nacisnąć lewy przycisk myszy, aby zaznaczyć okno dialogowe, okno, menu lub przycisk polecenia. Ta funkcja elementu członkowskiego pobiera kontekst Pomocy obiektu pod kursorem i wywołuje funkcję Systemu Windows WinHelp z tym kontekstem Pomocy.

## <a name="cwinapponddecommand"></a><a name="onddecommand"></a>CWinApp::OnDDECommand

Wywoływane przez strukturę, gdy okno ramki głównej odbiera komunikat wykonania DDE.

```
virtual BOOL OnDDECommand(LPTSTR lpszCommand);
```

### <a name="parameters"></a>Parametry

*lpszCommand ( lpszCommand )*<br/>
Wskazuje ciąg polecenia DDE odebrany przez aplikację.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli polecenie jest obsługiwane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja sprawdza, czy polecenie jest żądaniem otwarcia dokumentu, a jeśli tak, otwiera określony dokument. Menedżer plików systemu Windows zwykle wysyła takie ciągi poleceń DDE, gdy użytkownik kliknie dwukrotnie plik danych. Zastądź tę funkcję do obsługi innych poleceń wykonywania DDE, takich jak polecenie do drukowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#48](../../mfc/reference/codesnippet/cpp/cwinapp-class_24.cpp)]

## <a name="cwinapponfilenew"></a><a name="onfilenew"></a>CWinApp::OnFileNowy

Implementuje polecenie ID_FILE_NEW.

```
afx_msg void OnFileNew();
```

### <a name="remarks"></a>Uwagi

Aby włączyć `ON_COMMAND( ID_FILE_NEW, OnFileNew )` tę funkcję `CWinApp` elementu członkowskiego, należy dodać instrukcję do mapy komunikatów klasy. Jeśli ta funkcja jest włączona, obsługuje wykonywanie polecenia Plik nowy.

Zobacz [uwaga techniczna 22,](../../mfc/tn022-standard-commands-implementation.md) aby uzyskać informacje na temat zachowania domyślnego i wskazówki dotyczące zastępowania tej funkcji elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

## <a name="cwinapponfileopen"></a><a name="onfileopen"></a>CWinApp::OnFileOpen

Implementuje polecenie ID_FILE_OPEN.

```
afx_msg void OnFileOpen();
```

### <a name="remarks"></a>Uwagi

Aby włączyć `ON_COMMAND( ID_FILE_OPEN, OnFileOpen )` tę funkcję `CWinApp` elementu członkowskiego, należy dodać instrukcję do mapy komunikatów klasy. Jeśli ta funkcja jest włączona, obsługuje wykonywanie polecenia Otwieranie pliku.

Aby uzyskać informacje na temat zachowania domyślnego i wskazówek dotyczących zastępowania tej funkcji elementu członkowskiego, zobacz [Uwaga techniczna 22](../../mfc/tn022-standard-commands-implementation.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

## <a name="cwinapponfileprintsetup"></a><a name="onfileprintsetup"></a>CWinApp::OnFilePrintSetup

Implementuje polecenie ID_FILE_PRINT_SETUP.

```
afx_msg void OnFilePrintSetup();
```

### <a name="remarks"></a>Uwagi

Aby włączyć `ON_COMMAND( ID_FILE_PRINT_SETUP, OnFilePrintSetup )` tę funkcję `CWinApp` elementu członkowskiego, należy dodać instrukcję do mapy komunikatów klasy. Jeśli ta funkcja jest włączona, obsługuje wykonywanie polecenia Drukowanie plików.

Aby uzyskać informacje na temat zachowania domyślnego i wskazówek dotyczących zastępowania tej funkcji elementu członkowskiego, zobacz [Uwaga techniczna 22](../../mfc/tn022-standard-commands-implementation.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

## <a name="cwinapponhelp"></a><a name="onhelp"></a>CWinApp::OnHelp

Obsługuje Pomoc F1 w aplikacji (przy użyciu bieżącego kontekstu).

```
afx_msg void OnHelp();
```

### <a name="remarks"></a>Uwagi

Zazwyczaj można również dodać wpis klucza akceleratora dla klucza F1. Włączenie klucza F1 jest tylko konwencją, a nie wymaganiem.

Aby włączyć `ON_COMMAND( ID_HELP, OnHelp )` tę funkcję `CWinApp` elementu członkowskiego, należy dodać instrukcję do mapy komunikatów klasy. Jeśli jest włączona, wywoływana przez platformę, gdy użytkownik naciśnie klawisz F1.

Domyślna implementacja tej funkcji obsługi wiadomości określa kontekst Pomocy, który odpowiada bieżącemu okno, okno dialogowe lub element menu, a następnie wywołuje WINHELP. Exe. Jeśli żaden kontekst nie jest obecnie dostępny, funkcja używa kontekstu domyślnego.

Zastąp tę funkcję elementu członkowskiego, aby ustawić kontekst Pomocy na coś innego niż okno, okno dialogowe, element menu lub przycisk paska narzędzi, który obecnie ma fokus. Zadzwoń `WinHelp` z żądanym identyfikatorem kontekstu Pomocy.

## <a name="cwinapponhelpfinder"></a><a name="onhelpfinder"></a>CWinApp::OnHelpFinder

Obsługuje polecenia ID_HELP_FINDER i ID_DEFAULT_HELP.

```
afx_msg void OnHelpFinder();
```

### <a name="remarks"></a>Uwagi

Aby włączyć `ON_COMMAND( ID_HELP_FINDER, OnHelpFinder )` tę funkcję `CWinApp` elementu członkowskiego, należy dodać instrukcję do mapy komunikatów klasy. Jeśli ta opcja jest włączona, struktura wywołuje tę funkcję obsługi wiadomości, gdy użytkownik `WinHelp` aplikacji wybierze polecenie Help Finder do wywołania przy standardowym **temacie HELP_FINDER.**

## <a name="cwinapponhelpindex"></a><a name="onhelpindex"></a>CWinApp::OnHelpIndex

Obsługuje polecenie ID_HELP_INDEX i udostępnia domyślny temat Pomocy.

```
afx_msg void OnHelpIndex();
```

### <a name="remarks"></a>Uwagi

Aby włączyć `ON_COMMAND( ID_HELP_INDEX, OnHelpIndex )` tę funkcję `CWinApp` elementu członkowskiego, należy dodać instrukcję do mapy komunikatów klasy. Jeśli ta opcja jest włączona, struktura wywołuje tę funkcję obsługi wiadomości, gdy `WinHelp` użytkownik aplikacji wybierze polecenie Indeks pomocy do wywołania przy zastosowaniu standardowego **tematu HELP_INDEX.**

## <a name="cwinapponhelpusing"></a><a name="onhelpusing"></a>CWinApp::OnHelpUżywanie

Obsługuje polecenie ID_HELP_USING.

```
afx_msg void OnHelpUsing();
```

### <a name="remarks"></a>Uwagi

Aby włączyć `ON_COMMAND( ID_HELP_USING, OnHelpUsing )` tę funkcję `CWinApp` elementu członkowskiego, należy dodać instrukcję do mapy komunikatów klasy. Struktura wywołuje tę funkcję obsługi wiadomości, gdy użytkownik aplikacji wybiera help using `WinHelp` polecenia do wywołania aplikacji ze standardową **HELP_HELPONHELP** tematu.

## <a name="cwinapponidle"></a><a name="onidle"></a>CWinApp::OnIdle

Zastąpokaj tę funkcję elementu członkowskiego, aby wykonać przetwarzanie w czasie bezczynnym.

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>Parametry

*lLicza*<br/>
Licznik zwiększany za każdym `OnIdle` razem jest wywoływany, gdy kolejka komunikatów aplikacji jest pusta. Ta liczba jest resetowana do 0 za każdym razem, gdy nowa wiadomość jest przetwarzana. Za pomocą parametru *lCount* można określić względny czas bezczynności aplikacji bez przetwarzania wiadomości.

### <a name="return-value"></a>Wartość zwracana

Nonzero, aby otrzymać więcej czasu bezczynnego przetwarzania; 0, jeśli nie jest potrzebny czas bezczynny.

### <a name="remarks"></a>Uwagi

`OnIdle`jest wywoływana w domyślnej pętli komunikatów, gdy kolejka komunikatów aplikacji jest pusta. Użyj zastąpienia, aby wywołać własne zadania bezczynnego obsługi tła.

`OnIdle`powinien zwrócić 0, aby wskazać, że nie jest wymagany czas bezczynnego przetwarzania. Parametr *lCount* jest zwiększany za `OnIdle` każdym razem, gdy kolejka komunikatów jest pusta i resetuje się do 0 za każdym razem, gdy nowa wiadomość jest przetwarzana. Na podstawie tej liczby można wywołać różne procedury bezczynne.

Poniżej podsumowano przetwarzanie pętli bezczynnej:

1. Jeśli pętla komunikatów w bibliotece klas Programu Microsoft Foundation sprawdza `OnIdle` kolejkę komunikatów i nie znajdzie żadnych oczekujących wiadomości, wywołuje obiekt aplikacji i dostarcza 0 jako argument *lCount.*

2. `OnIdle`wykonuje pewne przetwarzanie i zwraca wartość niezerową, aby wskazać, że należy ją ponownie wywołać w celu dalszego przetwarzania.

3. Pętla komunikatów ponownie sprawdza kolejkę komunikatów. Jeśli żadne wiadomości nie `OnIdle` są oczekujące, wywołuje ponownie, zwiększanie *lCount* argument.

4. Ostatecznie `OnIdle` kończy przetwarzanie wszystkich zadań bezczynności i zwraca 0. Informuje to pętli komunikatów, aby zatrzymać wywołanie, `OnIdle` aż następna wiadomość zostanie odebrana z kolejki wiadomości, w którym to momencie cykl bezczynny zostanie ponownie uruchomiony z argumentem ustawionym na 0.

Nie należy wykonywać `OnIdle` długie zadania podczas, ponieważ `OnIdle` aplikacja nie może przetwarzać danych wejściowych użytkownika, dopóki nie zwraca.

> [!NOTE]
> Domyślna implementacja `OnIdle` aktualizacje polecenia obiektów interfejsu użytkownika, takich jak elementy menu i przyciski paska narzędzi, i wykonuje oczyszczanie wewnętrznej struktury danych. W związku z tym `OnIdle`w przypadku `CWinApp::OnIdle` zastąpienia `lCount` , należy wywołać z w wersji zastąpione. Najpierw wywołać wszystkie klasy podstawowej bezczynnego przetwarzania (to znaczy, dopóki klasa `OnIdle` podstawowa zwraca 0). Jeśli musisz wykonać pracę przed zakończeniem przetwarzania klasy podstawowej, przejrzyj implementację klasy podstawowej, aby wybrać właściwą *liczbę lCount,* podczas której ma być wykonywanej pracy.

Jeśli nie chcesz `OnIdle` być wywoływany za każdym razem, gdy wiadomość jest pobierana z kolejki wiadomości, możesz zastąpić [CWinThreadIsIdleMessage](../../mfc/reference/cwinthread-class.md#isidlemessage). Jeśli aplikacja ustawiła bardzo krótki czasomierz lub jeśli system wysyła komunikat `OnIdle` WM_SYSTIMER, zostanie wywołana wielokrotnie i obniży wydajność.

### <a name="example"></a>Przykład

Poniższe dwa przykłady pokazują, jak używać `OnIdle`. Pierwszy przykład przetwarza dwa bezczynne zadania przy użyciu *lCount* argument do priorytetów zadań. Pierwsze zadanie ma wysoki priorytet i należy to zrobić, gdy tylko jest to możliwe. Drugie zadanie jest mniej ważne i powinno być wykonywane tylko wtedy, gdy istnieje długa pauza w danych wejściowych użytkownika. Zanotuj wywołanie wersji `OnIdle`klasy podstawowej programu . Drugi przykład zarządza grupą bezczynnych zadań z różnymi priorytetami.

[!code-cpp[NVC_MFCWindowing#51](../../mfc/reference/codesnippet/cpp/cwinapp-class_27.cpp)]

## <a name="cwinappopendocumentfile"></a><a name="opendocumentfile"></a>CWinApp::OpenDocumentFile

Struktura wywołuje tę metodę, aby otworzyć plik o nazwie [CDocument](../../mfc/reference/cdocument-class.md) dla aplikacji.

```
virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszFileName
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
[w] Nazwa pliku, który ma zostać otwarty.

*bAddToMRU*<br/>
[w] TRUE wskazuje, że dokument jest jednym z najnowszych plików; FALSE wskazuje, że dokument nie jest jednym z najnowszych plików.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CDocument` if successful; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Jeśli dokument o tej nazwie jest już otwarty, pierwsze okno ramki zawierające ten dokument uzyska fokus. Jeśli aplikacja obsługuje wiele szablonów dokumentów, struktura używa rozszerzenia nazwy pliku, aby znaleźć odpowiedni szablon dokumentu, aby spróbować załadować dokument. Jeśli powiedzie się, szablon dokumentu tworzy okno ramki i widok dokumentu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

## <a name="cwinappparsecommandline"></a><a name="parsecommandline"></a>CWinApp::ParseCommandLine

Wywołanie tej funkcji elementu członkowskiego, aby przeanalizować wiersz polecenia i wysłać parametry, jeden po drugim, do [CCommandLineInfo::ParseParam](../../mfc/reference/ccommandlineinfo-class.md#parseparam).

```
void ParseCommandLine(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>Parametry

*rCmdInfo*<br/>
Odwołanie do [obiektu CCommandLineInfo.](../../mfc/reference/ccommandlineinfo-class.md)

### <a name="remarks"></a>Uwagi

Po uruchomieniu nowego projektu MFC za pomocą Kreatora aplikacji Kreator `CCommandLineInfo`aplikacji utworzy `ProcessShellCommand` `ParseCommandLine` lokalne wystąpienie , a następnie wywoła i w funkcji elementu członkowskiego [InitInstance.](#initinstance) Wiersz polecenia podąża trasą opisaną poniżej:

1. Po utworzeniu `InitInstance` `CCommandLineInfo` w , obiekt `ParseCommandLine`jest przekazywany do .

2. `ParseCommandLine`następnie `CCommandLineInfo::ParseParam` wywołuje wielokrotnie, raz dla każdego parametru.

3. `ParseParam`wypełnia `CCommandLineInfo` obiekt, który jest następnie przekazywany do [ProcessShellCommand](#processshellcommand).

4. `ProcessShellCommand`obsługuje argumenty wiersza polecenia i flagi.

Należy pamiętać, `ParseCommandLine` że można wywołać bezpośrednio w razie potrzeby.

Aby uzyskać opis flag wiersza polecenia, zobacz [CCommandLineInfo::m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand).

## <a name="cwinapppretranslatemessage"></a><a name="pretranslatemessage"></a>CWinApp::PretranslateMessage

Zastąpuj tę funkcję, aby filtrować komunikaty okna, zanim zostaną wysłane do funkcji systemu Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Domyślna implementacja wykonuje translację klucza akceleratora, więc należy wywołać funkcję `CWinApp::PreTranslateMessage` elementu członkowskiego w zastąpionej wersji.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Wskaźnik do struktury [MSG,](/windows/win32/api/winuser/ns-winuser-msg) który zawiera komunikat do przetworzenia.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wiadomość została `PreTranslateMessage` w pełni przetworzona i nie powinny być przetwarzane dalej. Zero, jeśli wiadomość powinna być przetwarzana w normalny sposób.

## <a name="cwinappprocessmessagefilter"></a><a name="processmessagefilter"></a>CWinApp::Pprotwofiltr

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
Wskaźnik do tructure [MSG](/windows/win32/api/winuser/ns-winuser-msg)systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wiadomość jest przetwarzana; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Funkcja hak przetwarza zdarzenia, zanim zostaną wysłane do normalnego przetwarzania wiadomości aplikacji.

Jeśli zastąpisz tę zaawansowaną funkcję, należy wywołać wersję klasy podstawowej, aby zachować przetwarzanie haków struktury.

## <a name="cwinappprocessshellcommand"></a><a name="processshellcommand"></a>CWinApp::ProcessShellCommand

Ta funkcja elementu członkowskiego jest wywoływana przez [InitInstance,](#initinstance) aby zaakceptować parametry przekazywane z `CCommandLineInfo` obiektu zidentyfikowanego przez *rCmdInfo*i wykonać wskazaną akcję.

```
BOOL ProcessShellCommand(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>Parametry

*rCmdInfo*<br/>
Odwołanie do [obiektu CCommandLineInfo.](../../mfc/reference/ccommandlineinfo-class.md)

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli polecenie powłoki jest przetwarzane pomyślnie. Jeśli 0, zwraca wartość FAŁSZ z [InitInstance](#initinstance).

### <a name="remarks"></a>Uwagi

Po uruchomieniu nowego projektu MFC za pomocą Kreatora aplikacji Kreator `CCommandLineInfo`aplikacji utworzy `ProcessShellCommand` lokalne wystąpienie , a `InitInstance` następnie wywoła i [ParseCommandLine](#parsecommandline) w funkcji elementu członkowskiego. Wiersz polecenia podąża trasą opisaną poniżej:

1. Po utworzeniu `InitInstance` `CCommandLineInfo` w , obiekt `ParseCommandLine`jest przekazywany do .

2. `ParseCommandLine`następnie wywołuje [CCommandLineInfo::ParseParam](../../mfc/reference/ccommandlineinfo-class.md#parseparam) wielokrotnie, raz dla każdego parametru.

3. `ParseParam`wypełnia `CCommandLineInfo` obiekt, który jest następnie `ProcessShellCommand`przekazywany do .

4. `ProcessShellCommand`obsługuje argumenty wiersza polecenia i flagi.

Elementy członkowskie danych `CCommandLineInfo` obiektu, identyfikowane przez [CCommandLineInfo::m_nShellCommand,](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand)są następujące wyliczane typu, `CCommandLineInfo` który jest zdefiniowany w klasie.

```
enum {
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE
    };
```

Aby uzyskać krótki opis każdej z `CCommandLineInfo::m_nShellCommand`tych wartości, zobacz .

## <a name="cwinappprocesswndprocexception"></a><a name="processwndprocexception"></a>CWinApp::ProcessWndProcException

Struktura wywołuje tę funkcję elementu członkowskiego, gdy program obsługi nie przechwytuje wyjątek zgłoszony w jednej z aplikacji wiadomości lub obsługi poleceń.

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*E*<br/>
Wskaźnik do nieprzechowywać wyjątku.

*pMsg*<br/>
Tructure [MSG,](/windows/win32/api/winuser/ns-winuser-msg)który zawiera informacje o komunikacie systemu Windows, który spowodował, że struktura zgłosić wyjątek.

### <a name="return-value"></a>Wartość zwracana

Wartość, która powinna zostać zwrócona do systemu Windows. Zwykle jest to 0L dla wiadomości systemu Windows, 1L (TRUE) dla komunikatów poleceń.

### <a name="remarks"></a>Uwagi

Nie należy wywoływać tej funkcji elementu członkowskiego bezpośrednio.

Domyślna implementacja tej funkcji elementu członkowskiego tworzy okno komunikatu. Jeśli nieprzechowycony wyjątek pochodzi z menu, paska narzędzi lub polecenia akceleratora, w oknie komunikatu jest wyświetlany komunikat "Polecenie nie powiodło się"; w przeciwnym razie wyświetla komunikat "Wewnętrzny błąd aplikacji".

Zastąpojąć tę funkcję elementu członkowskiego, aby zapewnić globalną obsługę wyjątków. Wywołaj podstawową funkcjonalność tylko wtedy, gdy chcesz, aby okno komunikatu było wyświetlane.

## <a name="cwinappregister"></a><a name="register"></a>CWinApp::Zarejestruj się

Wykonuje wszystkie zadania rejestracji, `RegisterShellFileTypes`które nie są obsługiwane przez plik .

```
virtual BOOL Register();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero na sukces; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja po prostu zwraca wartość TRUE. Zastąd w tej funkcji należy wykonać wszystkie kroki rejestracji dostosowane.

## <a name="cwinappregistershellfiletypes"></a><a name="registershellfiletypes"></a>CWinApp::RegisterShellFileTypes

Wywołanie tej funkcji elementu członkowskiego, aby zarejestrować wszystkie typy dokumentów aplikacji w Menedżerze plików systemu Windows.

```
void RegisterShellFileTypes(BOOL bCompat = FALSE);
```

### <a name="parameters"></a>Parametry

*bKomponowanie*<br/>
[w] True dodaje wpisy rejestracji dla poleceń powłoki Drukuj i Drukuj do, umożliwiając użytkownikowi drukowanie plików bezpośrednio z powłoki lub przeciągając plik do obiektu drukarki. Dodaje również klucz DefaultIcon. Domyślnie ten parametr jest FALSE dla zgodności z powrotem.

### <a name="remarks"></a>Uwagi

Dzięki temu użytkownik może otworzyć plik danych utworzony przez aplikację, klikając go dwukrotnie z poziomu Menedżera plików. Wywołanie `RegisterShellFileTypes` po wywołaniu [AddDocTemplate](#adddoctemplate) dla każdego z szablonów dokumentów w aplikacji. Wywołanie [enableshellopen](#enableshellopen) funkcji elementu `RegisterShellFileTypes`członkowskiego podczas wywoływania .

`RegisterShellFileTypes`iteruje za pośrednictwem listy obiektów [CDocTemplate,](../../mfc/reference/cdoctemplate-class.md) które aplikacja przechowuje i dla każdego szablonu dokumentu dodaje wpisy do bazy danych rejestracji, która jest obsługiwana przez system Windows dla skojarzeń plików. Menedżer plików używa tych wpisów do otwierania pliku danych, gdy użytkownik kliknie go dwukrotnie. Eliminuje to konieczność wysyłki . reg z aplikacją.

> [!NOTE]
> `RegisterShellFileTypes`działa tylko wtedy, gdy użytkownik uruchamia program z uprawnieniami administratora. Jeśli program nie ma praw administratora, nie może zmienić kluczy rejestru.

Jeśli baza danych rejestracji kojarzy już dane rozszerzenie nazwy pliku z innym typem pliku, nie jest tworzone żadne nowe skojarzenie. Zobacz `CDocTemplate` klasę dla formatu ciągów niezbędnych do zarejestrowania tych informacji.

## <a name="cwinappregisterwithrestartmanager"></a><a name="registerwithrestartmanager"></a>CWinApp::RegisterWithRestartManager

Rejestruje aplikację za pomocą menedżera ponownego uruchamiania.

```
virtual HRESULT RegisterWithRestartManager(
    BOOL bRegisterRecoveryCallback,
    const CString& strRestartIdentifier);

virtual HRESULT RegisterWithRestartManager(
    LPCWSTR pwzCommandLineArgs,
    DWORD dwRestartFlags,
    APPLICATION_RECOVERY_CALLBACK pRecoveryCallback,
    LPVOID lpvParam,
    DWORD dwPingInterval,
    DWORD dwCallbackFlags);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*bRegisterRecoveryCallback*|[w] PRAWDA wskazuje, że to wystąpienie aplikacji używa funkcji wywołania zwrotnego odzyskiwania; FALSE oznacza, że nie. Struktura wywołuje funkcję wywołania zwrotnego odzyskiwania, gdy aplikacja kończy nieoczekiwane działanie. Aby uzyskać więcej informacji, zobacz [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).|
|*strRestartIdentifier (identyfikowacz)*|[w] Unikatowy ciąg identyfikujący to wystąpienie menedżera ponownego uruchamiania. Identyfikator menedżera ponownego uruchamiania jest unikatowy dla każdego wystąpienia aplikacji.|
|*pwzCommandLineArgs*|[w] Ciąg zawierający dodatkowe argumenty z wiersza polecenia.|
|*dwRestartPlags*|[w] Opcjonalne flagi menedżera ponownego uruchamiania. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.|
|*pRecoveryCallback (Powrót do)*|[w] Funkcja wywołania zwrotnego odzyskiwania. Ta funkcja musi wziąć parametr LPVOID jako dane wejściowe i zwrócić DWORD. Domyślną funkcją wywołania zwrotnego odzyskiwania jest `CWinApp::ApplicationRecoveryCallback`.|
|*lpvParam*|[w] Parametr wejściowy dla funkcji wywołania zwrotnego odzyskiwania. Aby uzyskać więcej informacji, zobacz [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).|
|*dwPingInterval (wersywanie)*|[w] Czas oczekiwania menedżera ponownego uruchamiania na powrót funkcji wywołania zwrotnego odzyskiwania. Ten parametr jest w milisekundach.|
|*dwCallbackSlags*|[w] Flagi przekazywane do funkcji wywołania zwrotnego odzyskiwania. Zarezerwowane do użytku w przyszłości.|

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie kod błędu.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja używa domyślnej implementacji MFC do automatycznego ratowania plików, należy użyć prostej wersji programu `RegisterWithRestartManager`. Użyj złożonej `RegisterWithRestartManager` wersji, jeśli chcesz dostosować zachowanie autosave aplikacji.

Jeśli wywołasz tę metodę z pustym ciągiem `RegisterWithRestartManager` dla *strRestartIdentifier*, tworzy unikatowy ciąg identyfikatora dla tego wystąpienia menedżera ponownego uruchamiania.

Gdy aplikacja kończy się nieoczekiwanie, menedżer ponownego uruchamiania uruchamia ponownie aplikację z wiersza polecenia i udostępnia unikatowy identyfikator ponownego uruchomienia jako opcjonalny argument. W tym scenariuszu `RegisterWithRestartManager` ramach wywołuje dwa razy. Pierwsze wywołanie pochodzi z [CWinApp::InitInstance](#initinstance) z pustym ciągiem dla identyfikatora ciągu. Następnie metoda [CWinApp::PprorocessShellCommand](#processshellcommand) wywołuje `RegisterWithRestartManager` z unikatowym identyfikatorem ponownego uruchomienia.

Po zarejestrowaniu aplikacji w menedżerze ponownego uruchamiania menedżer ponownego uruchamiania monitoruje aplikację. Jeśli aplikacja zakończy się nieoczekiwanie, menedżer ponownego uruchamiania wywołuje funkcję wywołania zwrotnego odzyskiwania podczas procesu zamykania. Menedżer ponownego uruchamiania czeka *dwPingInterval* na odpowiedź z funkcji wywołania zwrotnego odzyskiwania. Jeśli funkcja wywołania zwrotnego odzyskiwania nie odpowiada w tym czasie, aplikacja kończy pracę bez wykonywania funkcji wywołania zwrotnego odzyskiwania.

Domyślnie dwRestartFlags nie są obsługiwane, ale są przewidziane do wykorzystania w przyszłości. Możliwe wartości dla *dwRestartFlags* są następujące:

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

## <a name="cwinappreopenpreviousfilesatrestart"></a><a name="reopenpreviousfilesatrestart"></a>CWinApp::ReopenPreviousFilesAtRestart

Określa, czy menedżer ponownego uruchamiania ponownie otwiera pliki, które były otwarte po nieoczekiwanym zamknięciu aplikacji.

```
virtual BOOL ReopenPreviousFilesAtRestart() const;
```

### <a name="return-value"></a>Wartość zwracana

TRUE wskazuje, że menedżer ponownego uruchamiania ponownie otwiera wcześniej otwarte pliki; FALSE wskazuje, że menedżer ponownego uruchamiania nie.

## <a name="cwinapprestartinstance"></a><a name="restartinstance"></a>CWinApp::Ponowne instance

Obsługuje ponowne uruchomienie aplikacji zainicjowane przez menedżera ponownego uruchamiania.

```
virtual BOOL CWinApp::RestartInstance();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli program obsługi odzyskiwania danych otwiera wcześniej otwarte dokumenty; FAŁSZ, jeśli program obsługi odzyskiwania danych ma błąd lub jeśli nie ma wcześniej otwartych dokumentów.

### <a name="remarks"></a>Uwagi

Gdy menedżer ponownego uruchamiania uruchamia ponownie aplikację, struktura wywołuje tę metodę. Ta metoda pobiera program obsługi odzyskiwania danych i przywraca automatycznieaved plików. Ta metoda wywołuje [CDataRecoveryHandler::RestoreAutosavedDocuments,](../../mfc/reference/cdatarecoveryhandler-class.md#restoreautosaveddocuments) aby ustalić, czy użytkownik chce przywrócić automatycznie zapisywane pliki.

Ta metoda zwraca wartość FAŁSZ, jeśli [CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md) określa, że nie było żadnych otwartych dokumentów. Jeśli nie było otwartych dokumentów, wniosek rozpoczyna się zwykle.

## <a name="cwinapprestoreautosavedfilesatrestart"></a><a name="restoreautosavedfilesatrestart"></a>CWinApp::RestoreAutosavedFilesAtRestart

Określa, czy menedżer ponownego uruchamiania przywraca automatycznie odpisane pliki po ponownym uruchomieniu aplikacji.

```
virtual BOOL RestoreAutosavedFilesAtRestart() const;
```

### <a name="return-value"></a>Wartość zwracana

FUNKCJA TRUE wskazuje, że menedżer ponownego uruchamiania przywraca automatycznie uratowane pliki; FALSE wskazuje, że menedżer ponownego uruchamiania nie.

## <a name="cwinapprun"></a><a name="run"></a>CWinApp::Uruchom

Udostępnia domyślną pętlę wiadomości.

```
virtual int Run();
```

### <a name="return-value"></a>Wartość zwracana

Wartość **int** zwracana `WinMain`przez plik .

### <a name="remarks"></a>Uwagi

`Run`pobiera i wysyła wiadomości systemu Windows, dopóki aplikacja nie otrzyma WM_QUIT wiadomości. Jeśli kolejka komunikatów aplikacji obecnie nie `Run` zawiera żadnych komunikatów, wywołuje [OnIdle](#onidle) do wykonywania przetwarzania w czasie bezczynnym. Przychodzące wiadomości przejść do funkcji elementu członkowskiego [PretranslateMessage](#pretranslatemessage) `TranslateMessage` do specjalnego przetwarzania, a następnie do funkcji systemu Windows do standardowego tłumaczenia klawiatury; na koniec `DispatchMessage` wywoływana jest funkcja systemu Windows.

`Run`rzadko jest zastępowane, ale można go zastąpić, aby zapewnić specjalne zachowanie.

## <a name="cwinapprunautomated"></a><a name="runautomated"></a>CWinApp::UruchomAutoma

Wywołanie tej funkcji, aby ustalić, czy opcja " **/Automation**" lub " **-Automation**" jest obecny, co wskazuje, czy aplikacja serwera została uruchomiona przez aplikację kliencką.

```
BOOL RunAutomated();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli opcja została znaleziona; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli opcja jest obecna, opcja jest usuwana z wiersza polecenia. Aby uzyskać więcej informacji na temat automatyzacji ole, zobacz artykuł [Automatyzacja serwerów](../../mfc/automation-servers.md).

## <a name="cwinapprunembedded"></a><a name="runembedded"></a>CWinApp::RunEmbedded

Wywołanie tej funkcji, aby ustalić, czy opcja " **/Embedding**" lub " **-Embedding**" jest dostępna, co wskazuje, czy aplikacja serwera została uruchomiona przez aplikację kliencką.

```
BOOL RunEmbedded();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli opcja została znaleziona; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli opcja jest obecna, opcja jest usuwana z wiersza polecenia. Aby uzyskać więcej informacji na temat osadzania, zobacz artykuł [Serwery: Implementowanie serwera](../../mfc/servers-implementing-a-server.md).

## <a name="cwinappsaveallmodified"></a><a name="saveallmodified"></a>CWinApp::SaveAllModified

Wywoływane przez strukturę, aby zapisać wszystkie dokumenty, gdy okno ramki głównej aplikacji ma zostać zamknięte lub za pośrednictwem komunikatu WM_QUERYENDSESSION.

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli bezpieczne, aby zakończyć aplikację; 0, jeśli nie jest bezpieczne, aby zakończyć aplikację.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji elementu członkowskiego wywołuje funkcję [CDocument::SaveModified](../../mfc/reference/cdocument-class.md#savemodified) element członkowski z kolei dla wszystkich zmodyfikowanych dokumentów w aplikacji.

## <a name="cwinappselectprinter"></a><a name="selectprinter"></a>CWinApp::Wybierajprinter

Wywołanie tej funkcji elementu członkowskiego w celu wybrania określonej drukarki i zwolnij drukarkę, która została wcześniej wybrana w oknie dialogowym Drukowanie.

```
void SelectPrinter(
    HANDLE hDevNames,
    HANDLE hDevMode,
    BOOL bFreeOld = TRUE);
```

### <a name="parameters"></a>Parametry

*Hdevnames*<br/>
Dojście do tructure [DEVNAMES,](/windows/win32/api/commdlg/ns-commdlg-devnames)który identyfikuje nazwy portów sterownika, urządzenia i portu wyjściowego określonej drukarki.

*hDevMode (Mod.*<br/>
Dojście do struktury [DEVMODE,](/windows/win32/api/wingdi/ns-wingdi-devmodea) która określa informacje o inicjowaniu urządzenia i środowisku drukarki.

*bFreeStar*<br/>
Zwalnia wcześniej wybraną drukarkę.

### <a name="remarks"></a>Uwagi

Jeśli zarówno *hDevMode,* jak i *hDevNames* mają wartość NULL, `SelectPrinter` używa bieżącej drukarki domyślnej.

## <a name="cwinappsethelpmode"></a><a name="sethelpmode"></a>CWinApp::SetHelpMode

Ustawia typ pomocy aplikacji.

```
void SetHelpMode(AFX_HELP_TYPE eHelpType);
```

### <a name="parameters"></a>Parametry

*eHelpType (typ eHelpType)*<br/>
Określa typ pomocy do użycia. Aby uzyskać więcej informacji, zobacz [CWinApp::m_eHelpType.](#m_ehelptype)

### <a name="remarks"></a>Uwagi

Ustawia typ Pomocy aplikacji.

Aby ustawić typ Pomocy aplikacji na HTMLHelp, można wywołać [EnableHTMLHelp](#enablehtmlhelp). Po wywołaniu `EnableHTMLHelp`aplikacja musi używać HTMLHelp jako swojej aplikacji pomocy. Jeśli chcesz zmienić użycie WinHelp, `SetHelpMode` możesz wywołać i `afxWinHelp`ustawić *eHelpType* na .

## <a name="cwinappsetregistrykey"></a><a name="setregistrykey"></a>CWinApp::SetRegistryKey

Powoduje, że ustawienia aplikacji mają być przechowywane w rejestrze zamiast plików INI.

```
void SetRegistryKey(LPCTSTR lpszRegistryKey);
void SetRegistryKey(UINT nIDRegistryKey);
```

### <a name="parameters"></a>Parametry

*lpszRegistryKey (klucz)*<br/>
Wskaźnik do ciągu zawierającego nazwę klucza.

*nIDRegistryKey (Identyfikator Rejestrowy Klucz)*<br/>
Identyfikator zasobu ciągu zawierającego nazwę klucza rejestru.

### <a name="remarks"></a>Uwagi

Ta funkcja ustawia *m_pszRegistryKey*, który jest `GetProfileInt`następnie `GetProfileString` `WriteProfileInt`używany `WriteProfileString` przez , `CWinApp`, i funkcji członkowskich . Jeśli ta funkcja została wywołana, lista ostatnio używanych plików (MRU) jest również przechowywana w rejestrze. Klucz rejestru jest zwykle nazwą firmy. Jest on przechowywany w kluczu następującego formularza:\\ HKEY_CURRENT_USER\Software<\> \\ nazwa firmy<\> \\ nazwa aplikacji<\> \\ nazwa sekcji<\>nazwa wartości .

## <a name="cwinappsupportsapplicationrecovery"></a><a name="supportsapplicationrecovery"></a>CWinApp::SupportsApplicationRecovery

Określa, czy menedżer ponownego uruchamiania odzyskuje aplikację, która nieoczekiwanie została zakończona.

```
virtual BOOL SupportsApplicationRecovery() const;
```

### <a name="return-value"></a>Wartość zwracana

TRUE wskazuje, że menedżer ponownego uruchamiania odzyskuje aplikację; FALSE wskazuje, że menedżer ponownego uruchamiania nie.

## <a name="cwinappsupportsautosaveatinterval"></a><a name="supportsautosaveatinterval"></a>CWinApp::SupportsAutosaveAtInterval

Określa, czy menedżer ponownego uruchamiania automatycznie otwiera otwarte dokumenty w regularnych odstępach czasu.

```
virtual BOOL SupportsAutosaveAtInterval() const;
```

### <a name="return-value"></a>Wartość zwracana

Funkcja TRUE wskazuje, że menedżer ponownego uruchamiania otwiera dokumenty; FALSE wskazuje, że menedżer ponownego uruchamiania nie.

## <a name="cwinappsupportsautosaveatrestart"></a><a name="supportsautosaveatrestart"></a>CWinApp::SupportsAutosaveAtRestart

Określa, czy menedżer ponownego uruchamiania automatycznie automatycznie uruchamia otwarte dokumenty po ponownym uruchomieniu aplikacji.

```
virtual BOOL SupportsAutosaveAtRestart() const;
```

### <a name="return-value"></a>Wartość zwracana

Funkcja TRUE wskazuje, że menedżer ponownego uruchamiania automatycznie otwiera dokumenty po ponownym uruchomieniu aplikacji; FALSE wskazuje, że menedżer ponownego uruchamiania nie.

## <a name="cwinappsupportsrestartmanager"></a><a name="supportsrestartmanager"></a>CWinApp::SupportsRestartManager

Określa, czy aplikacja obsługuje menedżera ponownego uruchamiania.

```
virtual BOOL SupportsRestartManager() const;
```

### <a name="return-value"></a>Wartość zwracana

TRUE wskazuje, że aplikacja obsługuje menedżera ponownego uruchamiania; FALSE oznacza, że aplikacja nie.

## <a name="cwinappunregister"></a><a name="unregister"></a>CWinApp::Wyrejestrowanie

Wyrejestrowaje wszystkie pliki zarejestrowane przez obiekt aplikacji.

```
virtual BOOL Unregister();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero na sukces; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Funkcja `Unregister` cofa rejestrację wykonaną przez obiekt aplikacji i funkcję [Register.](#register) Zwykle obie funkcje są wywoływane niejawnie przez MFC i dlatego nie pojawi się w kodzie.

Zastądnij tę funkcję, aby wykonać niestandardowe kroki wyrejestrowania.

## <a name="cwinappunregistershellfiletypes"></a><a name="unregistershellfiletypes"></a>CWinApp::Wyrejestrowanie plików Plików

Wywołanie tej funkcji elementu członkowskiego, aby wyrejestrować wszystkie typy dokumentów aplikacji za pomocą Menedżera plików systemu Windows.

```
void UnregisterShellFileTypes();
```

## <a name="cwinappwinhelp"></a><a name="winhelp"></a>CWinApp::WinHelp

Wywołanie tej funkcji elementu członkowskiego, aby wywołać aplikację WinHelp.

```
virtual void WinHelp(
    DWORD_PTR dwData,
    UINT nCmd = HELP_CONTEXT);
```

### <a name="parameters"></a>Parametry

*dwData (dane)*<br/>
Określa dodatkowe dane. Używana wartość zależy od wartości parametru *nCmd.*

*nCmd (wł.)*<br/>
Określa typ żądanej pomocy. Aby uzyskać listę możliwych wartości i ich wpływ na parametr *dwData,* zobacz funkcję [WinHelp](/windows/win32/api/winuser/nf-winuser-winhelpw) Windows.

### <a name="remarks"></a>Uwagi

Struktura również wywołuje tę funkcję, aby wywołać aplikację WinHelp.

Struktura automatycznie zamknie aplikację WinHelp po zakończeniu aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#53](../../mfc/reference/codesnippet/cpp/cwinapp-class_28.cpp)]

## <a name="cwinappwriteprofilebinary"></a><a name="writeprofilebinary"></a>CWinApp::WriteProfileBinary

Wywołanie tej funkcji elementu członkowskiego, aby zapisać dane binarne w określonej sekcji rejestru aplikacji lub . ini.

```
BOOL WriteProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE pData,
    UINT nBytes);
```

### <a name="parameters"></a>Parametry

*lpszSekcja*<br/>
Wskazuje ciąg zakończony zerem, który określa sekcję zawierającą wpis. Jeśli sekcja nie istnieje, zostanie utworzona. Nazwa sekcji jest niezależna od sprawy; ciąg może być dowolną kombinacją wielkich i małych liter.

*lpszEntry*<br/>
Wskazuje ciąg zakończony zerem, który zawiera wpis, w którym ma być zapisywana wartość. Jeśli wpis nie istnieje w określonej sekcji, jest tworzony.

*Pdata*<br/>
Wskazuje na dane, które mają być zapisane.

*n Bajty*<br/>
Zawiera liczbę bajtów do zapisania.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

W tym `CWinApp* pApp = AfxGetApp();` przykładzie użyto, aby uzyskać w `WriteProfileBinary` CWinApp klasy ilustrującej sposób, który i `GetProfileBinary` może być używany z dowolnej funkcji w aplikacji MFC.

[!code-cpp[NVC_MFCWindowing#54](../../mfc/reference/codesnippet/cpp/cwinapp-class_29.cpp)]

Inny przykład można znaleźć w przykładzie [aplikacji CWinApp::GetProfileBinary](#getprofilebinary).

## <a name="cwinappwriteprofileint"></a><a name="writeprofileint"></a>CWinApp::WriteProfileInt

Wywołanie tej funkcji elementu członkowskiego, aby zapisać określoną wartość w określonej sekcji rejestru aplikacji lub . ini.

```
BOOL WriteProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nValue);
```

### <a name="parameters"></a>Parametry

*lpszSekcja*<br/>
Wskazuje ciąg zakończony zerem, który określa sekcję zawierającą wpis. Jeśli sekcja nie istnieje, zostanie utworzona. Nazwa sekcji jest niezależna od sprawy; ciąg może być dowolną kombinacją wielkich i małych liter.

*lpszEntry*<br/>
Wskazuje ciąg zakończony zerem, który zawiera wpis, w którym ma być zapisywana wartość. Jeśli wpis nie istnieje w określonej sekcji, jest tworzony.

*wartość nValue*<br/>
Zawiera wartość, która ma zostać zapisana.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

W tym `CWinApp* pApp = AfxGetApp();` przykładzie użyto, aby uzyskać w `WriteProfileString`CWinApp klasy ilustrującej sposób, który , `WriteProfileInt` `GetProfileString`, i `GetProfileInt` może być używany z dowolnej funkcji w aplikacji MFC.

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

Inny przykład można znaleźć w przykładzie [aplikacji CWinApp::GetProfileInt](#getprofileint).

## <a name="cwinappwriteprofilestring"></a><a name="writeprofilestring"></a>CWinApp::WriteProfileString

Wywołanie tej funkcji elementu członkowskiego, aby zapisać określony ciąg w określonej sekcji rejestru aplikacji lub . ini.

```
BOOL WriteProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszValue);
```

### <a name="parameters"></a>Parametry

*lpszSekcja*<br/>
Wskazuje ciąg zakończony zerem, który określa sekcję zawierającą wpis. Jeśli sekcja nie istnieje, zostanie utworzona. Nazwa sekcji jest niezależna od sprawy; ciąg może być dowolną kombinacją wielkich i małych liter.

*lpszEntry*<br/>
Wskazuje ciąg zakończony zerem, który zawiera wpis, w którym ma być zapisywana wartość. Jeśli wpis nie istnieje w określonej sekcji, jest tworzony. Jeśli ten parametr ma wartość NULL, sekcja określona przez *lpszSection* zostanie usunięta.

*lpszValue*<br/>
Wskazuje ciąg do zapisania. Jeśli ten parametr ma wartość NULL, wpis określony przez parametr *lpszEntry* zostanie usunięty.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

Inny przykład można znaleźć w przykładzie [aplikacji CWinApp::GetProfileInt](#getprofileint).

## <a name="cwinappsetappid"></a><a name="setappid"></a>CWinApp::SetAppID

Jawnie ustawia identyfikator modelu użytkownika aplikacji dla aplikacji. Ta metoda powinna być wywoływana przed każdym interfejsem użytkownika jest przedstawiony użytkownikowi (najlepszym miejscem jest konstruktor aplikacji).

```
void SetAppID(LPCTSTR lpcszAppID);
```

### <a name="parameters"></a>Parametry

*lpcszAppID*<br/>
Określa identyfikator modelu użytkownika aplikacji.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Klasa CWinThread](../../mfc/reference/cwinthread-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Instrukcje: dodawanie obsługi menedżera ponownego uruchamiania](../../mfc/how-to-add-restart-manager-support.md)
