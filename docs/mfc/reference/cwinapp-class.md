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
ms.openlocfilehash: 732bdf980240b1f496c1aca56c8a89b6a7f52d27
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502179"
---
# <a name="cwinapp-class"></a>Klasa CWinApp

Klasa bazowa, z której pochodzi obiekt aplikacji systemu Windows.

## <a name="syntax"></a>Składnia

```
class CWinApp : public CWinThread
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinApp:: CWinApp](#cwinapp)|Konstruuje `CWinApp` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinApp::AddDocTemplate](#adddoctemplate)|Dodaje szablon dokumentu do listy dostępnych szablonów dokumentów aplikacji.|
|[CWinApp::AddToRecentFileList](#addtorecentfilelist)|Dodaje nazwę pliku do listy ostatnio używanych plików (MRU).|
|[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)|Wywoływane przez platformę, gdy aplikacja nieoczekiwanie kończy pracę.|
|[CWinApp:: CloseAllDocuments](#closealldocuments)|Zamyka wszystkie otwarte dokumenty.|
|[CWinApp::CreatePrinterDC](#createprinterdc)|Tworzy kontekst urządzenia drukarki.|
|[CWinApp::DelRegTree](#delregtree)|Usuwa określony klucz i wszystkie jego podklucze.|
|[CWinApp::DoMessageBox](#domessagebox)|Implementuje [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) dla aplikacji.|
|[CWinApp::DoWaitCursor](#dowaitcursor)|Włącza i wyłącza kursor oczekiwania.|
|[CWinApp::EnableD2DSupport](#enabled2dsupport)|Włącza obsługę aplikacji D2D. Wywołaj tę metodę przed zainicjowaniem okna głównego.|
|[CWinApp::EnableHtmlHelp](#enablehtmlhelp)|Implementuje HTMLHelp dla aplikacji, a nie Program WinHelp.|
|[CWinApp::EnableTaskbarInteraction](#enabletaskbarinteraction)|Włącza interakcję paska zadań.|
|[CWinApp::ExitInstance](#exitinstance)|Zastąpienie do oczyszczenia po zakończeniu działania aplikacji.|
|[CWinApp::GetApplicationRecoveryParameter](#getapplicationrecoveryparameter)|Pobiera parametr wejściowy dla metody odzyskiwania aplikacji.|
|[CWinApp::GetApplicationRecoveryPingInterval](#getapplicationrecoverypinginterval)|Zwraca czas oczekiwania przez Menedżera ponownego uruchomienia na zwrócenie przez funkcję wywołania zwrotnego odzyskiwania.|
|[CWinApp:: GetApplicationRestartFlags](#getapplicationrestartflags)|Zwraca flagi Menedżera ponownego uruchamiania.|
|[CWinApp::GetAppRegistryKey](#getappregistrykey)|Zwraca klucz dla elementu\\HKEY_CURRENT_USER "Software" \RegistryKey\ProfileName.|
|[CWinApp::GetDataRecoveryHandler](#getdatarecoveryhandler)|Pobiera procedurę obsługi odzyskiwania danych dla tego wystąpienia aplikacji.|
|[CWinApp::GetFirstDocTemplatePosition](#getfirstdoctemplateposition)|Pobiera pozycję pierwszego szablonu dokumentu.|
|[CWinApp::GetHelpMode](#gethelpmode)|Pobiera typ pomocy używanej przez aplikację.|
|[CWinApp::GetNextDocTemplate](#getnextdoctemplate)|Pobiera pozycję szablonu dokumentu. Może być używany rekursywnie.|
|[CWinApp::GetPrinterDeviceDefaults](#getprinterdevicedefaults)|Pobiera ustawienia domyślne urządzenia drukarki.|
|[CWinApp::GetProfileBinary](#getprofilebinary)|Pobiera dane binarne z wpisu w aplikacji. Plik INI.|
|[CWinApp::GetProfileInt](#getprofileint)|Pobiera liczbę całkowitą z wpisu w aplikacji. Plik INI.|
|[CWinApp::GetProfileString](#getprofilestring)|Pobiera ciąg z wpisu w aplikacji. Plik INI.|
|[CWinApp::GetSectionKey](#getsectionkey)|Zwraca klucz dla elementu\\HKEY_CURRENT_USER "Software" \RegistryKey\AppName\lpszSection.|
|[CWinApp:: HideApplication](#hideapplication)|Ukrywa aplikację przed zamknięciem wszystkich dokumentów.|
|[CWinApp::HtmlHelp](#htmlhelp)|Wywołuje funkcję `HTMLHelp` systemu Windows.|
|[CWinApp::InitInstance](#initinstance)|Przesłoń, aby przeprowadzić inicjowanie wystąpienia systemu Windows, takie jak tworzenie obiektów okien.|
|[CWinApp::IsTaskbarInteractionEnabled](#istaskbarinteractionenabled)|Informuje, czy włączono interakcję paska zadań systemu Windows 7.|
|[CWinApp::LoadCursor](#loadcursor)|Ładuje zasób kursora.|
|[CWinApp::LoadIcon](#loadicon)|Ładuje zasób ikony.|
|[CWinApp:: LoadOEMCursor](#loadoemcursor)|Ładuje wstępnie zdefiniowany kursor OEM systemu Windows, który **OCR_** stałe w systemie Windows. C.|
|[CWinApp:: LoadOEMIcon](#loadoemicon)|Ładuje wstępnie zdefiniowaną ikonę OEM systemu Windows, która określa stałe **OIC_** w systemie Windows. C.|
|[CWinApp:: LoadStandardCursor](#loadstandardcursor)|Ładuje wstępnie zdefiniowany kursor systemu Windows, który określa stałe **IDC_** w systemie Windows. C.|
|[CWinApp:: LoadStandardIcon](#loadstandardicon)|Ładuje wstępnie zdefiniowaną ikonę systemu Windows, która określa stałe **IDI_** w systemie Windows. C.|
|[CWinApp:: OnDDECommand](#onddecommand)|Wywoływane przez platformę w odpowiedzi na polecenie wykonywania dynamicznej wymiany danych (DDE).|
|[CWinApp::OnIdle](#onidle)|Przesłoń, aby przetwarzać czas bezczynności specyficzny dla aplikacji.|
|[CWinApp::OpenDocumentFile](#opendocumentfile)|Wywoływane przez platformę, by otworzyć dokument z pliku.|
|[CWinApp::ParseCommandLine](#parsecommandline)|Analizuje poszczególne parametry i flagi w wierszu polecenia.|
|[CWinApp::PreTranslateMessage](#pretranslatemessage)|Filtruje komunikaty przed ich wysłaniem do funkcji systemu Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).|
|[CWinApp::ProcessMessageFilter](#processmessagefilter)|Przechwytuje niektóre komunikaty przed osiągnięciem aplikacji.|
|[CWinApp::ProcessShellCommand](#processshellcommand)|Obsługuje argumenty wiersza polecenia i flagi.|
|[CWinApp::ProcessWndProcException](#processwndprocexception)|Przechwytuje wszystkie Nieobsłużone wyjątki zgłoszone przez komunikaty i procedury obsługi poleceń aplikacji.|
|[CWinApp:: register](#register)|Wykonuje dostosowaną rejestrację.|
|[CWinApp::RegisterWithRestartManager](#registerwithrestartmanager)|Rejestruje aplikację za pomocą Menedżera ponownego uruchamiania.|
|[CWinApp:: ReopenPreviousFilesAtRestart](#reopenpreviousfilesatrestart)|Określa, czy Menedżer ponownego uruchamiania ponownie otwiera pliki otwarte, gdy aplikacja nieoczekiwanie zakończyła pracę.|
|[CWinApp::RestartInstance](#restartinstance)|Obsługuje ponowne uruchomienie aplikacji zainicjowane przez Menedżera ponownego uruchamiania.|
|[CWinApp::RestoreAutosavedFilesAtRestart](#restoreautosavedfilesatrestart)|Określa, czy Menedżer ponownego uruchamiania przywraca automatycznie zapisane pliki po ponownym uruchomieniu aplikacji.|
|[CWinApp::Run](#run)|Uruchamia domyślną pętlę komunikatów. Przesłoń, aby dostosować pętlę komunikatów.|
|[CWinApp:: RunAutomated](#runautomated)|Testuje wiersz polecenia aplikacji dla opcji **/Automation.** . Nieaktualne. Zamiast tego należy użyć wartości z [CCommandLineInfo:: m_bRunAutomated](../../mfc/reference/ccommandlineinfo-class.md#m_brunautomated) po wywołaniu [ParseCommandLine](#parsecommandline).|
|[CWinApp::RunEmbedded](#runembedded)|Testuje wiersz polecenia aplikacji dla opcji **przełącznikiem/Embedding** . Nieaktualne. Zamiast tego należy użyć wartości z [CCommandLineInfo:: m_bRunEmbedded](../../mfc/reference/ccommandlineinfo-class.md#m_brunembedded) po wywołaniu [ParseCommandLine](#parsecommandline).|
|[CWinApp::SaveAllModified](#saveallmodified)|Prosi użytkownika o zapisanie wszystkich zmodyfikowanych dokumentów.|
|[CWinApp::SelectPrinter](#selectprinter)|Wybiera drukarkę wcześniej wskazywaną przez użytkownika za pomocą okna dialogowego Drukuj.|
|[CWinApp::SetHelpMode](#sethelpmode)|Ustawia i inicjuje typ pomocy używanej przez aplikację.|
|[CWinApp::SupportsApplicationRecovery](#supportsapplicationrecovery)|Określa, czy Menedżer ponownego uruchamiania odzyskuje aplikację, która nieoczekiwanie zakończyła pracę.|
|[CWinApp::SupportsAutosaveAtInterval](#supportsautosaveatinterval)|Określa, czy Menedżer ponownego uruchamiania automatycznie zapisuje otwarte dokumenty w regularnych odstępach czasu.|
|[CWinApp:: SupportsAutosaveAtRestart](#supportsautosaveatrestart)|Określa, czy Menedżer ponownego uruchamiania automatycznie zapisuje wszystkie otwarte dokumenty po ponownym uruchomieniu aplikacji.|
|[CWinApp::SupportsRestartManager](#supportsrestartmanager)|Określa, czy aplikacja obsługuje Menedżera ponownego uruchamiania.|
|[CWinApp::Unregister](#unregister)|Wyrejestrowuje wszystkie elementy znane do zarejestrowania przez `CWinApp` obiekt.|
|[CWinApp:: WinHelp](#winhelp)|Wywołuje funkcję `WinHelp` systemu Windows.|
|[CWinApp::WriteProfileBinary](#writeprofilebinary)|Zapisuje dane binarne do wpisu w aplikacji. Plik INI.|
|[CWinApp::WriteProfileInt](#writeprofileint)|Zapisuje liczbę całkowitą do wpisu w aplikacji. Plik INI.|
|[CWinApp::WriteProfileString](#writeprofilestring)|Zapisuje ciąg do wpisu w aplikacji. Plik INI.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CWinApp::EnableShellOpen](#enableshellopen)|Zezwala użytkownikowi na otwieranie plików danych z Menedżera plików systemu Windows.|
|[CWinApp::LoadStdProfileSettings](#loadstdprofilesettings)|Ładuje Standard. Ustawienia pliku INI i włącza funkcję listy plików MRU.|
|[CWinApp:: OnContextHelp](#oncontexthelp)|Obsługuje pomoc dotyczącą SHIFT + F1 w aplikacji.|
|[CWinApp::OnFileNew](#onfilenew)|Implementuje polecenie ID_FILE_NEW.|
|[CWinApp::OnFileOpen](#onfileopen)|Implementuje polecenie ID_FILE_OPEN.|
|[CWinApp::OnFilePrintSetup](#onfileprintsetup)|Implementuje polecenie ID_FILE_PRINT_SETUP.|
|[CWinApp:: OnHelp](#onhelp)|Obsługuje Pomoc F1 w aplikacji (przy użyciu bieżącego kontekstu).|
|[CWinApp:: OnHelpFinder](#onhelpfinder)|Obsługuje polecenia ID_HELP_FINDER i ID_DEFAULT_HELP.|
|[CWinApp:: OnHelpIndex](#onhelpindex)|Obsługuje polecenie ID_HELP_INDEX i udostępnia domyślny temat pomocy.|
|[CWinApp:: OnHelpUsing](#onhelpusing)|Obsługuje polecenie ID_HELP_USING.|
|[CWinApp::RegisterShellFileTypes](#registershellfiletypes)|Rejestruje wszystkie typy dokumentów aplikacji za pomocą Menedżera plików systemu Windows.|
|[CWinApp::SetAppID](#setappid)|Jawnie ustawia identyfikator modelu użytkownika aplikacji dla aplikacji. Ta metoda powinna być wywoływana przed wyświetleniem przez użytkownika interfejsu użytkownika (najlepszym miejscem jest Konstruktor aplikacji).|
|[CWinApp::SetRegistryKey](#setregistrykey)|Powoduje, że ustawienia aplikacji są przechowywane w rejestrze, a nie. Pliki INI.|
|[CWinApp::UnregisterShellFileTypes](#unregistershellfiletypes)|Wyrejestrowuje wszystkie typy dokumentów aplikacji za pomocą Menedżera plików systemu Windows.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CWinApp::m_bHelpMode](#m_bhelpmode)|Wskazuje, czy użytkownik jest w trybie kontekstu pomocy (zazwyczaj wywoływany przez SHIFT + F1).|
|[CWinApp::m_eHelpType](#m_ehelptype)|Określa typ pomocy używanej przez aplikację.|
|[CWinApp::m_hInstance](#m_hinstance)|Identyfikuje bieżące wystąpienie aplikacji.|
|[CWinApp::m_lpCmdLine](#m_lpcmdline)|Wskazuje ciąg zakończony znakiem null, który określa wiersz polecenia dla aplikacji.|
|[CWinApp:: m_nCmdShow](#m_ncmdshow)|Określa sposób początkowego wyświetlania okna.|
|[CWinApp::m_pActiveWnd](#m_pactivewnd)|Wskaźnik do głównego okna aplikacji kontenera, gdy serwer OLE jest aktywny.|
|[CWinApp::m_pszAppID](#m_pszappid)|Identyfikator modelu użytkownika aplikacji.|
|[CWinApp::m_pszAppName](#m_pszappname)|Określa nazwę aplikacji.|
|[CWinApp::m_pszExeName](#m_pszexename)|Nazwa modułu aplikacji.|
|[CWinApp::m_pszHelpFilePath](#m_pszhelpfilepath)|Ścieżka do pliku pomocy aplikacji.|
|[CWinApp::m_pszProfileName](#m_pszprofilename)|Aplikacja. Nazwa pliku INI.|
|[CWinApp::m_pszRegistryKey](#m_pszregistrykey)|Służy do określania pełnego klucza rejestru do przechowywania ustawień profilu aplikacji.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CWinApp::m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags)|Flagi określające sposób zachowania Menedżera ponownego uruchamiania.|
|[CWinApp:: m_nAutosaveInterval](#m_nautosaveinterval)|Długość czasu (w milisekundach) między autozapisami.|
|[CWinApp::m_pDataRecoveryHandler](#m_pdatarecoveryhandler)|Wskaźnik do programu obsługi odzyskiwania danych dla aplikacji.|

## <a name="remarks"></a>Uwagi

Obiekt aplikacji udostępnia funkcje członkowskie do inicjowania aplikacji (i każdego z nich) oraz do uruchamiania aplikacji.

Każda aplikacja, która korzysta z klas Microsoft Foundation, może zawierać tylko jeden obiekt `CWinApp`pochodzący z. Ten obiekt jest tworzony, gdy C++ inne obiekty globalne są konstruowane i są już dostępne, gdy system `WinMain` Windows wywołuje funkcję, która jest dostarczana przez Biblioteka MFC. Zadeklaruj obiekt `CWinApp` pochodny na poziomie globalnym.

Podczas wyprowadzania klasy aplikacji z `CWinApp`, Zastąp funkcję składowej [InitInstance](#initinstance) , aby utworzyć obiekt głównego okna aplikacji.

Oprócz `CWinApp` funkcji elementów członkowskich Biblioteka MFC udostępnia następujące funkcje globalne, aby `CWinApp` uzyskać dostęp do obiektu i innych informacji globalnych:

- [AfxGetApp](application-information-and-management.md#afxgetapp) Uzyskuje wskaźnik do `CWinApp` obiektu.

- [AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle) Uzyskuje dojście do bieżącego wystąpienia aplikacji.

- [AfxGetResourceHandle](application-information-and-management.md#afxgetresourcehandle) Uzyskuje obsługę zasobów aplikacji.

- [AfxGetAppName](application-information-and-management.md#afxgetappname) Uzyskuje wskaźnik do ciągu zawierającego nazwę aplikacji. Alternatywnie, jeśli masz wskaźnik do `CWinApp` obiektu, użyj `m_pszExeName` , aby uzyskać nazwę aplikacji.

Zobacz [CWinApp: Klasa](../../mfc/cwinapp-the-application-class.md) aplikacji więcej informacji na ten temat `CWinApp` zawiera omówienie następujących elementów:

- `CWinApp`-kod pochodny tworzony przez Kreatora aplikacji.

- `CWinApp`w sekwencji wykonywania aplikacji.

- `CWinApp`domyślne implementacje funkcji Członkowskich.

- `CWinApp`kluczowe zastąpienia.

Element `m_hPrevInstance` członkowski danych już nie istnieje. Aby określić, czy jest uruchomione inne wystąpienie aplikacji, użyj nazwanego obiektu mutex. Jeśli otwarcie obiektu mutex nie powiedzie się, nie są uruchomione żadne inne wystąpienia aplikacji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWinThread](../../mfc/reference/cwinthread-class.md)

`CWinApp`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

##  <a name="adddoctemplate"></a>  CWinApp::AddDocTemplate

Wywołaj tę funkcję elementu członkowskiego, aby dodać szablon dokumentu do listy dostępnych szablonów dokumentów, które obsługuje aplikacja.

```
void AddDocTemplate(CDocTemplate* pTemplate);
```

### <a name="parameters"></a>Parametry

*pTemplate*<br/>
Wskaźnik do `CDocTemplate` dodania.

### <a name="remarks"></a>Uwagi

Przed wywołaniem [RegisterShellFileTypes](#registershellfiletypes)należy dodać wszystkie szablony dokumentów do aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#35](../../mfc/reference/codesnippet/cpp/cwinapp-class_1.cpp)]

##  <a name="addtorecentfilelist"></a>  CWinApp::AddToRecentFileList

Wywołaj tę funkcję elementu członkowskiego, aby dodać *lpszPathName* do listy ostatnio używanych plików.

```
virtual void AddToRecentFileList(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Ścieżka pliku.

### <a name="remarks"></a>Uwagi

Należy wywołać funkcję elementu członkowskiego [LoadStdProfileSettings](#loadstdprofilesettings) , aby załadować bieżącą listę plików MRU przed użyciem tej funkcji elementu członkowskiego.

Struktura wywołuje tę funkcję elementu członkowskiego, gdy otwiera plik lub wykonuje polecenie Zapisz jako, aby zapisać plik o nowej nazwie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#36](../../mfc/reference/codesnippet/cpp/cwinapp-class_2.cpp)]

##  <a name="applicationrecoverycallback"></a>CWinApp:: ApplicationRecoveryCallback

Wywoływane przez platformę, gdy aplikacja nieoczekiwanie kończy pracę.

```
virtual DWORD ApplicationRecoveryCallback(LPVOID lpvParam);
```

### <a name="parameters"></a>Parametry

*lpvParam*<br/>
podczas Zarezerwowane do użytku w przyszłości.

### <a name="return-value"></a>Wartość zwracana

0, jeśli ta metoda zakończyła się pomyślnie; niezerowe, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja obsługuje Menedżera ponownego uruchamiania, struktura wywołuje tę funkcję, gdy aplikacja nieoczekiwanie zakończy pracę.

Domyślna implementacja programu `ApplicationRecoveryCallback` używa programu, `CDataRecoveryHandler` aby zapisać listę obecnie otwartych dokumentów w rejestrze. Ta metoda nie powoduje automatycznego zapisywania plików.

Aby dostosować zachowanie, Zastąp tę funkcję w pochodnej [klasie CWinApp](../../mfc/reference/cwinapp-class.md) lub Przekaż własną metodę odzyskiwania aplikacji jako parametr do [CWinApp:: RegisterWithRestartManager](#registerwithrestartmanager).

##  <a name="closealldocuments"></a>CWinApp:: CloseAllDocuments

Wywołaj tę funkcję elementu członkowskiego, aby zamknąć wszystkie otwarte dokumenty przed zamknięciem.

```
void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>Parametry

*bEndSession*<br/>
Określa, czy sesja systemu Windows jest zakończona. Ma to wartość PRAWDA, jeśli sesja jest zakończona; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wywołaj [HideApplication](#hideapplication) przed `CloseAllDocuments`wywołaniem.

##  <a name="createprinterdc"></a>CWinApp:: CreatePrinterDC

Wywołaj tę funkcję elementu członkowskiego, aby utworzyć kontekst urządzenia drukarki (DC) z wybranej drukarki.

```
BOOL CreatePrinterDC(CDC& dc);
```

### <a name="parameters"></a>Parametry

*DC*<br/>
Odwołanie do kontekstu urządzenia drukarki.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli kontekst urządzenia drukarki został utworzony pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`CreatePrinterDC`Inicjuje kontekst urządzenia przekazywany przez odwołanie, aby można było go użyć do drukowania.

Jeśli funkcja się powiedzie, po zakończeniu drukowania należy zniszczyć kontekst urządzenia. Można pozwolić, aby destruktor obiektu przerzucał go, lub można go jawnie poprzez wywołanie metody [przechwytywania::D eletedc](../../mfc/reference/cdc-class.md#deletedc). [](../../mfc/reference/cdc-class.md)

##  <a name="cwinapp"></a>CWinApp:: CWinApp

Konstruuje obiekt i przekazuje lpszAppName, aby były przechowywane jako nazwa aplikacji. `CWinApp`

```
CWinApp(LPCTSTR lpszAppName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszAppName*<br/>
Ciąg zakończony znakiem null, który zawiera nazwę aplikacji używaną przez system Windows. Jeśli ten argument nie zostanie podany lub ma wartość null `CWinApp` , używa ciągu zasobu AFX_IDS_APP_TITLE lub nazwy pliku wykonywalnego.

### <a name="remarks"></a>Uwagi

Należy skonstruować jeden obiekt `CWinApp`globalny klasy pochodnej. W aplikacji może znajdować `CWinApp` się tylko jeden obiekt. Konstruktor przechowuje wskaźnik do `CWinApp` obiektu, `WinMain` tak aby można było wywołać funkcje elementu członkowskiego obiektu w celu zainicjowania i uruchomienia aplikacji.

##  <a name="delregtree"></a>  CWinApp::DelRegTree

Usuwa określony klucz rejestru i wszystkie jego podklucze.

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

*hParentKey*<br/>
Dojście do klucza rejestru.

*strKeyName*<br/>
Nazwa klucza rejestru, który ma zostać usunięty.

*pTM*<br/>
Wskaźnik do obiektu CAtlTransactionManager.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, zwracaną wartością jest ERROR_SUCCESS. Jeśli funkcja się nie powiedzie, wartość zwracana jest niezerowym kodem błędu zdefiniowanym w Winerror. h.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby usunąć określony klucz i jego podklucz.

##  <a name="domessagebox"></a>CWinApp::D oMessageBox

Struktura wywołuje tę funkcję członkowską w celu zaimplementowania okna komunikatu dla funkcji globalnej [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox).

```
virtual int DoMessageBox(
    LPCTSTR lpszPrompt,
    UINT nType,
    UINT nIDPrompt);
```

### <a name="parameters"></a>Parametry

*lpszPrompt*<br/>
Adres tekstu w oknie komunikatu.

*Npowiadomienia*<br/>
[Styl](../../mfc/reference/styles-used-by-mfc.md#message-box-styles)okna komunikatu.

*nIDPrompt*<br/>
Indeks ciągu kontekstu pomocy.

### <a name="return-value"></a>Wartość zwracana

Zwraca te same wartości co `AfxMessageBox`.

### <a name="remarks"></a>Uwagi

Nie wywołuj tej funkcji elementu członkowskiego, aby otworzyć okno komunikatu. Użyj `AfxMessageBox` zamiast tego.

Zastąp tę funkcję elementu członkowskiego, aby dostosować przetwarzanie wywołań `AfxMessageBox` w całej aplikacji.

##  <a name="dowaitcursor"></a>CWinApp::D oWaitCursor

Ta funkcja członkowska jest wywoływana przez platformę w celu zaimplementowania [CWaitCursor](../../mfc/reference/cwaitcursor-class.md), [CCmdTarget:: BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget:: EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)i [CCmdTarget:: RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor).

```
virtual void DoWaitCursor(int nCode);
```

### <a name="parameters"></a>Parametry

*nCode*<br/>
Jeśli ten parametr ma wartość 1, pojawi się kursor oczekiwania. Jeśli wartość jest równa 0, kursor oczekiwania zostanie przywrócony bez zwiększania liczby odwołań. Jeśli-1, kursor oczekiwania zostanie zakończony.

### <a name="remarks"></a>Uwagi

Domyślna implementacja kursora klepsydry. `DoWaitCursor`zachowuje liczbę odwołań. W przypadku wartości dodatniej wyświetlany jest kursor klepsydry.

Mimo że nie jest to zwykle `DoWaitCursor` możliwe, można zastąpić tę funkcję elementu członkowskiego, aby zmienić kursor oczekiwania lub wykonać dodatkowe przetwarzanie podczas wyświetlania kursora oczekiwania.

Aby ułatwić, bardziej usprawnić sposób implementacji kursora oczekiwania, użyj `CWaitCursor`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#37](../../mfc/reference/codesnippet/cpp/cwinapp-class_3.cpp)]

##  <a name="enabled2dsupport"></a>CWinApp:: EnableD2DSupport

Wymagany jest dodatek SP1 dla programu Visual Studio 2010.

Włącza obsługę aplikacji D2D. Wywołaj tę metodę przed zainicjowaniem okna głównego.

```
BOOL EnableD2DSupport(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>Parametry

*d2dFactoryType*<br/>
Model wątkowości fabryki D2D i tworzonych przez nią zasobów.

*writeFactoryType*<br/>
Wartość określająca, czy obiekt fabryki zapisu będzie współużytkowany, czy izolowany

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli włączono obsługę D2D, FAŁSZ — w przeciwnym razie

##  <a name="enablehtmlhelp"></a>CWinApp:: EnableHtmlHelp

Wywołaj tę funkcję elementu członkowskiego z poziomu konstruktora `CWinApp`klasy pochodnej, aby użyć HTMLHelp do pomocy aplikacji.

```
void EnableHtmlHelp();
```

### <a name="remarks"></a>Uwagi

##  <a name="enableshellopen"></a>CWinApp:: EnableShellOpen

Wywołaj tę funkcję, zazwyczaj z `InitInstance` przesłonięcia, aby umożliwić użytkownikom aplikacji otwieranie plików danych po dwukrotnym kliknięciu plików z poziomu Menedżera plików systemu Windows.

```
void EnableShellOpen();
```

### <a name="remarks"></a>Uwagi

Wywołaj `RegisterShellFileTypes` funkcję członkowską w połączeniu z tą funkcją lub podaj. Plik REG z aplikacją do ręcznej rejestracji typów dokumentów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#38](../../mfc/reference/codesnippet/cpp/cwinapp-class_4.cpp)]

##  <a name="enabletaskbarinteraction"></a>CWinApp:: EnableTaskbarInteraction

Włącza interakcję paska zadań.

```
BOOL EnableTaskbarInteraction(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Określa, czy interakcja z paskiem zadań systemu Windows 7 powinna być włączona (TRUE), czy wyłączona (FALSE).

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli interakcja paska zadań może być włączona lub wyłączona.

### <a name="remarks"></a>Uwagi

Ta metoda musi być wywoływana przed utworzeniem okna głównego, w przeciwnym razie potwierdzenia i zwraca wartość FALSE.

##  <a name="exitinstance"></a>CWinApp:: ExitInstance

Wywoływane przez platformę z poziomu `Run` funkcji składowej, aby wyjść z tego wystąpienia aplikacji.

```
virtual int ExitInstance();
```

### <a name="return-value"></a>Wartość zwracana

Kod zakończenia aplikacji; wartość 0 oznacza brak błędów, a wartości większe niż 0 wskazują na błąd. Ta wartość jest używana jako wartość zwracana z `WinMain`.

### <a name="remarks"></a>Uwagi

Nie wywołuj tej funkcji elementu członkowskiego z dowolnego miejsca, `Run` ale wewnątrz funkcji składowej.

Domyślna implementacja tej funkcji zapisuje opcje struktury w aplikacji. Plik INI. Przesłoń tę funkcję, aby oczyścić ją po zakończeniu działania aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#39](../../mfc/reference/codesnippet/cpp/cwinapp-class_5.cpp)]

##  <a name="getapplicationrecoveryparameter"></a>CWinApp:: GetApplicationRecoveryParameter

Pobiera parametr wejściowy dla metody odzyskiwania aplikacji.

```
virtual LPVOID GetApplicationRecoveryParameter();
```

### <a name="return-value"></a>Wartość zwracana

Domyślny parametr wejściowy dla metody odzyskiwania aplikacji.

### <a name="remarks"></a>Uwagi

Domyślne zachowanie tej funkcji zwraca wartość NULL.

Aby uzyskać więcej informacji, zobacz [CWinApp:: ApplicationRecoveryCallback](#applicationrecoverycallback).

##  <a name="getapplicationrecoverypinginterval"></a>CWinApp:: GetApplicationRecoveryPingInterval

Zwraca czas oczekiwania przez Menedżera ponownego uruchomienia na zwrócenie przez funkcję wywołania zwrotnego odzyskiwania.

```
virtual DWORD GetApplicationRecoveryPingInterval();
```

### <a name="return-value"></a>Wartość zwracana

Długość czasu (w milisekundach).

### <a name="remarks"></a>Uwagi

Gdy aplikacja zarejestrowana za pomocą Menedżera ponownego uruchamiania kończy się nieoczekiwanie, aplikacja próbuje zapisać otwarte dokumenty i wywołuje funkcję wywołania zwrotnego odzyskiwania. Domyślna funkcja wywołania zwrotnego odzyskiwania to [CWinApp:: ApplicationRecoveryCallback](#applicationrecoverycallback).

Czas oczekiwania platformy na zwrócenie przez funkcję wywołania zwrotnego odzyskiwania jest interwałem ping. Interwał ping można dostosować, zastępując `CWinApp::GetApplicationRecoveryPingInterval` lub podając `RegisterWithRestartManager`wartość niestandardową.

##  <a name="getapplicationrestartflags"></a>CWinApp:: GetApplicationRestartFlags

Zwraca flagi Menedżera ponownego uruchamiania.

```
virtual DWORD GetApplicationRestartFlags();
```

### <a name="return-value"></a>Wartość zwracana

Flagi Menedżera ponownego uruchamiania. Domyślna implementacja zwraca wartość 0.

### <a name="remarks"></a>Uwagi

Flagi Menedżera ponownego uruchamiania nie mają wpływu na implementację domyślną. Są one udostępniane do użytku w przyszłości.

Flagi są ustawiane podczas rejestrowania aplikacji za pomocą Menedżera ponownego uruchamiania przy użyciu [CWinApp:: RegisterWithRestartManager](#registerwithrestartmanager).

Możliwe wartości dla flag Menedżera ponownego uruchomienia są następujące:

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

##  <a name="getappregistrykey"></a>CWinApp:: GetAppRegistryKey

Zwraca klucz dla elementu HKEY_CURRENT_USER\\"Software" \RegistryKey\ProfileName.

```
HKEY GetAppRegistryKey(CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*pTM*<br/>
Wskaźnik do `CAtlTransactionManager` obiektu.

### <a name="return-value"></a>Wartość zwracana

Klucz aplikacji, jeśli funkcja się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

##  <a name="getdatarecoveryhandler"></a>CWinApp:: GetDataRecoveryHandler

Pobiera procedurę obsługi odzyskiwania danych dla tego wystąpienia aplikacji.

```
virtual CDataRecoveryHandler *GetDataRecoveryHandler();
```

### <a name="return-value"></a>Wartość zwracana

Program obsługi odzyskiwania danych dla tego wystąpienia aplikacji.

### <a name="remarks"></a>Uwagi

Każda aplikacja, która korzysta z Menedżera ponownego uruchamiania, musi mieć jedno wystąpienie [klasy CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md). Ta klasa jest odpowiedzialna za monitorowanie otwartych dokumentów i zapisywanie plików. Zachowanie `CDataRecoveryHandler` zależy od konfiguracji Menedżera ponownego uruchamiania. Aby uzyskać więcej informacji, zobacz [Klasa CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md).

Ta metoda zwraca wartość NULL w systemach operacyjnych starszych niż Windows Vista. Menedżer ponownego uruchamiania nie jest obsługiwany w systemach operacyjnych starszych niż Windows Vista.

Jeśli aplikacja nie ma obecnie procedury obsługi odzyskiwania danych, ta metoda tworzy jedną i zwraca do niej wskaźnik.

##  <a name="getfirstdoctemplateposition"></a>CWinApp:: GetFirstDocTemplatePosition

Pobiera pozycję pierwszego szablonu dokumentu w aplikacji.

```
POSITION GetFirstDocTemplatePosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość pozycji, która może być używana do pobierania iteracji lub wskaźnika obiektu; Wartość NULL, jeśli lista jest pusta.

### <a name="remarks"></a>Uwagi

Użyj wartości POSITION zwracanej w wywołaniu [GetNextDocTemplate](#getnextdoctemplate) , aby pobrać pierwszy obiekt [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) .

##  <a name="gethelpmode"></a>CWinApp:: gethelpmode

Pobiera typ pomocy używanej przez aplikację.

```
AFX_HELP_TYPE GetHelpMode();
```

### <a name="return-value"></a>Wartość zwracana

Typ pomocy używany przez aplikację. Aby uzyskać więcej informacji, zobacz [CWinApp:: m_eHelpType](#m_ehelptype) .

##  <a name="getnextdoctemplate"></a>CWinApp:: GetNextDocTemplate

Pobiera szablon dokumentu identyfikowany przez program *pos*, a następnie ustawia *punkt sprzedaży* na wartość pozycji.

```
CDocTemplate* GetNextDocTemplate(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Odwołanie do wartości pozycji zwróconej przez poprzednie wywołanie `GetNextDocTemplate` lub [GetFirstDocTemplatePosition](#getfirstdoctemplateposition). Wartość jest aktualizowana do następnej pozycji przez to wywołanie.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) .

### <a name="remarks"></a>Uwagi

Można użyć `GetNextDocTemplate` w pętli iteracji do przodu, jeśli ustanowi początkową pozycję z wywołaniem do `GetFirstDocTemplatePosition`.

Musisz się upewnić, że wartość pozycji jest prawidłowa. Jeśli jest nieprawidłowa, wersja debugowana biblioteka MFC potwierdzenia.

Jeśli pobrany szablon dokumentu jest ostatnim dostępnym, Nowa wartość *pos* jest ustawiona na wartość null.

##  <a name="getprinterdevicedefaults"></a>CWinApp:: GetPrinterDeviceDefaults

Wywołaj tę funkcję elementu członkowskiego, aby przygotować kontekst urządzenia drukarki do drukowania.

```
BOOL GetPrinterDeviceDefaults(struct tagPDA* pPrintDlg);
```

### <a name="parameters"></a>Parametry

*pPrintDlg*<br/>
Wskaźnik do struktury [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-pdw) .

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pobiera bieżące wartości domyślne drukarki z systemu Windows. Plik INI w razie potrzeby lub używa ostatniej konfiguracji drukarki ustawionej przez użytkownika w konfiguracji drukowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#40](../../mfc/reference/codesnippet/cpp/cwinapp-class_6.cpp)]

##  <a name="getprofilebinary"></a>CWinApp:: GetProfileBinary

Wywołaj tę funkcję elementu członkowskiego, aby pobrać dane binarne z wpisu w określonej sekcji rejestru aplikacji lub. Plik INI.

```
BOOL GetProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE* ppData,
    UINT* pBytes);
```

### <a name="parameters"></a>Parametry

*lpszSection*<br/>
Wskazuje ciąg zakończony znakiem null, który określa sekcję zawierającą wpis.

*lpszEntry*<br/>
Wskazuje ciąg zakończony znakiem null, który zawiera wpis, którego wartość ma zostać pobrana.

*ppData*<br/>
Wskazuje wskaźnik, który będzie otrzymywał adres danych.

*pBytes*<br/>
Wskazuje element UINT, który będzie otrzymywał rozmiar danych (w bajtach).

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska nie uwzględnia wielkości liter, dlatego ciągi w parametrach *lpszSection* i *lpszEntry* mogą się różnić w przypadku.

> [!NOTE]
> `GetProfileBinary`przydziela bufor i zwraca jego adres w \* *ppData*. Obiekt wywołujący jest odpowiedzialny za zwolnienie buforu przy użyciu polecenia **delete []** .

> [!IMPORTANT]
> Dane zwrócone przez tę funkcję nie muszą mieć wartości NULL, a obiekt wywołujący musi przeprowadzić walidację. Aby uzyskać więcej informacji, zobacz Unikanie przekroczeń [buforu](/windows/win32/SecBP/avoiding-buffer-overruns).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#41](../../mfc/reference/codesnippet/cpp/cwinapp-class_7.cpp)]

Aby uzyskać dodatkowy przykład, zobacz [CWinApp:: WriteProfileBinary](#writeprofilebinary).

##  <a name="getprofileint"></a>CWinApp:: GetProfileInt

Wywołaj tę funkcję elementu członkowskiego, aby pobrać wartość całkowitą z wpisu w określonej sekcji rejestru aplikacji lub. Plik INI.

```
UINT GetProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nDefault);
```

### <a name="parameters"></a>Parametry

*lpszSection*<br/>
Wskazuje ciąg zakończony znakiem null, który określa sekcję zawierającą wpis.

*lpszEntry*<br/>
Wskazuje ciąg zakończony znakiem null, który zawiera wpis, którego wartość ma zostać pobrana.

*nDefault*<br/>
Określa wartość domyślną, która ma zostać zwrócona, jeśli struktura nie może znaleźć wpisu.

### <a name="return-value"></a>Wartość zwracana

Wartość całkowita ciągu, który następuje po poprawnym wpisie. Wartość zwracana jest wartością parametru *nDefault* , jeśli funkcja nie znajduje wpisu. Wartość zwracana jest równa 0, jeśli wartość odpowiadająca określonemu wpisowi nie jest liczbą całkowitą.

Ta funkcja członkowska obsługuje notację szesnastkową dla wartości w. Plik INI. Po pobraniu liczby całkowitej ze znakiem należy rzutować wartość na **int**.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska nie uwzględnia wielkości liter, dlatego ciągi w parametrach *lpszSection* i *lpszEntry* mogą się różnić w przypadku.

> [!IMPORTANT]
> Dane zwrócone przez tę funkcję nie muszą mieć wartości NULL, a obiekt wywołujący musi przeprowadzić walidację. Aby uzyskać więcej informacji, zobacz Unikanie przekroczeń [buforu](/windows/win32/SecBP/avoiding-buffer-overruns).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#42](../../mfc/reference/codesnippet/cpp/cwinapp-class_8.cpp)]

Aby uzyskać dodatkowy przykład, zobacz [CWinApp:: WriteProfileInt](#writeprofileint).

##  <a name="getprofilestring"></a>CWinApp:: GetProfileString

Wywołaj tę funkcję elementu członkowskiego, aby pobrać ciąg skojarzony z wpisem w określonej sekcji w rejestrze aplikacji lub. Plik INI.

```
CString GetProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszDefault = NULL);
```

### <a name="parameters"></a>Parametry

*lpszSection*<br/>
Wskazuje ciąg zakończony znakiem null, który określa sekcję zawierającą wpis.

*lpszEntry*<br/>
Wskazuje ciąg zakończony znakiem null, który zawiera wpis, którego ciąg ma zostać pobrany. Ta wartość nie może być RÓWNa NULL.

*lpszDefault*<br/>
Wskazuje domyślną wartość ciągu dla danego wpisu, jeśli nie można odnaleźć wpisu w pliku inicjującym.

### <a name="return-value"></a>Wartość zwracana

Wartość zwracana jest ciągiem z aplikacji. Plik INI lub *lpszDefault* , jeśli nie można znaleźć ciągu. Maksymalna długość ciągu obsługiwana przez platformę to _MAX_PATH. Jeśli *lpszDefault* ma wartość null, zwracana wartość jest ciągiem pustym.

### <a name="remarks"></a>Uwagi

> [!IMPORTANT]
> Dane zwrócone przez tę funkcję nie muszą mieć wartości NULL, a obiekt wywołujący musi przeprowadzić walidację. Aby uzyskać więcej informacji, zobacz Unikanie przekroczeń [buforu](/windows/win32/SecBP/avoiding-buffer-overruns).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

Aby uzyskać inny przykład, zobacz przykład dla [CWinApp:: GetProfileInt](#getprofileint).

##  <a name="getsectionkey"></a>CWinApp:: GetSectionKey

Zwraca klucz dla elementu HKEY_CURRENT_USER\\"Software" \RegistryKey\AppName\lpszSection.

```
HKEY GetSectionKey(
    LPCTSTR lpszSection,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*lpszSection*<br/>
Nazwa klucza do uzyskania.

*pTM*<br/>
Wskaźnik do `CAtlTransactionManager` obiektu.

### <a name="return-value"></a>Wartość zwracana

Klucz sekcji, jeśli funkcja się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

##  <a name="hideapplication"></a>CWinApp:: HideApplication

Wywołaj tę funkcję elementu członkowskiego, aby ukryć aplikację przed zamknięciem otwartych dokumentów.

```
void HideApplication();
```

##  <a name="htmlhelp"></a>  CWinApp::HtmlHelp

Wywołaj tę funkcję elementu członkowskiego, aby wywołać aplikację HTMLHelp.

```
virtual void HtmlHelp(
    DWORD_PTR dwData,
    UINT nCmd = 0x000F);
```

### <a name="parameters"></a>Parametry

*dwData*<br/>
Określa dodatkowe dane. Używana wartość zależy od wartości parametru *nCmd* . Wartość domyślna `0x000F` to [HH_HELP_CONTEXT](/previous-versions/windows/desktop/htmlhelp/hh-help-context-command).

*nCmd*<br/>
Określa typ żądanej pomocy. Aby zapoznać się z listą możliwych wartości i wpływem na parametr *dwData* , zobacz parametr *uCommand* opisany w funkcjach interfejsu API [HtmlHelpW](/windows/win32/api/htmlhelp/nf-htmlhelp-htmlhelpw) lub [HtmlHelpA](/windows/win32/api/htmlhelp/nf-htmlhelp-htmlhelpa) w Windows SDK.  

### <a name="remarks"></a>Uwagi

Struktura wywołuje również tę funkcję, aby wywołać aplikację HTMLHelp.

Platforma automatycznie zamknie aplikację HTMLHelp, gdy aplikacja zostanie przerwana.

##  <a name="initinstance"></a>CWinApp:: InitInstance

System Windows umożliwia uruchamianie kilku kopii tego samego programu w tym samym czasie.

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli Inicjalizacja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Inicjalizacja aplikacji jest koncepcyjnie dzielona na dwie sekcje: jednorazowe inicjowanie aplikacji wykonywane podczas pierwszego uruchomienia programu oraz inicjowanie wystąpienia, które jest uruchamiane za każdym razem, gdy zostanie uruchomiona kopia programu, w tym po raz pierwszy. Implementacja `WinMain` platformy wywołuje tę funkcję.

Przesłoń `InitInstance` , aby zainicjować każde nowe wystąpienie aplikacji uruchomionej w systemie Windows. Zwykle przesłonisz `InitInstance` Konstruowanie obiektu głównego okna i `CWinThread::m_pMainWnd` ustawisz element członkowski danych w taki sposób, aby wskazywał to okno. Aby uzyskać więcej informacji na temat przesłaniania tej funkcji [elementu członkowskiego, zobacz CWinApp: Klasa](../../mfc/cwinapp-the-application-class.md)aplikacji.

> [!NOTE]
> Aplikacje MFC muszą być zainicjowane jako Apartament jednowątkowy (STA). Jeśli wywołasz [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) w `InitInstance` przesłonięciu, określ COINIT_APARTMENTTHREADED (zamiast COINIT_MULTITHREADED).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCListView#9](../../atl/reference/codesnippet/cpp/cwinapp-class_10.cpp)]

##  <a name="istaskbarinteractionenabled"></a>CWinApp:: IsTaskbarInteractionEnabled

Informuje, czy włączono interakcję paska zadań systemu Windows 7.

```
virtual BOOL IsTaskbarInteractionEnabled();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA `EnableTaskbarInteraction` , jeśli został wywołany, a system operacyjny to Windows 7 lub nowszy.

### <a name="remarks"></a>Uwagi

Interakcja paska zadań oznacza, że aplikacja MDI wyświetla zawartość elementów podrzędnych MDI w oddzielnych miniaturach z kartami, które są wyświetlane, gdy wskaźnik myszy znajduje się nad przyciskiem paska zadań aplikacji.

##  <a name="loadcursor"></a>CWinApp:: LoadCursor

Ładuje zasób kursora o nazwie *lpszResourceName* lub określony przez *nIDResource* z bieżącego pliku wykonywalnego.

```
HCURSOR LoadCursor(LPCTSTR lpszResourceName) const;  HCURSOR LoadCursor(UINT nIDResource) const;
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Wskazuje ciąg zakończony znakiem null, który zawiera nazwę zasobu kursora. `CString` Dla tego argumentu można użyć.

*nIDResource*<br/>
Identyfikator zasobu kursora. Aby uzyskać listę zasobów, zobacz [LoadCursor](/windows/win32/api/winuser/nf-winuser-loadcursorw) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Dojście do kursora w przypadku powodzenia; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

`LoadCursor`ładuje kursor do pamięci tylko wtedy, gdy nie został poprzednio załadowany; w przeciwnym razie Pobiera dojście istniejącego zasobu.

Użyj funkcji składowej [LoadStandardCursor](#loadstandardcursor) lub [LoadOEMCursor](#loadoemcursor) , aby uzyskać dostęp do wstępnie zdefiniowanych kursorów systemu Windows.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#44](../../mfc/reference/codesnippet/cpp/cwinapp-class_11.cpp)]

##  <a name="loadicon"></a>CWinApp:: LoadIcon

Ładuje zasób ikony o nazwie *lpszResourceName* lub określony przez *nIDResource* z pliku wykonywalnego.

```
HICON LoadIcon(LPCTSTR lpszResourceName) const;  HICON LoadIcon(UINT nIDResource) const;
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Wskazuje ciąg zakończony znakiem null, który zawiera nazwę zasobu ikony. Można również użyć `CString` dla tego argumentu.

*nIDResource*<br/>
Numer IDENTYFIKACYJNy zasobu ikony.

### <a name="return-value"></a>Wartość zwracana

Dojście do ikony, jeśli się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

`LoadIcon`ładuje ikonę tylko wtedy, gdy nie została wcześniej załadowana; w przeciwnym razie Pobiera dojście istniejącego zasobu.

Aby uzyskać dostęp do wstępnie zdefiniowanych ikon systemu Windows, można użyć funkcji składowej [LoadStandardIcon](#loadstandardicon) lub [LoadOEMIcon](#loadoemicon) .

> [!NOTE]
> Ta funkcja członkowska wywołuje funkcję Win32 API [LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw), która może ładować ikonę, której rozmiar jest zgodny z wartościami metryk systemu SM_CXICON i SM_CYICON.

##  <a name="loadoemcursor"></a>CWinApp:: LoadOEMCursor

Ładuje zasób wstępnie zdefiniowanego kursora systemu Windows określony przez *nIDCursor*.

```
HCURSOR LoadOEMCursor(UINT nIDCursor) const;
```

### <a name="parameters"></a>Parametry

*nIDCursor*<br/>
Stały identyfikator manifestu **OCR_** , który określa wstępnie zdefiniowany kursor systemu Windows. Musisz `#define OEMRESOURCE` wcześniej`#include \<afxwin.h>` uzyskać dostęp do stałych **OCR_** w systemie Windows. C.

### <a name="return-value"></a>Wartość zwracana

Dojście do kursora w przypadku powodzenia; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Użyj funkcji składowej [](#loadstandardcursor) lubLoadStandardCursor,abyuzyskaćdostępdowstępniezdefiniowanychkursorówsystemu`LoadOEMCursor` Windows.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#45](../../mfc/reference/codesnippet/cpp/cwinapp-class_12.h)]

[!code-cpp[NVC_MFCWindowing#46](../../mfc/reference/codesnippet/cpp/cwinapp-class_13.cpp)]

##  <a name="loadoemicon"></a>CWinApp:: LoadOEMIcon

Ładuje zasób ikony wstępnie zdefiniowanej systemu Windows określony przez *nIDIcon*.

```
HICON LoadOEMIcon(UINT nIDIcon) const;
```

### <a name="parameters"></a>Parametry

*nIDIcon*<br/>
Stały identyfikator manifestu **OIC_** , który określa wstępnie zdefiniowaną ikonę systemu Windows. Musisz mieć `#define OEMRESOURCE` wcześniej `#include \<afxwin.h>` dostęp do stałych **OIC_** w systemie Windows. C.

### <a name="return-value"></a>Wartość zwracana

Dojście do ikony, jeśli się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Użyj funkcji składowej [](#loadstandardicon) lubLoadStandardIcon,abyuzyskaćdostępdowstępniezdefiniowanychikonsystemu`LoadOEMIcon` Windows.

##  <a name="loadstandardcursor"></a>CWinApp:: LoadStandardCursor

Ładuje zasób wstępnie zdefiniowanego kursora systemu Windows, który *lpszCursorName* określa.

```
HCURSOR LoadStandardCursor(LPCTSTR lpszCursorName) const;
```

### <a name="parameters"></a>Parametry

*lpszCursorName*<br/>
Stały identyfikator manifestu **IDC_** , który określa wstępnie zdefiniowany kursor systemu Windows. Te identyfikatory są zdefiniowane w systemie WINDOWS. C. Na poniższej liście przedstawiono możliwe wstępnie zdefiniowane wartości i znaczenia dla *lpszCursorName*:

- Kursor standardowej strzałki IDC_ARROW

- Kursor standardowego wstawiania tekstu IDC_IBEAM

- IDC_WAIT, który jest używany, gdy system Windows wykonuje zadanie czasochłonne

- IDC_CROSS kursora krzyżowego dla zaznaczenia

- Strzałka IDC_UPARROW, która wskazuje prostą

- IDC_SIZE przestarzałe i nieobsługiwane; Użyj IDC_SIZEALL

- IDC_SIZEALL strzałkę z czterema ostrami. Kursor używany do zmiany rozmiaru okna.

- IDC_ICON przestarzałe i nieobsługiwane. Użyj IDC_ARROW.

- IDC_SIZENWSE strzałka dwukierunkowa z końcami w lewym górnym rogu i w prawo

- IDC_SIZENESW strzałka dwukierunkowa z końcami w prawym górnym rogu i z lewej u dołu

- IDC_SIZEWEa Strzałka w poziomie z dwoma grotami

- IDC_SIZENS pionowa strzałka z dwoma grotami

### <a name="return-value"></a>Wartość zwracana

Dojście do kursora w przypadku powodzenia; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Użyj funkcji składowej [](#loadoemcursor) lubLoadOEMCursor,abyuzyskaćdostępdowstępniezdefiniowanychkursorówsystemu`LoadStandardCursor` Windows.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#47](../../mfc/reference/codesnippet/cpp/cwinapp-class_14.cpp)]

##  <a name="loadstandardicon"></a>CWinApp:: LoadStandardIcon

Ładuje zasób ikony wstępnie zdefiniowanej systemu Windows, który *lpszIconName* określa.

```
HICON LoadStandardIcon(LPCTSTR lpszIconName) const;
```

### <a name="parameters"></a>Parametry

*lpszIconName*<br/>
Stały identyfikator manifestu, który określa wstępnie zdefiniowaną ikonę systemu Windows. Te identyfikatory są zdefiniowane w systemie WINDOWS. C. Aby zapoznać się z listą możliwych wstępnie zdefiniowanych wartości i ich opisów, zobacz parametr *lpIconName* w [LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Dojście do ikony, jeśli się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Użyj funkcji składowej [](#loadoemicon) lubLoadOEMIcon,abyuzyskaćdostępdowstępniezdefiniowanychikonsystemu`LoadStandardIcon` Windows.

##  <a name="loadstdprofilesettings"></a>CWinApp:: LoadStdProfileSettings

Wywołaj tę funkcję elementu członkowskiego z poziomu funkcji składowej [InitInstance](#initinstance) , aby włączyć i załadować listę ostatnio używanych plików (MRU) i ostatni stan wersji zapoznawczej.

```
void LoadStdProfileSettings(UINT nMaxMRU = _AFX_MRU_COUNT);
```

### <a name="parameters"></a>Parametry

*nMaxMRU*<br/>
Liczba ostatnio używanych plików do śledzenia.

### <a name="remarks"></a>Uwagi

Jeśli *nMaxMRU* ma wartość 0, nie będzie utrzymywana żadna lista MRU.

##  <a name="m_bhelpmode"></a>  CWinApp::m_bHelpMode

PRAWDA, jeśli aplikacja działa w trybie kontekstu pomocy (Konwencja została wywołana z SHIFT + F1); w przeciwnym razie FALSE.

```
BOOL m_bHelpMode;
```

### <a name="remarks"></a>Uwagi

W trybie kontekstu pomocy kursor zostanie oznaczony jako znak zapytania, a użytkownik może przenieść go na ekran. Obejrzyj tę flagę, jeśli chcesz zaimplementować obsługę specjalną w trybie pomocy. `m_bHelpMode`jest publiczną zmienną typu BOOL.

##  <a name="m_dwrestartmanagersupportflags"></a>CWinApp:: m_dwRestartManagerSupportFlags

Flagi określające sposób zachowania Menedżera ponownego uruchamiania.

```
DWORD m_dwRestartManagerSupportFlags;
```

### <a name="remarks"></a>Uwagi

Aby włączyć Menedżera ponownego uruchamiania, ustaw `m_dwRestartManagerSupportFlags` odpowiednie zachowanie. W poniższej tabeli przedstawiono dostępne flagi.

|||
|-|-|
|Flaga|Opis|
|AFX_RESTART_MANAGER_SUPPORT_RESTART|Aplikacja jest zarejestrowana przy użyciu [CWinApp:: RegisterWithRestartManager](#registerwithrestartmanager). Menedżer ponownego uruchamiania jest odpowiedzialny za ponowne uruchomienie aplikacji, jeśli zakończył się nieoczekiwanie.|
|- AFX_RESTART_MANAGER_SUPPORT_RECOVERY|Aplikacja jest zarejestrowana za pomocą Menedżera ponownego uruchamiania, a Menedżer ponownego uruchamiania wywołuje funkcję wywołania zwrotnego odzyskiwania po ponownym uruchomieniu aplikacji. Domyślna funkcja wywołania zwrotnego odzyskiwania to [CWinApp:: ApplicationRecoveryCallback](#applicationrecoverycallback).|
|- AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART|Funkcja automatycznego zapisywania jest włączona, a Menedżer ponownego uruchamiania automatycznie zapisuje wszystkie otwarte dokumenty po ponownym uruchomieniu aplikacji.|
|- AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL|Funkcja Autozapisu jest włączona, a Menedżer ponownego uruchamiania automatycznie zapisuje wszystkie otwarte dokumenty w regularnych odstępach czasu. Interwał jest definiowany przez [CWinApp:: m_nAutosaveInterval](#m_nautosaveinterval).|
|- AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES|Menedżer ponownego uruchamiania otwiera wcześniej otwarte dokumenty po ponownym uruchomieniu aplikacji z nieoczekiwanego zamknięcia. [Klasa CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md) obsługuje przechowywanie listy otwartych dokumentów i ich przywracanie.|
|- AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES|Menedżer ponownego uruchamiania monituje użytkownika o przywrócenie automatycznie zapisywanych plików po ponownym uruchomieniu aplikacji. `CDataRecoveryHandler` Klasa wysyła zapytanie do użytkownika.|
|- AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE|Unia AFX_RESTART_MANAGER_SUPPORT_RESTART, AFX_RESTART_MANAGER_SUPPORT_RECOVER i AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES.|
|- AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS|Unia AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART, AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL i AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|
|- AFX_RESTART_MANAGER_SUPPORT_RESTART_ASPECTS|Unia AFX_RESTART_MANAGER_SUPPORT_RESTART, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES i AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|
|- AFX_RESTART_MANAGER_SUPPORT_RECOVERY_ASPECTS|Unia ofAFX_RESTART_MANAGER_SUPPORT_RECOVERY, AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES i AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|

##  <a name="m_ehelptype"></a>  CWinApp::m_eHelpType

Typ tego elementu członkowskiego danych jest typem wyliczanym AFX_HELP_TYPE, który jest zdefiniowany w `CWinApp` klasie.

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

- Aby ustawić pomoc dotyczącą HTML aplikacji, wywołaj polecenie [](#sethelpmode) sethelpmode i określ `afxHTMLHelp`.

- Aby ustawić pomoc aplikacji na polecenie WinHelp, wywołaj `SetHelpMode` i określ `afxWinHelp`.

##  <a name="m_hinstance"></a>CWinApp:: m_hInstance

Odnosi się do parametru *HINSTANCE* przesyłanego przez system `WinMain`Windows do.

```
HINSTANCE m_hInstance;
```

### <a name="remarks"></a>Uwagi

Element `m_hInstance` członkowski danych jest dojściem do bieżącego wystąpienia aplikacji uruchomionej w systemie Windows. Jest on zwracany przez funkcję globalną [AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle). `m_hInstance`jest publiczną zmienną typu HINSTANCE.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#55](../../mfc/reference/codesnippet/cpp/cwinapp-class_15.cpp)]

##  <a name="m_lpcmdline"></a>CWinApp:: m_lpCmdLine

Odnosi się do parametru *lpCmdLine* przesyłanego przez system `WinMain`Windows do.

```
LPTSTR m_lpCmdLine;
```

### <a name="remarks"></a>Uwagi

Wskazuje ciąg zakończony znakiem null, który określa wiersz polecenia dla aplikacji. Służy `m_lpCmdLine` do uzyskiwania dostępu do dowolnych argumentów wiersza polecenia wprowadzonych przez użytkownika podczas uruchamiania aplikacji. `m_lpCmdLine`jest publiczną zmienną typu LPTSTR.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

##  <a name="m_nautosaveinterval"></a>CWinApp:: m_nAutosaveInterval

Długość czasu (w milisekundach) między autozapisami.

```
int m_nAutosaveInterval;
```

### <a name="remarks"></a>Uwagi

Można skonfigurować Menedżera ponownego uruchamiania w celu automatycznego zapisywania otwartych dokumentów w ustalonych odstępach czasu. Jeśli aplikacja nie powoduje automatycznego zapisywania plików, ten parametr nie ma żadnego wpływu.

##  <a name="m_ncmdshow"></a>CWinApp:: m_nCmdShow

Odnosi się do parametru *nCmdShow* przesyłanego przez system `WinMain`Windows do.

```
int m_nCmdShow;
```

### <a name="remarks"></a>Uwagi

Należy przekazać `m_nCmdShow` jako argument w przypadku wywołania [CWnd:: funkcja ShowWindow](../../mfc/reference/cwnd-class.md#showwindow) dla głównego okna aplikacji. `m_nCmdShow`jest publiczną zmienną typu **int**.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#56](../../mfc/reference/codesnippet/cpp/cwinapp-class_17.cpp)]

##  <a name="m_pactivewnd"></a>  CWinApp::m_pActiveWnd

Za pomocą tego elementu członkowskiego danych można przechowywać wskaźnik do głównego okna aplikacji kontenera OLE, które ma aktywowaną aplikację serwera OLE.

### <a name="remarks"></a>Uwagi

Jeśli ten element członkowski danych ma wartość NULL, aplikacja nie jest aktywna.

Struktura ustawia tę zmienną elementu członkowskiego, gdy okno ramki jest aktywowane w miejscu przez aplikację kontenera OLE.

##  <a name="m_pdatarecoveryhandler"></a>  CWinApp::m_pDataRecoveryHandler

Wskaźnik do programu obsługi odzyskiwania danych dla aplikacji.

```
CDataRecoveryHandler* m_pDataRecoveryHandler;
```

### <a name="remarks"></a>Uwagi

Procedura obsługi odzyskiwania danych aplikacji monitoruje otwarte dokumenty i automatycznie zapisuje je. Struktura używa programu obsługi odzyskiwania danych do przywracania automatycznie zapisywanych plików, gdy aplikacja zostanie ponownie uruchomiona po nieoczekiwanym zamknięciu. Aby uzyskać więcej informacji, zobacz [Klasa CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md).

##  <a name="m_pszappname"></a>  CWinApp::m_pszAppName

Określa nazwę aplikacji.

```
LPCTSTR m_pszAppName;
```

### <a name="remarks"></a>Uwagi

Nazwa aplikacji może pochodzić z parametru przesłanego do konstruktora [CWinApp](#cwinapp) lub, jeśli nie zostanie określony, do ciągu zasobu o identyfikatorze AFX_IDS_APP_TITLE. Jeśli nazwa aplikacji nie zostanie znaleziona w zasobie, pochodzi ona z programu. Nazwa pliku EXE.

Zwrócone przez funkcję globalną [AfxGetAppName](application-information-and-management.md#afxgetappname). `m_pszAppName`jest publiczną zmienną typu **const char**<strong>\*</strong>.

> [!NOTE]
> Jeśli przypiszesz wartość do `m_pszAppName`, musi ona być przydzielana dynamicznie na stercie. Destruktor wywołuje Free () z tym wskaźnikiem. `CWinApp` Wiele chce użyć `_tcsdup`funkcji biblioteki wykonawczej () w celu wykonania przydziału. Ponadto zwolnij pamięć skojarzoną z bieżącym wskaźnikiem przed przypisaniem nowej wartości. Na przykład:

[!code-cpp[NVC_MFCWindowing#57](../../mfc/reference/codesnippet/cpp/cwinapp-class_18.cpp)]

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#65](../../mfc/reference/codesnippet/cpp/cwinapp-class_19.cpp)]

##  <a name="m_pszexename"></a>  CWinApp::m_pszExeName

Zawiera nazwę pliku wykonywalnego aplikacji bez rozszerzenia.

```
LPCTSTR m_pszExeName;
```

### <a name="remarks"></a>Uwagi

W przeciwieństwie do [m_pszAppName](#m_pszappname), ta nazwa nie może zawierać pustych wartości. `m_pszExeName`jest publiczną zmienną typu **const char**<strong>\*</strong>.

> [!NOTE]
> Jeśli przypiszesz wartość do `m_pszExeName`, musi ona być przydzielana dynamicznie na stercie. Destruktor wywołuje Free () z tym wskaźnikiem. `CWinApp` Wiele chce użyć `_tcsdup`funkcji biblioteki wykonawczej () w celu wykonania przydziału. Ponadto zwolnij pamięć skojarzoną z bieżącym wskaźnikiem przed przypisaniem nowej wartości. Na przykład:

[!code-cpp[NVC_MFCWindowing#58](../../mfc/reference/codesnippet/cpp/cwinapp-class_20.cpp)]

##  <a name="m_pszhelpfilepath"></a>  CWinApp::m_pszHelpFilePath

Zawiera ścieżkę do pliku pomocy aplikacji.

```
LPCTSTR m_pszHelpFilePath;
```

### <a name="remarks"></a>Uwagi

Domyślnie struktura inicjuje `m_pszHelpFilePath` się nazwą aplikacji z ". HLP "dołączone. Aby zmienić nazwę pliku pomocy, ustaw wartość `m_pszHelpFilePath` na ciąg, który zawiera pełną nazwę żądanego pliku pomocy. Dogodnym miejscem do wykonania jest funkcja [InitInstance](#initinstance) aplikacji. `m_pszHelpFilePath`jest publiczną zmienną typu **const char**<strong>\*</strong>.

> [!NOTE]
> Jeśli przypiszesz wartość do `m_pszHelpFilePath`, musi ona być przydzielana dynamicznie na stercie. Destruktor wywołuje Free () z tym wskaźnikiem. `CWinApp` Wiele chce użyć `_tcsdup`funkcji biblioteki wykonawczej () w celu wykonania przydziału. Ponadto zwolnij pamięć skojarzoną z bieżącym wskaźnikiem przed przypisaniem nowej wartości. Na przykład:

[!code-cpp[NVC_MFCWindowing#59](../../mfc/reference/codesnippet/cpp/cwinapp-class_21.cpp)]

##  <a name="m_pszprofilename"></a>  CWinApp::m_pszProfileName

Zawiera nazwę aplikacji. Plik INI.

```
LPCTSTR m_pszProfileName;
```

### <a name="remarks"></a>Uwagi

`m_pszProfileName`jest publiczną zmienną typu **const char**<strong>\*</strong>.

> [!NOTE]
> Jeśli przypiszesz wartość do `m_pszProfileName`, musi ona być przydzielana dynamicznie na stercie. Destruktor wywołuje Free () z tym wskaźnikiem. `CWinApp` Wiele chce użyć `_tcsdup`funkcji biblioteki wykonawczej () w celu wykonania przydziału. Ponadto zwolnij pamięć skojarzoną z bieżącym wskaźnikiem przed przypisaniem nowej wartości. Na przykład:

[!code-cpp[NVC_MFCWindowing#60](../../mfc/reference/codesnippet/cpp/cwinapp-class_22.cpp)]

##  <a name="m_pszregistrykey"></a>  CWinApp::m_pszRegistryKey

Służy do określenia, gdzie w rejestrze lub pliku INI są przechowywane ustawienia profilu aplikacji.

```
LPCTSTR m_pszRegistryKey;
```

### <a name="remarks"></a>Uwagi

Zwykle ten element członkowski danych jest traktowany jako tylko do odczytu.

- Wartość jest przechowywana w kluczu rejestru. Nazwa ustawienia profilu aplikacji jest dołączana do następującego klucza rejestru: HKEY_CURRENT_USER/Software/LocalAppWizard — Wygenerowano/.

Jeśli przypiszesz wartość do `m_pszRegistryKey`, musi ona być przydzielana dynamicznie na stercie. Destruktor wywołuje Free () z tym wskaźnikiem. `CWinApp` Wiele chce użyć `_tcsdup`funkcji biblioteki wykonawczej () w celu wykonania przydziału. Ponadto zwolnij pamięć skojarzoną z bieżącym wskaźnikiem przed przypisaniem nowej wartości. Na przykład:

[!code-cpp[NVC_MFCWindowing#61](../../mfc/reference/codesnippet/cpp/cwinapp-class_23.cpp)]

##  <a name="m_pszappid"></a>  CWinApp::m_pszAppID

Identyfikator modelu użytkownika aplikacji.

```
LPCTSTR m_pszAppID;
```

### <a name="remarks"></a>Uwagi

##  <a name="oncontexthelp"></a>CWinApp:: OnContextHelp

Obsługuje pomoc dotyczącą SHIFT + F1 w aplikacji.

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>Uwagi

Należy dodać `ON_COMMAND( ID_CONTEXT_HELP, OnContextHelp )` instrukcję `CWinApp` do mapy komunikatów klasy, a także dodać wpis tabeli akceleratora, zazwyczaj Shift + F1, aby włączyć tę funkcję elementu członkowskiego.

`OnContextHelp`umieszcza aplikację w trybie pomocy. Kursor zmieni się w strzałkę i znak zapytania, a użytkownik będzie mógł przenieść wskaźnik myszy i nacisnąć lewy przycisk myszy, aby zaznaczyć okno dialogowe, okno, menu lub przycisk polecenia. Ta funkcja członkowska Pobiera kontekst pomocy obiektu pod kursorem i wywołuje funkcję systemu Windows WinHelp z tym kontekstem pomocy.

##  <a name="onddecommand"></a>CWinApp:: OnDDECommand

Wywoływane przez platformę, gdy okno głównej ramki odbiera komunikat wykonania DDE.

```
virtual BOOL OnDDECommand(LPTSTR lpszCommand);
```

### <a name="parameters"></a>Parametry

*lpszCommand*<br/>
Wskazuje ciąg polecenia DDE otrzymany przez aplikację.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli polecenie jest obsługiwane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja sprawdza, czy polecenie jest żądaniem otwarcia dokumentu, a jeśli tak, otwiera określony dokument. Menedżer plików systemu Windows zazwyczaj wysyła takie ciągi poleceń DDE, gdy użytkownik kliknie dwukrotnie plik danych. Przesłoń tę funkcję, aby obsłużyć inne polecenia wykonywania DDE, takie jak polecenie drukowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#48](../../mfc/reference/codesnippet/cpp/cwinapp-class_24.cpp)]

##  <a name="onfilenew"></a>CWinApp:: OnFileNew

Implementuje polecenie ID_FILE_NEW.

```
afx_msg void OnFileNew();
```

### <a name="remarks"></a>Uwagi

Należy dodać `ON_COMMAND( ID_FILE_NEW, OnFileNew )` instrukcję `CWinApp` do mapy komunikatów klasy, aby włączyć tę funkcję elementu członkowskiego. W przypadku włączenia tej funkcji Ta funkcja obsługuje wykonywanie polecenia nowy plik.

Zapoznaj się z [uwagą techniczną 22](../../mfc/tn022-standard-commands-implementation.md) , aby uzyskać informacje dotyczące domyślnego zachowania i wskazówki dotyczące przesłonięcia tej funkcji elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

##  <a name="onfileopen"></a>  CWinApp::OnFileOpen

Implementuje polecenie ID_FILE_OPEN.

```
afx_msg void OnFileOpen();
```

### <a name="remarks"></a>Uwagi

Należy dodać `ON_COMMAND( ID_FILE_OPEN, OnFileOpen )` instrukcję `CWinApp` do mapy komunikatów klasy, aby włączyć tę funkcję elementu członkowskiego. W przypadku włączenia tej funkcji Ta funkcja obsługuje wykonywanie polecenia Otwórz plik.

Aby uzyskać informacje dotyczące domyślnego zachowania i wskazówek dotyczących sposobu przesłaniania tej funkcji elementu członkowskiego, zobacz [Uwagi techniczne 22](../../mfc/tn022-standard-commands-implementation.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

##  <a name="onfileprintsetup"></a>  CWinApp::OnFilePrintSetup

Implementuje polecenie ID_FILE_PRINT_SETUP.

```
afx_msg void OnFilePrintSetup();
```

### <a name="remarks"></a>Uwagi

Należy dodać `ON_COMMAND( ID_FILE_PRINT_SETUP, OnFilePrintSetup )` instrukcję `CWinApp` do mapy komunikatów klasy, aby włączyć tę funkcję elementu członkowskiego. W przypadku włączenia tej funkcji Ta funkcja obsługuje wykonywanie polecenia plik Print.

Aby uzyskać informacje dotyczące domyślnego zachowania i wskazówek dotyczących sposobu przesłaniania tej funkcji elementu członkowskiego, zobacz [Uwagi techniczne 22](../../mfc/tn022-standard-commands-implementation.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

##  <a name="onhelp"></a>CWinApp:: OnHelp

Obsługuje Pomoc F1 w aplikacji (przy użyciu bieżącego kontekstu).

```
afx_msg void OnHelp();
```

### <a name="remarks"></a>Uwagi

Zwykle do klawisza F1 zostanie również dodany wpis klawisza skrótu. Włączenie klawisza F1 jest tylko Konwencją, a nie wymaganiem.

Należy dodać `ON_COMMAND( ID_HELP, OnHelp )` instrukcję `CWinApp` do mapy komunikatów klasy, aby włączyć tę funkcję elementu członkowskiego. Jeśli jest włączona, wywoływana przez platformę, gdy użytkownik naciśnie klawisz F1.

Domyślna implementacja tej funkcji obsługi komunikatów określa kontekst pomocy, który odnosi się do bieżącego okna, okna dialogowego lub elementu menu, a następnie wywołuje funkcję WINHELP. EXE. Jeśli żaden kontekst nie jest obecnie dostępny, funkcja używa kontekstu domyślnego.

Przesłoń tę funkcję elementu członkowskiego, aby ustawić kontekst pomocy na coś innego niż okno, okno dialogowe, element menu lub przycisk paska narzędzi, który aktualnie ma fokus. Wywołaj `WinHelp` z żądanym identyfikatorem kontekstu pomocy.

##  <a name="onhelpfinder"></a>CWinApp:: OnHelpFinder

Obsługuje polecenia ID_HELP_FINDER i ID_DEFAULT_HELP.

```
afx_msg void OnHelpFinder();
```

### <a name="remarks"></a>Uwagi

Należy dodać `ON_COMMAND( ID_HELP_FINDER, OnHelpFinder )` instrukcję `CWinApp` do mapy komunikatów klasy, aby włączyć tę funkcję elementu członkowskiego. Jeśli ta funkcja jest włączona, platforma wywołuje tę funkcję obsługi komunikatów, gdy użytkownik aplikacji wybierze polecenie help Finder do wywołania `WinHelp` przy użyciu standardowego tematu **HELP_FINDER** .

##  <a name="onhelpindex"></a>CWinApp:: OnHelpIndex

Obsługuje polecenie ID_HELP_INDEX i udostępnia domyślny temat pomocy.

```
afx_msg void OnHelpIndex();
```

### <a name="remarks"></a>Uwagi

Należy dodać `ON_COMMAND( ID_HELP_INDEX, OnHelpIndex )` instrukcję `CWinApp` do mapy komunikatów klasy, aby włączyć tę funkcję elementu członkowskiego. Jeśli ta funkcja jest włączona, platforma wywołuje tę funkcję obsługi komunikatów, gdy użytkownik aplikacji wybierze polecenie indeks pomocy do wywołania `WinHelp` w standardowym temacie **HELP_INDEX** .

##  <a name="onhelpusing"></a>CWinApp:: OnHelpUsing

Obsługuje polecenie ID_HELP_USING.

```
afx_msg void OnHelpUsing();
```

### <a name="remarks"></a>Uwagi

Należy dodać `ON_COMMAND( ID_HELP_USING, OnHelpUsing )` instrukcję `CWinApp` do mapy komunikatów klasy, aby włączyć tę funkcję elementu członkowskiego. Struktura wywołuje tę funkcję obsługi komunikatów, gdy użytkownik aplikacji wybierze pomoc przy użyciu polecenia do wywołania `WinHelp` aplikacji za pomocą standardowego tematu **HELP_HELPONHELP** .

##  <a name="onidle"></a>CWinApp:: OnIdle

Przesłoń tę funkcję elementu członkowskiego, aby przeprowadzić przetwarzanie w czasie bezczynności.

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>Parametry

*lCount*<br/>
Licznik `OnIdle` jest zwiększany każdorazowo, gdy kolejka komunikatów aplikacji jest pusta. Ta liczba jest resetowana do wartości 0 za każdym razem, gdy nowy komunikat jest przetwarzany. Można użyć parametru *lCount* , aby określić względną długość czasu bezczynności aplikacji bez przetwarzania komunikatu.

### <a name="return-value"></a>Wartość zwracana

Różna od zera, aby uzyskać więcej czasu bezczynności przetwarzania; 0, jeśli nie jest wymagany więcej czasu bezczynności.

### <a name="remarks"></a>Uwagi

`OnIdle`jest wywoływana w domyślnej pętli komunikatów, gdy kolejka komunikatów aplikacji jest pusta. Użyj zastąpień do wywołania własnych zadań programu obsługi bezczynności w tle.

`OnIdle`powinien zwrócić wartość 0, aby wskazać, że nie jest wymagany czas przetwarzania bezczynności. Wartość parametru *lCount* jest zwiększana każdorazowo `OnIdle` , gdy kolejka komunikatów jest pusta i zostanie zresetowana do wartości 0 za każdym razem, gdy zostanie przetworzony nowy komunikat. Możesz wywoływać różne procedury bezczynności w oparciu o tę liczbę.

Poniżej przedstawiono podsumowanie przetwarzania pętli bezczynności:

1. Jeśli pętla komunikatów w Biblioteka MFC sprawdza kolejkę komunikatów i nie znajduje żadnych oczekujących komunikatów, wywołuje `OnIdle` obiekt aplikacji i dostarcza 0 jako argument *lCount* .

2. `OnIdle`wykonuje kilka operacji przetwarzania i zwraca wartość różną od zera, aby wskazać, że należy ją ponownie wywołać, aby przeprowadzić dalsze przetwarzanie.

3. Pętla komunikatów ponownie sprawdza kolejkę komunikatów. Jeśli żadne komunikaty nie są w stanie oczekiwania `OnIdle` , nastąpi ponowne wywołanie, zwiększając wartość argumentu *lCount* .

4. Ostatecznie program `OnIdle` zakończy przetwarzanie wszystkich zadań bezczynności i zwróci wartość 0. Powoduje to, że pętla komunikatów zostanie `OnIdle` zatrzymana do momentu odebrania następnego komunikatu z kolejki komunikatów, co oznacza, że cykl bezczynności zostanie uruchomiony ponownie z argumentem ustawionym na 0.

Nie wykonuj zadań w czasie `OnIdle` , ponieważ aplikacja nie może przetwarzać danych wejściowych użytkownika do momentu `OnIdle` powracania.

> [!NOTE]
> Domyślna implementacja programu `OnIdle` Updates obiektów interfejsu użytkownika, takich jak elementy menu i przyciski paska narzędzi, i wykonuje oczyszczanie struktury danych wewnętrznych. W związku z tym, `OnIdle`w przypadku przesłonięcia, należy wywołać `CWinApp::OnIdle` z w przesłoniętej wersji. `lCount` Najpierw Wywołaj wszystkie nieczynne przetwarzanie klasy podstawowej (czyli do momentu, `OnIdle` gdy klasa bazowa zwróci wartość 0). Jeśli musisz wykonać pracę przed ukończeniem przetwarzania klas podstawowych, przejrzyj implementację klasy podstawowej, aby wybrać odpowiednie *lCount* , w których chcesz wykonać swoją pracę.

Jeśli użytkownik nie chce `OnIdle` być wywoływana za każdym razem, gdy komunikat zostanie pobrany z kolejki komunikatów, można zastąpić [CWinThreadIsIdleMessage](../../mfc/reference/cwinthread-class.md#isidlemessage). Jeśli aplikacja ustawił bardzo krótki czasomierz lub gdy system wysyła komunikat WM_SYSTIMER, `OnIdle` zostanie wywołany wielokrotnie i spadek wydajności.

### <a name="example"></a>Przykład

Poniższe dwa przykłady pokazują, jak korzystać `OnIdle`z programu. Pierwszy przykład przetwarza dwa bezczynne zadania przy użyciu argumentu *lCount* , aby określić priorytety zadań. Pierwsze zadanie ma wysoki priorytet i należy to zrobić, jeśli jest to możliwe. Drugie zadanie jest mniej ważne i powinno zostać wykonane tylko wtedy, gdy dane wejściowe użytkownika są długotrwałe. Zanotuj wywołanie do wersji `OnIdle`klasy podstawowej. Drugi przykład zarządza grupą bezczynnych zadań z różnymi priorytetami.

[!code-cpp[NVC_MFCWindowing#51](../../mfc/reference/codesnippet/cpp/cwinapp-class_27.cpp)]

##  <a name="opendocumentfile"></a>CWinApp:: OpenDocumentFile

Struktura wywołuje tę metodę, aby otworzyć nazwany plik [CDocument](../../mfc/reference/cdocument-class.md) dla aplikacji.

```
virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszFileName
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
podczas Nazwa pliku, który ma zostać otwarty.

*bAddToMRU*<br/>
podczas Wartość TRUE wskazuje, że dokument jest jednym z najnowszych plików; Wartość FALSE wskazuje, że dokument nie jest jednym z najnowszych plików.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu, `CDocument` Jeśli to się powiedzie; w przeciwnym razie wartość null.

### <a name="remarks"></a>Uwagi

Jeśli dokument o tej nazwie jest już otwarty, pierwsze okno ramki zawierające ten dokument będzie miało fokus. Jeśli aplikacja obsługuje wiele szablonów dokumentów, struktura używa rozszerzenia nazwy pliku, aby znaleźć odpowiedni szablon dokumentu, aby spróbować załadować dokument. Jeśli to się powiedzie, szablon dokumentu tworzy okno ramki i widok dla dokumentu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

##  <a name="parsecommandline"></a>CWinApp::P arseCommandLine

Wywołaj tę funkcję elementu członkowskiego, aby przeanalizować wiersz polecenia i wysłać parametry po jednym naraz do [CCommandLineInfo::P arseparam](../../mfc/reference/ccommandlineinfo-class.md#parseparam).

```
void ParseCommandLine(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>Parametry

*rCmdInfo*<br/>
Odwołanie do obiektu [CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md) .

### <a name="remarks"></a>Uwagi

Po rozpoczęciu tworzenia nowego projektu MFC przy użyciu Kreatora aplikacji Kreator `CCommandLineInfo`aplikacji utworzy wystąpienie lokalne, a następnie wywoła `ProcessShellCommand` i `ParseCommandLine` w funkcji składowej [InitInstance](#initinstance) . Wiersz polecenia jest zgodny z trasą opisaną poniżej:

1. Po utworzeniu w programie `InitInstance` `CCommandLineInfo` obiekt jest przesyłany do `ParseCommandLine`.

2. `ParseCommandLine`następnie wywołuje `CCommandLineInfo::ParseParam` się wielokrotnie, raz dla każdego parametru.

3. `ParseParam`wypełnia obiekt, który następnie jest przenoszona do [elemencie ProcessShellCommand.](#processshellcommand) `CCommandLineInfo`

4. `ProcessShellCommand`obsługuje argumenty wiersza polecenia i flagi.

Należy pamiętać, że można `ParseCommandLine` wywołać bezpośrednio w razie konieczności.

Aby uzyskać opis flag wiersza polecenia, zobacz [CCommandLineInfo:: m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand).

##  <a name="pretranslatemessage"></a>CWinApp::P reTranslateMessage

Przesłoń tę funkcję w celu filtrowania komunikatów okna przed wysłaniem ich do funkcji systemu Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) domyślną implementację Wykonuje translację klawiszy akceleratora, dlatego należy wywołać `CWinApp::PreTranslateMessage`funkcja członkowska w zastąpionej wersji.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Wskaźnik do struktury [MSG](/windows/win32/api/winuser/ns-winuser-tagmsg) , która zawiera komunikat do przetworzenia.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli komunikat został w `PreTranslateMessage` pełni przetworzony i nie powinien być przetwarzany jeszcze. Zero, jeśli komunikat powinien być przetwarzany w normalny sposób.

##  <a name="processmessagefilter"></a>CWinApp::P rocessMessageFilter

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
Wskaźnik do trukturę Windows [MSG](/windows/win32/api/winuser/ns-winuser-msg).

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli komunikat jest przetwarzany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Funkcja Hook przetwarza zdarzenia przed wysłaniem ich do normalnego przetwarzania komunikatów aplikacji.

Jeśli zastąpisz tę funkcję zaawansowaną, pamiętaj, aby wywołać wersję klasy bazowej, aby zachować przetwarzanie punktu zaczepienia struktury.

##  <a name="processshellcommand"></a>CWinApp::P rocessShellCommand

Ta funkcja członkowska jest wywoływana przez [InitInstance](#initinstance) , aby akceptować parametry przesyłane `CCommandLineInfo` z obiektu identyfikowanego przez *rCmdInfo*i wykonywać wskazane działanie.

```
BOOL ProcessShellCommand(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>Parametry

*rCmdInfo*<br/>
Odwołanie do obiektu [CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md) .

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli polecenie powłoki zostało pomyślnie przetworzone. Jeśli 0, zwróć wartość FALSE z [InitInstance](#initinstance).

### <a name="remarks"></a>Uwagi

Po uruchomieniu nowego projektu MFC przy użyciu Kreatora aplikacji Kreator aplikacji utworzy lokalne `CCommandLineInfo`wystąpienie, a następnie Wywołaj `ProcessShellCommand` i [ParseCommandLine](#parsecommandline) w `InitInstance` funkcji składowej. Wiersz polecenia jest zgodny z trasą opisaną poniżej:

1. Po utworzeniu w programie `InitInstance` `CCommandLineInfo` obiekt jest przesyłany do `ParseCommandLine`.

2. `ParseCommandLine`następnie wielokrotnie wywołuje [CCommandLineInfo::P arseparam](../../mfc/reference/ccommandlineinfo-class.md#parseparam) dla każdego parametru.

3. `ParseParam`wypełnia obiekt, który jest następnie przekazywać do `ProcessShellCommand`. `CCommandLineInfo`

4. `ProcessShellCommand`obsługuje argumenty wiersza polecenia i flagi.

Elementy członkowskie `CCommandLineInfo` danych obiektu, identyfikowane przez [CCommandLineInfo:: m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand), mają następujący typ wyliczeniowy, który `CCommandLineInfo` jest zdefiniowany w klasie.

```
enum {
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE
    };
```

Aby uzyskać krótki opis każdej z tych wartości, zobacz `CCommandLineInfo::m_nShellCommand`.

##  <a name="processwndprocexception"></a>CWinApp::P rocessWndProcException

Struktura wywołuje tę funkcję elementu członkowskiego, gdy program obsługi nie przechwytuje wyjątku zgłoszonego w jednej z komunikatów aplikacji lub programów obsługi poleceń.

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*e*<br/>
Wskaźnik do nieprzechwyconego wyjątku.

*pMsg*<br/>
Komunikat [](/windows/win32/api/winuser/ns-winuser-msg)trukturę, który zawiera informacje o komunikacie systemu Windows, który spowodował wygenerowanie wyjątku przez strukturę.

### <a name="return-value"></a>Wartość zwracana

Wartość, która powinna zostać zwrócona do systemu Windows. Zwykle jest to 0L dla komunikatów systemu Windows, 1L (TRUE) dla komunikatów poleceń.

### <a name="remarks"></a>Uwagi

Nie wywołuj tej funkcji elementu członkowskiego bezpośrednio.

Domyślna implementacja tej funkcji elementu członkowskiego tworzy okno komunikatu. Jeśli nieprzechwycony wyjątek pochodzi z menu, paska narzędzi lub niepowodzenia polecenia akceleratora, w oknie komunikatu zostanie wyświetlony komunikat "polecenie nie powiodło się". w przeciwnym razie zostanie wyświetlony komunikat "wewnętrzny błąd aplikacji".

Przesłoń tę funkcję elementu członkowskiego, aby zapewnić globalną obsługę wyjątków. Wywołaj tylko podstawowe funkcje, jeśli chcesz, aby okno komunikatu było wyświetlane.

##  <a name="register"></a>CWinApp:: register

Wykonuje wszelkie zadania rejestracji, które nie `RegisterShellFileTypes`są obsługiwane przez program.

```
virtual BOOL Register();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe po powodzeniu; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja po prostu zwraca wartość TRUE. Zastąp tę funkcję, aby zapewnić wszelkie niestandardowe kroki rejestracji.

##  <a name="registershellfiletypes"></a>CWinApp:: RegisterShellFileTypes

Wywołaj tę funkcję elementu członkowskiego, aby zarejestrować wszystkie typy dokumentów aplikacji za pomocą Menedżera plików systemu Windows.

```
void RegisterShellFileTypes(BOOL bCompat = FALSE);
```

### <a name="parameters"></a>Parametry

*bCompat*<br/>
podczas Wartość TRUE powoduje dodanie wpisów rejestracji dla poleceń powłoki drukowania i drukowania, umożliwiając użytkownikowi drukowanie plików bezpośrednio z powłoki lub przeciąganie pliku do obiektu drukarki. Dodaje również klucz DefaultIcon. Domyślnie ten parametr ma wartość FALSE w celu zapewnienia zgodności z poprzednimi wersjami.

### <a name="remarks"></a>Uwagi

Pozwala to użytkownikowi na otwieranie pliku danych utworzonego przez aplikację przez dwukrotne kliknięcie go w Menedżerze plików. Wywołaj `RegisterShellFileTypes` po wywołaniu [AddDocTemplate](#adddoctemplate) dla każdego szablonu dokumentu w aplikacji. Wywołaj również funkcję elementu członkowskiego [EnableShellOpen](#enableshellopen) podczas `RegisterShellFileTypes`wywoływania.

`RegisterShellFileTypes`wykonuje iterację na liście obiektów [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) , które są obsługiwane przez aplikację i dla każdego szablonu dokumentu dodaje do bazy danych rejestracji wpisy, które przechowuje w systemie Windows dla skojarzeń plików. Menedżer plików używa tych wpisów, aby otworzyć plik danych po dwukrotnym kliknięciu go przez użytkownika. Eliminuje to potrzebę wysłania. Plik REG z aplikacją.

> [!NOTE]
> `RegisterShellFileTypes`działa tylko wtedy, gdy użytkownik uruchamia program z uprawnieniami administratora. Jeśli program nie ma uprawnień administratora, nie może zmienić kluczy rejestru.

Jeśli baza danych rejestracji już kojarzy dane rozszerzenie nazwy pliku z innym typem pliku, nowe skojarzenie nie zostanie utworzone. Zapoznaj się z klasą format ciągów niezbędnych do zarejestrowania tych informacji. `CDocTemplate`

##  <a name="registerwithrestartmanager"></a>CWinApp:: RegisterWithRestartManager

Rejestruje aplikację za pomocą Menedżera ponownego uruchamiania.

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
|*bRegisterRecoveryCallback*|podczas Wartość TRUE wskazuje, że to wystąpienie aplikacji używa funkcji wywołania zwrotnego odzyskiwania; Wartość FALSE wskazuje, że nie. Struktura wywołuje funkcję wywołania zwrotnego odzyskiwania po nieoczekiwanym zamknięciu aplikacji. Aby uzyskać więcej informacji, zobacz [CWinApp:: ApplicationRecoveryCallback](#applicationrecoverycallback).|
|*strRestartIdentifier*|podczas Unikatowy ciąg identyfikujący to wystąpienie Menedżera ponownego uruchamiania. Identyfikator Menedżera ponownego uruchamiania jest unikatowy dla każdego wystąpienia aplikacji.|
|*pwzCommandLineArgs*|podczas Ciąg, który zawiera dodatkowe argumenty z wiersza polecenia.|
|*dwRestartFlags*|podczas Opcjonalne flagi dla Menedżera ponownego uruchamiania. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.|
|*pRecoveryCallback*|podczas Funkcja wywołania zwrotnego odzyskiwania. Ta funkcja musi przyjmować parametr LPVOID jako dane wejściowe i zwracać wartość typu DWORD. Domyślna funkcja wywołania zwrotnego odzyskiwania `CWinApp::ApplicationRecoveryCallback`to.|
|*lpvParam*|podczas Parametr wejściowy funkcji wywołania zwrotnego odzyskiwania. Aby uzyskać więcej informacji, zobacz [CWinApp:: ApplicationRecoveryCallback](#applicationrecoverycallback).|
|*dwPingInterval*|podczas Czas oczekiwania przez Menedżera ponownego uruchomienia na zwrócenie przez funkcję wywołania zwrotnego odzyskiwania. Ten parametr jest w milisekundach.|
|*dwCallbackFlags*|podczas Flagi przechodzą do funkcji wywołania zwrotnego odzyskiwania. Zarezerwowane do użytku w przyszłości.|

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie kod błędu.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja używa domyślnej implementacji MFC do zapisywania plików, należy użyć prostej wersji programu `RegisterWithRestartManager`. Użyj wersji `RegisterWithRestartManager` złożonej, jeśli chcesz dostosować zachowanie automatycznego zapisywania aplikacji.

W przypadku wywołania tej metody z pustym ciągiem dla *strRestartIdentifier*, `RegisterWithRestartManager` program tworzy unikatowy ciąg identyfikatora dla tego wystąpienia Menedżera ponownego uruchamiania.

Gdy aplikacja zostanie nieoczekiwanie zakończona, Menedżer ponownego uruchamiania ponownie uruchamia aplikację z wiersza polecenia i zapewnia unikatowy identyfikator ponownego uruchomienia jako opcjonalny argument. W tym scenariuszu platforma wywołuje `RegisterWithRestartManager` dwa razy. Pierwsze wywołanie pochodzi z [CWinApp:: InitInstance](#initinstance) z pustym ciągiem dla identyfikatora ciągu. Następnie Metoda [CWinApp::P rocessshellcommand](#processshellcommand) wywołania `RegisterWithRestartManager` z unikatowym identyfikatorem ponownego uruchomienia.

Po zarejestrowaniu aplikacji za pomocą Menedżera ponownego uruchamiania Menedżer ponownego uruchamiania monitoruje aplikację. Jeśli aplikacja zostanie nieoczekiwanie zakończona, Menedżer ponownego uruchamiania wywoła funkcję wywołania zwrotnego odzyskiwania podczas procesu zamykania. Menedżer ponownego uruchamiania czeka na *dwPingInterval* odpowiedzi z funkcji wywołania zwrotnego odzyskiwania. Jeśli funkcja wywołania zwrotnego odzyskiwania nie odpowiada w tym czasie, aplikacja zakończy działanie bez wykonywania funkcji wywołania zwrotnego odzyskiwania.

Domyślnie dwRestartFlags nie są obsługiwane, ale są udostępniane do użytku w przyszłości. Możliwe wartości dla *dwRestartFlags* są następujące:

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

##  <a name="reopenpreviousfilesatrestart"></a>CWinApp:: ReopenPreviousFilesAtRestart

Określa, czy Menedżer ponownego uruchamiania ponownie otwiera pliki otwarte, gdy aplikacja nieoczekiwanie zakończyła pracę.

```
virtual BOOL ReopenPreviousFilesAtRestart() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE oznacza, że Menedżer ponownego uruchamiania ponownie otwiera poprzednio otwarte pliki; Wartość FALSE oznacza, że Menedżer ponownego uruchamiania nie jest.

##  <a name="restartinstance"></a>CWinApp:: RestartInstance

Obsługuje ponowne uruchomienie aplikacji zainicjowane przez Menedżera ponownego uruchamiania.

```
virtual BOOL CWinApp::RestartInstance();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli program obsługi odzyskiwania danych otwiera wcześniej otwarte dokumenty; Wartość FALSE, jeśli program obsługi odzyskiwania danych ma błąd lub jeśli nie ma wcześniej otwartych dokumentów.

### <a name="remarks"></a>Uwagi

Po ponownym uruchomieniu aplikacji przez Menedżera ponownego uruchamiania platforma wywołuje tę metodę. Ta metoda pobiera program obsługi odzyskiwania danych i przywraca automatycznie zapisane pliki. Ta metoda wywołuje [CDataRecoveryHandler:: RestoreAutosavedDocuments](../../mfc/reference/cdatarecoveryhandler-class.md#restoreautosaveddocuments) , aby określić, czy użytkownik chce przywrócić automatycznie zapisane pliki.

Ta metoda zwraca wartość FALSE, jeśli [CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md) ustali, że nie było otwartych dokumentów. Jeśli nie było otwartych dokumentów, aplikacja uruchamia się normalnie.

##  <a name="restoreautosavedfilesatrestart"></a>CWinApp:: RestoreAutosavedFilesAtRestart

Określa, czy Menedżer ponownego uruchamiania przywraca automatycznie zapisane pliki po ponownym uruchomieniu aplikacji.

```
virtual BOOL RestoreAutosavedFilesAtRestart() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE wskazuje, że Menedżer ponownego uruchamiania przywraca automatycznie zapisane pliki; Wartość FALSE oznacza, że Menedżer ponownego uruchamiania nie jest.

##  <a name="run"></a>CWinApp:: Run

Udostępnia domyślną pętlę komunikatów.

```
virtual int Run();
```

### <a name="return-value"></a>Wartość zwracana

Wartość **int** , która jest zwracana przez `WinMain`.

### <a name="remarks"></a>Uwagi

`Run`uzyskuje i wysyła komunikaty systemu Windows do momentu otrzymania przez aplikację komunikatu WM_QUIT. Jeśli kolejka komunikatów aplikacji nie zawiera obecnie żadnych komunikatów, `Run` wywołania [OnIdle](#onidle) w celu przeprowadzenia przetwarzania w czasie bezczynności. Komunikaty przychodzące przechodzą do funkcji składowej [PreTranslateMessage](#pretranslatemessage) na potrzeby przetwarzania specjalnego, a następnie do `TranslateMessage` funkcji systemu Windows dla standardowego tłumaczenia klawiatury; `DispatchMessage` na koniec wywoływana jest funkcja systemu Windows.

`Run`jest rzadko zastępowany, ale można go zastąpić, aby zapewnić specjalne zachowanie.

##  <a name="runautomated"></a>CWinApp:: RunAutomated

Wywołaj tę funkcję, aby określić, czy istnieje opcja " **/Automation.** " lub " **-Automation**", która wskazuje, czy aplikacja serwera została uruchomiona przez aplikację kliencką.

```
BOOL RunAutomated();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli opcja została znaleziona; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli jest obecny, opcja zostanie usunięta z wiersza polecenia. Aby uzyskać więcej informacji na temat automatyzacji OLE, zapoznaj się z artykułem [serwery automatyzacji](../../mfc/automation-servers.md).

##  <a name="runembedded"></a>CWinApp:: RunEmbedded

Wywołaj tę funkcję, aby określić, czy jest obecna opcja " **przełącznikiem/Embedding**" lub " **-osadzania**", która wskazuje, czy aplikacja serwera została uruchomiona przez aplikację kliencką.

```
BOOL RunEmbedded();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli opcja została znaleziona; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli jest obecny, opcja zostanie usunięta z wiersza polecenia. Aby uzyskać więcej informacji na temat osadzania, zobacz [artykuł serwery: Implementowanie serwera](../../mfc/servers-implementing-a-server.md).

##  <a name="saveallmodified"></a>CWinApp:: SaveAllModified

Wywoływane przez platformę, by zapisać wszystkie dokumenty, gdy okno głównej ramki aplikacji ma zostać zamknięte lub za pomocą komunikatu WM_QUERYENDSESSION.

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli chcesz bezpiecznie zakończyć działanie aplikacji; 0 Jeśli nie można bezpiecznie zakończyć aplikacji.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji składowej wywołuje funkcję członkowską [CDocument:: SaveModified](../../mfc/reference/cdocument-class.md#savemodified) z kolei dla wszystkich zmodyfikowanych dokumentów w aplikacji.

##  <a name="selectprinter"></a>CWinApp:: SelectPrinter

Wywołaj tę funkcję elementu członkowskiego, aby wybrać określoną drukarkę i Zwolnij drukarkę wcześniej wybraną w oknie dialogowym drukowania.

```
void SelectPrinter(
    HANDLE hDevNames,
    HANDLE hDevMode,
    BOOL bFreeOld = TRUE);
```

### <a name="parameters"></a>Parametry

*hDevNames*<br/>
Dojście do [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)trukturę, które identyfikuje sterownik, urządzenie i nazwy portów wyjściowych określonej drukarki.

*hDevMode*<br/>
Dojście do struktury [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) , które określa informacje o inicjacji i środowisku drukarki.

*bFreeOld*<br/>
Zwalnia wcześniej wybraną drukarkę.

### <a name="remarks"></a>Uwagi

Jeśli zarówno *hDevMode* , jak i *hDevNames* mają `SelectPrinter` wartość null, używa bieżącej drukarki domyślnej.

##  <a name="sethelpmode"></a>  CWinApp::SetHelpMode

Ustawia typ pomocy aplikacji.

```
void SetHelpMode(AFX_HELP_TYPE eHelpType);
```

### <a name="parameters"></a>Parametry

*eHelpType*<br/>
Określa typ pomocy, która ma być używana. Aby uzyskać więcej informacji, zobacz [CWinApp:: m_eHelpType](#m_ehelptype) .

### <a name="remarks"></a>Uwagi

Ustawia typ pomocy aplikacji.

Aby ustawić typ pomocy aplikacji na HTMLHelp, można wywołać [EnableHTMLHelp](#enablehtmlhelp). Po wywołaniu `EnableHTMLHelp`aplikacja musi używać HTMLHelp jako swojej aplikacji pomocy. Jeśli chcesz zmienić do korzystania z programu WinHelp, możesz wywołać `SetHelpMode` i ustawić *eHelpType* do. `afxWinHelp`

##  <a name="setregistrykey"></a>  CWinApp::SetRegistryKey

Powoduje, że ustawienia aplikacji mają być przechowywane w rejestrze, a nie w plikach INI.

```
void SetRegistryKey(LPCTSTR lpszRegistryKey);
void SetRegistryKey(UINT nIDRegistryKey);
```

### <a name="parameters"></a>Parametry

*lpszRegistryKey*<br/>
Wskaźnik na ciąg zawierający nazwę klucza.

*nIDRegistryKey*<br/>
Identyfikator zasobu ciągu zawierającego nazwę klucza rejestru.

### <a name="remarks"></a>Uwagi

Ta funkcja ustawia *m_pszRegistryKey* `GetProfileInt`, który jest następnie używany przez `CWinApp`funkcje członkowskie `GetProfileString`, `WriteProfileInt`, i `WriteProfileString` . Jeśli ta funkcja została wywołana, lista ostatnio używanych plików (MRU) jest również przechowywana w rejestrze. Klucz rejestru jest zwykle nazwą firmy. Jest on przechowywany w postaci klucza w następującej postaci: HKEY_CURRENT_USER\Software\\< nazwę\>firmy<\>nazwaaplikacji<\\Nazwa sekcji\><nazwa\>wartości.\\\\

##  <a name="supportsapplicationrecovery"></a>CWinApp:: SupportsApplicationRecovery

Określa, czy Menedżer ponownego uruchamiania odzyskuje aplikację, która nieoczekiwanie zakończyła pracę.

```
virtual BOOL SupportsApplicationRecovery() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE wskazuje, że Menedżer ponownego uruchamiania odzyska aplikację; Wartość FALSE oznacza, że Menedżer ponownego uruchamiania nie jest.

##  <a name="supportsautosaveatinterval"></a>CWinApp:: SupportsAutosaveAtInterval

Określa, czy Menedżer ponownego uruchamiania automatycznie zapisuje otwarte dokumenty w regularnych odstępach czasu.

```
virtual BOOL SupportsAutosaveAtInterval() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE oznacza, że Menedżer ponownego uruchamiania automatycznie zapisuje otwarte dokumenty; Wartość FALSE oznacza, że Menedżer ponownego uruchamiania nie jest.

##  <a name="supportsautosaveatrestart"></a>CWinApp:: SupportsAutosaveAtRestart

Określa, czy Menedżer ponownego uruchamiania automatycznie zapisuje wszystkie otwarte dokumenty po ponownym uruchomieniu aplikacji.

```
virtual BOOL SupportsAutosaveAtRestart() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE oznacza, że Menedżer ponownego uruchamiania automatycznie zapisuje otwarte dokumenty po ponownym uruchomieniu aplikacji; Wartość FALSE oznacza, że Menedżer ponownego uruchamiania nie jest.

##  <a name="supportsrestartmanager"></a>CWinApp:: SupportsRestartManager

Określa, czy aplikacja obsługuje Menedżera ponownego uruchamiania.

```
virtual BOOL SupportsRestartManager() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE oznacza, że aplikacja obsługuje Menedżera ponownego uruchamiania; Wartość FALSE oznacza, że aplikacja nie jest.

##  <a name="unregister"></a>CWinApp:: Unregister

Wyrejestrowuje wszystkie pliki zarejestrowane przez obiekt aplikacji.

```
virtual BOOL Unregister();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe po powodzeniu; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Funkcja cofa rejestrację wykonywaną przez obiekt aplikacji i funkcję register. [](#register) `Unregister` Zwykle obie funkcje są wywoływane niejawnie przez MFC i w związku z tym nie będą wyświetlane w kodzie.

Przesłoń tę funkcję, aby wykonać niestandardowe kroki wyrejestrowywania.

##  <a name="unregistershellfiletypes"></a>CWinApp:: UnregisterShellFileTypes

Wywołaj tę funkcję elementu członkowskiego, aby wyrejestrować wszystkie typy dokumentów aplikacji za pomocą Menedżera plików systemu Windows.

```
void UnregisterShellFileTypes();
```

##  <a name="winhelp"></a>CWinApp:: WinHelp

Wywołaj tę funkcję elementu członkowskiego, aby wywołać aplikację WinHelp.

```
virtual void WinHelp(
    DWORD_PTR dwData,
    UINT nCmd = HELP_CONTEXT);
```

### <a name="parameters"></a>Parametry

*dwData*<br/>
Określa dodatkowe dane. Używana wartość zależy od wartości parametru *nCmd* .

*nCmd*<br/>
Określa typ żądanej pomocy. Aby zapoznać się z listą możliwych wartości i wpływem na parametr *dwData* , zobacz Funkcja [WinHelp](/windows/win32/api/winuser/nf-winuser-winhelpw) systemu Windows.

### <a name="remarks"></a>Uwagi

Struktura wywołuje również tę funkcję, aby wywołać aplikację WinHelp.

Platforma automatycznie zamknie aplikację WinHelp, gdy aplikacja zostanie przerwana.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#53](../../mfc/reference/codesnippet/cpp/cwinapp-class_28.cpp)]

##  <a name="writeprofilebinary"></a>CWinApp:: WriteProfileBinary

Wywołaj tę funkcję elementu członkowskiego, aby zapisać dane binarne w określonej sekcji rejestru aplikacji lub. Plik INI.

```
BOOL WriteProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE pData,
    UINT nBytes);
```

### <a name="parameters"></a>Parametry

*lpszSection*<br/>
Wskazuje ciąg zakończony znakiem null, który określa sekcję zawierającą wpis. Jeśli sekcja nie istnieje, zostanie utworzona. Nazwa sekcji jest niezależna od wielkości liter; ciąg może zawierać dowolną kombinację wielkich i małych liter.

*lpszEntry*<br/>
Wskazuje ciąg zakończony znakiem null, który zawiera wpis, w którym ma zostać zapisywana wartość. Jeśli wpis nie istnieje w określonej sekcji, zostanie utworzony.

*pData*<br/>
Wskazuje dane, które mają być zapisywane.

*nBytes*<br/>
Zawiera liczbę bajtów do zapisania.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="example"></a>Przykład

W tym przykładzie `CWinApp* pApp = AfxGetApp();` użyto do uzyskania klasy CWinApp, `GetProfileBinary` która przedstawia sposób, który `WriteProfileBinary` może być używany z dowolnej funkcji w aplikacji MFC.

[!code-cpp[NVC_MFCWindowing#54](../../mfc/reference/codesnippet/cpp/cwinapp-class_29.cpp)]

Aby uzyskać inny przykład, zobacz przykład dla [CWinApp:: GetProfileBinary](#getprofilebinary).

##  <a name="writeprofileint"></a>CWinApp:: WriteProfileInt

Wywołaj tę funkcję elementu członkowskiego, aby zapisać określoną wartość w określonej sekcji rejestru aplikacji lub. Plik INI.

```
BOOL WriteProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nValue);
```

### <a name="parameters"></a>Parametry

*lpszSection*<br/>
Wskazuje ciąg zakończony znakiem null, który określa sekcję zawierającą wpis. Jeśli sekcja nie istnieje, zostanie utworzona. Nazwa sekcji jest niezależna od wielkości liter; ciąg może zawierać dowolną kombinację wielkich i małych liter.

*lpszEntry*<br/>
Wskazuje ciąg zakończony znakiem null, który zawiera wpis, w którym ma zostać zapisywana wartość. Jeśli wpis nie istnieje w określonej sekcji, zostanie utworzony.

*nWartość*<br/>
Zawiera wartość do zapisania.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="example"></a>Przykład

Ten przykład używa `CWinApp* pApp = AfxGetApp();` metody, aby uzyskać w klasie CWinApp ilustrujący, `GetProfileString` `WriteProfileString` `WriteProfileInt`że,, i `GetProfileInt` może być używany z dowolnej funkcji w aplikacji MFC.

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

Aby uzyskać inny przykład, zobacz przykład dla [CWinApp:: GetProfileInt](#getprofileint).

##  <a name="writeprofilestring"></a>CWinApp:: WriteProfileString

Wywołaj tę funkcję elementu członkowskiego, aby napisać określony ciąg w określonej sekcji rejestru aplikacji lub. Plik INI.

```
BOOL WriteProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszValue);
```

### <a name="parameters"></a>Parametry

*lpszSection*<br/>
Wskazuje ciąg zakończony znakiem null, który określa sekcję zawierającą wpis. Jeśli sekcja nie istnieje, zostanie utworzona. Nazwa sekcji jest niezależna od wielkości liter; ciąg może zawierać dowolną kombinację wielkich i małych liter.

*lpszEntry*<br/>
Wskazuje ciąg zakończony znakiem null, który zawiera wpis, w którym ma zostać zapisywana wartość. Jeśli wpis nie istnieje w określonej sekcji, zostanie utworzony. Jeśli ten parametr ma wartość NULL, sekcja określona przez *lpszSection* jest usuwana.

*lpszValue*<br/>
Wskazuje ciąg, który ma zostać zapisany. Jeśli ten parametr ma wartość NULL, wpis określony przez parametr *lpszEntry* jest usuwany.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

Aby uzyskać inny przykład, zobacz przykład dla [CWinApp:: GetProfileInt](#getprofileint).

##  <a name="setappid"></a>CWinApp:: setappid

Jawnie ustawia identyfikator modelu użytkownika aplikacji dla aplikacji. Ta metoda powinna być wywoływana przed wyświetleniem przez użytkownika interfejsu użytkownika (najlepszym miejscem jest Konstruktor aplikacji).

```
void SetAppID(LPCTSTR lpcszAppID);
```

### <a name="parameters"></a>Parametry

*lpcszAppID*<br/>
Określa identyfikator modelu użytkownika aplikacji.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Klasa CWinThread](../../mfc/reference/cwinthread-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Instrukcje: dodawanie obsługi menedżera ponownego uruchamiania](../../mfc/how-to-add-restart-manager-support.md)
