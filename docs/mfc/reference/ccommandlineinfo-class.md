---
title: Klasa CCommandLineInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCommandLineInfo
- AFXWIN/CCommandLineInfo
- AFXWIN/CCommandLineInfo::CCommandLineInfo
- AFXWIN/CCommandLineInfo::ParseParam
- AFXWIN/CCommandLineInfo::m_bRunAutomated
- AFXWIN/CCommandLineInfo::m_bRunEmbedded
- AFXWIN/CCommandLineInfo::m_bShowSplash
- AFXWIN/CCommandLineInfo::m_nShellCommand
- AFXWIN/CCommandLineInfo::m_strDriverName
- AFXWIN/CCommandLineInfo::m_strFileName
- AFXWIN/CCommandLineInfo::m_strPortName
- AFXWIN/CCommandLineInfo::m_strPrinterName
- AFXWIN/CCommandLineInfo::m_strRestartIdentifier
dev_langs:
- C++
helpviewer_keywords:
- CCommandLineInfo [MFC], CCommandLineInfo
- CCommandLineInfo [MFC], ParseParam
- CCommandLineInfo [MFC], m_bRunAutomated
- CCommandLineInfo [MFC], m_bRunEmbedded
- CCommandLineInfo [MFC], m_bShowSplash
- CCommandLineInfo [MFC], m_nShellCommand
- CCommandLineInfo [MFC], m_strDriverName
- CCommandLineInfo [MFC], m_strFileName
- CCommandLineInfo [MFC], m_strPortName
- CCommandLineInfo [MFC], m_strPrinterName
- CCommandLineInfo [MFC], m_strRestartIdentifier
ms.assetid: 3e313ddb-0a82-4991-87ac-a27feff4668c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d292c3f48f0a375fbd914cf287f1e8d2cef5c6c3
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952388"
---
# <a name="ccommandlineinfo-class"></a>Klasa CCommandLineInfo
Pomoc podczas analizy wiersza polecenia podczas uruchamiania aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CCommandLineInfo : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCommandLineInfo::CCommandLineInfo](#ccommandlineinfo)|Tworzy domyślny `CCommandLineInfo` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCommandLineInfo::ParseParam](#parseparam)|Zastąp to wywołanie zwrotne do analizy poszczególnych parametrów.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCommandLineInfo::m_bRunAutomated](#m_brunautomated)|Wskazuje wiersza polecenia `/Automation` znaleziono opcji.|  
|[CCommandLineInfo::m_bRunEmbedded](#m_brunembedded)|Wskazuje wiersza polecenia `/Embedding` znaleziono opcji.|  
|[CCommandLineInfo::m_bShowSplash](#m_bshowsplash)|Wskazuje, czy mają być wyświetlane ekranu powitalnego.|  
|[CCommandLineInfo::m_nShellCommand](#m_nshellcommand)|Wskazuje polecenia powłoki, aby można było przetworzyć.|  
|[CCommandLineInfo::m_strDriverName](#m_strdrivername)|Wskazuje sterownika nazwa polecenia powłoki jest drukowania; w przeciwnym razie wartość pusta.|  
|[CCommandLineInfo::m_strFileName](#m_strfilename)|Wskazuje nazwę pliku, który może być otwarty lub wydrukować; pusty w przypadku polecenia powłoki jest nowy lub DDE.|  
|[CCommandLineInfo::m_strPortName](#m_strportname)|Określa port nazwa polecenia powłoki jest drukowania; w przeciwnym razie wartość pusta.|  
|[CCommandLineInfo::m_strPrinterName](#m_strprintername)|Wskazuje drukarki nazwa polecenia powłoki jest drukowania; w przeciwnym razie wartość pusta.|  
|[CCommandLineInfo::m_strRestartIdentifier](#m_strrestartidentifier)|Wskazuje identyfikator unikatowy ponowne uruchomienie Menedżera ponownego uruchomienia, jeśli Menedżer ponownego uruchamiania ponownego uruchomienia aplikacji.|  
  
## <a name="remarks"></a>Uwagi  
 Aplikacji MFC zwykle utworzy lokalne wystąpienie tej klasy w [InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) funkcji jego obiektu aplikacji. Ten obiekt są następnie przekazywane do [CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline), które wywołuje wielokrotnie [ParseParam](#parseparam) do wypełnienia `CCommandLineInfo` obiektu. `CCommandLineInfo` Obiektu są następnie przekazywane do [CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand) do obsługi flagi i argumenty wiersza polecenia.  
  
 Ten obiekt umożliwia Hermetyzowanie poniższych opcji wiersza polecenia i parametry:  
  
|Argument wiersza polecenia|Polecenie wykonane|  
|----------------------------|----------------------|  
|*aplikacji*|Nowy plik.|  
|*Aplikacja* filename|Otwórz plik.|  
|*Aplikacja* `/p` filename|Plik wydruku do drukarki domyślnej.|  
|*Aplikacja* `/pt` portu sterownika drukarki filename|Drukowanie pliku do określonej drukarki.|  
|*aplikacji* `/dde`|Uruchom i poczekać na DDE polecenia.|  
|*aplikacji* `/Automation`|Uruchomiony jako serwer automatyzacji OLE.|  
|*aplikacji* `/Embedding`|Uruchamiać można edytować element osadzony OLE.|  
|*aplikacji* `/Register`<br /><br /> *aplikacji* `/Regserver`|Informuje o aplikacji do wykonywania wszystkich zadań rejestracji.|  
|*aplikacji* `/Unregister`<br /><br /> *aplikacji* `/Unregserver`|Informuje o aplikacji do wykonywania wszystkich zadań wyrejestrować.|  
  
 Klasa wyprowadzona z nowego `CCommandLineInfo` do obsługi inne flagi i wartości parametrów. Zastąpienie [ParseParam](#parseparam) do obsługi nowych flag.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CCommandLineInfo`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="ccommandlineinfo"></a>  CCommandLineInfo::CCommandLineInfo  
 Ten konstruktor tworzy `CCommandLineInfo` obiektu z wartościami domyślnymi.  
  
```  
CCommandLineInfo();
```  
  
### <a name="remarks"></a>Uwagi  
 Wartość domyślna to, aby wyświetlić ekran powitalny ( `m_bShowSplash=TRUE`) oraz uruchomić nowego polecenia menu Plik ( `m_nShellCommand` **= NewFile**).  
  
 Wywołania framework aplikacji [ParseParam](#parseparam) do wypełnienia elementy członkowskie danych tego obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#54](../../mfc/codesnippet/cpp/ccommandlineinfo-class_1.cpp)]  
  
##  <a name="m_brunautomated"></a>  CCommandLineInfo::m_bRunAutomated  
 Oznacza to, że `/Automation` flagi został znaleziony w wierszu polecenia.  
  
```  
BOOL m_bRunAutomated;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `TRUE`, oznacza to, że uruchamiania jako serwer automatyzacji OLE.  
  
##  <a name="m_brunembedded"></a>  CCommandLineInfo::m_bRunEmbedded  
 Oznacza to, że `/Embedding` flagi został znaleziony w wierszu polecenia.  
  
```  
BOOL m_bRunEmbedded;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `TRUE`, oznacza to, że uruchamiania dla edycji elementu OLE osadzonych.  
  
##  <a name="m_bshowsplash"></a>  CCommandLineInfo::m_bShowSplash  
 Wskazuje, że powinien być wyświetlany ekran powitalny.  
  
```  
BOOL m_bShowSplash;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `TRUE`, oznacza to, że ekran powitalny dla tej aplikacji powinien być wyświetlany podczas uruchamiania. Domyślna implementacja [ParseParam](#parseparam) ustawia ten element członkowski danych `TRUE` Jeśli [m_nShellCommand](#m_nshellcommand) jest równa `CCommandLineInfo::FileNew`.  
  
##  <a name="m_nshellcommand"></a>  CCommandLineInfo::m_nShellCommand  
 Wskazuje polecenia powłoki dla tego wystąpienia aplikacji.  
  
```  
m_nShellCommand;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ dla tego elementu członkowskiego danych jest następujący typ wyliczeniowy jest zdefiniowany w `CCommandLineInfo` klasy.  
  
```  
enum {  
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE,
    AppRegister,
    AppUnregister,
    RestartByRestartManager,
    FileNothing = -1  
    };  
```  
  
 Krótki opis tych wartości zobacz poniżej.  
  
- `CCommandLineInfo::FileNew` Wskazuje, że nie plik znaleziono nazwy w wierszu polecenia.  
  
- `CCommandLineInfo::FileOpen` Wskazuje, że nazwa pliku został znaleziony w wierszu polecenia i że z następujących flag nie znaleziono żadnych w wierszu polecenia: `/p`, `/pt`, `/dde`.  
  
- `CCommandLineInfo::FilePrint` Oznacza to, że `/p` flagi został znaleziony w wierszu polecenia.  
  
- `CCommandLineInfo::FilePrintTo` Oznacza to, że `/pt` flagi został znaleziony w wierszu polecenia.  
  
- `CCommandLineInfo::FileDDE` Oznacza to, że `/dde` flagi został znaleziony w wierszu polecenia.  
  
- `CCommandLineInfo::AppRegister` Oznacza to, że `/Register` lub `/Regserver` flagi został znaleziony w wierszu polecenia i aplikacji został poproszony o zarejestrować.  
  
- `CCommandLineInfo::AppUnregister` Oznacza to, że `/Unregister` lub `/Unregserver` aplikacji został poproszony o wyrejestrować.  
  
- `CCommandLineInfo::RestartByRestartManager` Wskazuje, że aplikacja została ponownie uruchomiona przez Menedżera ponownego uruchomienia.  
  
- `CCommandLineInfo::FileNothing` Wyłącza wyświetlanie nowe podrzędne okno MDI podczas uruchamiania. Zgodnie z projektem generowane przez Kreatora aplikacji MDI — aplikacje wyświetlane nowe okno podrzędne podczas uruchamiania. Aby wyłączyć tę funkcję, aplikacja może użyć `CCommandLineInfo::FileNothing` jako polecenia powłoki, gdy wywołuje [ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand). `ProcessShellCommand` Metoda jest wywoływana przez `InitInstance( )` wszystkich `CWinApp` klas pochodnych.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#55](../../mfc/codesnippet/cpp/ccommandlineinfo-class_2.cpp)]  
  
##  <a name="m_strdrivername"></a>  CCommandLineInfo::m_strDriverName  
 Przechowuje wartość trzeci parametr z systemem innym niż flagi w wierszu polecenia.  
  
```  
CString m_strDriverName;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ten parametr jest zazwyczaj nazwa sterownika drukarki dla polecenia powłoki do drukowania. Domyślna implementacja [ParseParam](#parseparam) ustawia tego danych elementu członkowskiego tylko wtedy, gdy `/pt` flagi został znaleziony w wierszu polecenia.  
  
##  <a name="m_strfilename"></a>  CCommandLineInfo::m_strFileName  
 Przechowuje wartość pierwszego parametru z systemem innym niż flagi w wierszu polecenia.  
  
```  
CString m_strFileName;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ten parametr jest zazwyczaj nazwę pliku, aby otworzyć.  
  
##  <a name="m_strportname"></a>  CCommandLineInfo::m_strPortName  
 Przechowuje wartość czwartego parametru z systemem innym niż flagi w wierszu polecenia.  
  
```  
CString m_strPortName;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ten parametr jest zazwyczaj nazwa portu drukarki dla polecenia powłoki do drukowania. Domyślna implementacja [ParseParam](#parseparam) ustawia tego danych elementu członkowskiego tylko wtedy, gdy `/pt` flagi został znaleziony w wierszu polecenia.  
  
##  <a name="m_strprintername"></a>  CCommandLineInfo::m_strPrinterName  
 Przechowuje wartość drugiego parametru z systemem innym niż flagi w wierszu polecenia.  
  
```  
CString m_strPrinterName;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ten parametr jest zazwyczaj nazwę polecenia powłoki drukowania do drukarki. Domyślna implementacja [ParseParam](#parseparam) ustawia tego danych elementu członkowskiego tylko wtedy, gdy `/pt` flagi został znaleziony w wierszu polecenia.  
  
##  <a name="m_strrestartidentifier"></a>  CCommandLineInfo::m_strRestartIdentifier  
 Unikatowy ponownie identyfikator w wierszu polecenia.  
  
```  
CString m_strRestartIdentifier;  
```  
  
### <a name="remarks"></a>Uwagi  
 Identyfikator ponowne uruchomienie jest unikatowy dla każdego wystąpienia aplikacji.  
  
 Menedżer ponownego uruchamiania zamyka aplikację, jest skonfigurowany, aby uruchomić ponownie Menedżer ponownego uruchamiania wykonuje aplikacji z poziomu wiersza polecenia o identyfikatorze ponownego uruchomienia jako parametr opcjonalny. Po ponownym uruchomieniu Menedżera używa identyfikatora ponownego uruchomienia, aplikację można ponownie otworzyć wcześniej otwartych dokumentów i odzyskiwanie plików automatycznie zapisany.  
  
##  <a name="parseparam"></a>  CCommandLineInfo::ParseParam  
 Struktura wywołuje tej funkcji do analizy/interpretacji poszczególnych parametrów wiersza polecenia. Druga wersja różni się od pierwszego wyłącznie w projektach Unicode.  
  
```  
virtual void ParseParam(
    const char* pszParam,  
    BOOL bFlag,  
    BOOL bLast);

 
virtual void ParseParam(
    const TCHAR* pszParam,  
    BOOL bFlag,  
    BOOL bLast);
```  
  
### <a name="parameters"></a>Parametry  
 *pszParam*  
 Parametr lub flagi.  
  
 *bFlag*  
 Wskazuje, czy *pszParam* jest parametr lub flagę.  
  
 *Wielkich*  
 Wskazuje, czy to jest ostatni parametr lub flagi w wierszu polecenia.  
  
### <a name="remarks"></a>Uwagi  
 [CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline) wywołania `ParseParam` raz dla każdego parametru lub flagi w wierszu polecenia, przekazywanie argument *pszParam*. Jeśli pierwszy znak w parametrze " **-**"lub " **/**", a następnie jest usuwany i *bFlag* ma ustawioną wartość `TRUE`. Podczas analizowania ostatni parametr *wielkich* ma ustawioną wartość `TRUE`.  
  
 Domyślna implementacja tej funkcji rozpoznaje następujące flagi: `/p`, `/pt`, `/dde`, `/Automation`, i `/Embedding`, jak pokazano w poniższej tabeli:  
  
|Argument wiersza polecenia|Polecenie wykonane|  
|----------------------------|----------------------|  
|*aplikacji*|Nowy plik.|  
|*Aplikacja* filename|Otwórz plik.|  
|*Aplikacja* `/p` filename|Plik wydruku do drukarki domyślnej.|  
|*Aplikacja* `/pt` portu sterownika drukarki filename|Drukowanie pliku do określonej drukarki.|  
|*aplikacji* `/dde`|Uruchom i poczekać na DDE polecenia.|  
|*aplikacji* `/Automation`|Uruchomiony jako serwer automatyzacji OLE.|  
|*aplikacji* `/Embedding`|Uruchamiać można edytować element osadzony OLE.|  
|*aplikacji* `/Register`<br /><br /> *aplikacji* `/Regserver`|Informuje o aplikacji do wykonywania wszystkich zadań rejestracji.|  
|*aplikacji* `/Unregister`<br /><br /> *aplikacji* `/Unregserver`|Informuje o aplikacji do wykonywania wszystkich zadań wyrejestrować.|  
  
 Te informacje są przechowywane w [m_bRunAutomated](#m_brunautomated), [m_bRunEmbedded](#m_brunembedded), i [m_nShellCommand](#m_nshellcommand). Flagi są oznaczane albo kreskami ukośnymi " **/**"lub łącznika" **-**".  
  
 Domyślna implementacja umieszcza pierwszy parametr z systemem innym niż flagi do [m_strFileName](#m_strfilename). W przypadku programu `/pt` flagę Domyślna implementacja umieszcza drugiego, trzecim i czwartym parametry bez flagi do [m_strPrinterName](#m_strprintername), [m_strDriverName](#m_strdrivername), i [m_ strPortName](#m_strportname)odpowiednio.  
  
 Domyślna implementacja ustawia również [m_bShowSplash](#m_bshowsplash) do `TRUE` tylko w przypadku nowego pliku. W przypadku nowego pliku użytkownik podjął działania dotyczące samej aplikacji. W innym przypadku, w tym otwieranie istniejących plików przy użyciu powłoki Akcja użytkownika obejmuje plik bezpośrednio. W zorientowany punktu widzenia ekranu powitalnego nie trzeba ogłaszamy uruchamiania aplikacji.  
  
 Przesłonić tę funkcję w klasie pochodnej do obsługi inne flagi i wartości parametrów.  
  
## <a name="see-also"></a>Zobacz też  
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)   
 [CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)

