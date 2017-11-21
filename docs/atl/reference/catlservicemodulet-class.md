---
title: Klasa CAtlServiceModuleT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT::CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT::Handler
- ATLBASE/ATL::CAtlServiceModuleT::InitializeSecurity
- ATLBASE/ATL::CAtlServiceModuleT::Install
- ATLBASE/ATL::CAtlServiceModuleT::IsInstalled
- ATLBASE/ATL::CAtlServiceModuleT::LogEvent
- ATLBASE/ATL::CAtlServiceModuleT::OnContinue
- ATLBASE/ATL::CAtlServiceModuleT::OnInterrogate
- ATLBASE/ATL::CAtlServiceModuleT::OnPause
- ATLBASE/ATL::CAtlServiceModuleT::OnShutdown
- ATLBASE/ATL::CAtlServiceModuleT::OnStop
- ATLBASE/ATL::CAtlServiceModuleT::OnUnknownRequest
- ATLBASE/ATL::CAtlServiceModuleT::ParseCommandLine
- ATLBASE/ATL::CAtlServiceModuleT::PreMessageLoop
- ATLBASE/ATL::CAtlServiceModuleT::RegisterAppId
- ATLBASE/ATL::CAtlServiceModuleT::Run
- ATLBASE/ATL::CAtlServiceModuleT::ServiceMain
- ATLBASE/ATL::CAtlServiceModuleT::SetServiceStatus
- ATLBASE/ATL::CAtlServiceModuleT::Start
- ATLBASE/ATL::CAtlServiceModuleT::Uninstall
- ATLBASE/ATL::CAtlServiceModuleT::Unlock
- ATLBASE/ATL::CAtlServiceModuleT::UnregisterAppId
- ATLBASE/ATL::CAtlServiceModuleT::WinMain
- ATLBASE/ATL::CAtlServiceModuleT::m_bService
- ATLBASE/ATL::CAtlServiceModuleT::m_dwThreadID
- ATLBASE/ATL::CAtlServiceModuleT::m_hServiceStatus
- ATLBASE/ATL::CAtlServiceModuleT::m_status
- ATLBASE/ATL::CAtlServiceModuleT::m_szServiceName
dev_langs: C++
helpviewer_keywords: CAtlServiceModuleT class
ms.assetid: 8fc753ce-4a50-402b-9b4a-0a4ce5dd496c
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8315177848b1beee9b6823ff2ee12f9ca1d02e4d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="catlservicemodulet-class"></a>Klasa CAtlServiceModuleT
Ta klasa implementuje usługi.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T, UINT nServiceNameID>  
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Klasy pochodne `CAtlServiceModuleT`.  
  
 *nServiceNameID*  
 Identyfikator zasobu usługi.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlServiceModuleT::CAtlServiceModuleT](#catlservicemodulet)|Konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlServiceModuleT::Handler](#handler)|Procedura programu obsługi dla usługi.|  
|[CAtlServiceModuleT::InitializeSecurity](#initializesecurity)|Udostępnia domyślne ustawienia zabezpieczeń dla usługi.|  
|[CAtlServiceModuleT::Install](#install)|Instaluje i tworzy usługi.|  
|[CAtlServiceModuleT::IsInstalled](#isinstalled)|Potwierdza, że usługa została zainstalowana.|  
|[CAtlServiceModuleT::LogEvent](#logevent)|Zapisuje w dzienniku zdarzeń.|  
|[CAtlServiceModuleT::OnContinue](#oncontinue)|Zastępuje tę metodę, aby kontynuować korzystanie z usługi.|  
|[CAtlServiceModuleT::OnInterrogate](#oninterrogate)|Zastępuje tę metodę, aby przejrzeć usługi.|  
|[CAtlServiceModuleT::OnPause](#onpause)|Zastępuje tę metodę można wstrzymać usługi.|  
|[CAtlServiceModuleT::OnShutdown](#onshutdown)|Przesłonić tę metodę w celu zatrzymania usługi|  
|[CAtlServiceModuleT::OnStop](#onstop)|Przesłonić tę metodę w celu zatrzymania usługi|  
|[CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest)|Przesłonić tę metodę w celu obsługi nieznanych żądań do usługi|  
|[CAtlServiceModuleT::ParseCommandLine](#parsecommandline)|Analizuje wiersz polecenia i wykonuje rejestrację, jeśli to konieczne.|  
|[CAtlServiceModuleT::PreMessageLoop](#premessageloop)|Ta metoda jest wywoływana bezpośrednio przed wprowadzania pętli komunikatów.|  
|[CAtlServiceModuleT::RegisterAppId](#registerappid)|Rejestruje usługę w rejestrze.|  
|[CAtlServiceModuleT::Run](#run)|Uruchamia usługę.|  
|[CAtlServiceModuleT::ServiceMain](#servicemain)|Metoda wywoływana przez Menedżera sterowania usługami.|  
|[CAtlServiceModuleT::SetServiceStatus](#setservicestatus)|Aktualizuje stan usługi.|  
|[CAtlServiceModuleT::Start](#start)|Wywoływane przez `CAtlServiceModuleT::WinMain` po uruchomieniu usługi.|  
|[CAtlServiceModuleT::Uninstall](#uninstall)|Zatrzymuje i usuwa usługę.|  
|[CAtlServiceModuleT::Unlock](#unlock)|Zmniejsza liczbę blokad usługi.|  
|[CAtlServiceModuleT::UnregisterAppId](#unregisterappid)|Usługa usuwa z rejestru.|  
|[CAtlServiceModuleT::WinMain](#winmain)|Ta metoda implementuje kod wymagany do uruchomienia usługi.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlServiceModuleT::m_bService](#m_bservice)|Flaga wskazująca, że program działa jako usługa.|  
|[CAtlServiceModuleT::m_dwThreadID](#m_dwthreadid)|Zmiennej członkowskiej przechowywania identyfikator wątku.|  
|[CAtlServiceModuleT::m_hServiceStatus](#m_hservicestatus)|Zmiennej członkowskiej przechowywania dojścia do stanu struktury informacje dla bieżącej usługi.|  
|[CAtlServiceModuleT::m_status](#m_status)|Zmiennej członkowskiej przechowywanie stanu struktury informacje dla bieżącej usługi.|  
|[CAtlServiceModuleT::m_szServiceName](#m_szservicename)|Nazwa usługi jest zarejestrowana.|  
  
## <a name="remarks"></a>Uwagi  
 `CAtlServiceModuleT`, pochodną [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md), implementuje modułu ATL usługi. `CAtlServiceModuleT`udostępnia metody do przetwarzania w wierszu polecenia, instalacji, rejestrowania i usuwania. Jeśli wymagane jest dodatkowe funkcje, można zastąpić tych i innych metod.  
  
 Ta klasa zastępuje przestarzałe [ccommodule — klasa](../../atl/reference/ccommodule-class.md) używany w starszych wersjach ATL. Zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)  
  
 `CAtlServiceModuleT`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="catlservicemodulet"></a>CAtlServiceModuleT::CAtlServiceModuleT  
 Konstruktor.  
  
```
CAtlServiceModuleT() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Inicjuje elementów członkowskich danych i ustawia stan początkowy usługi.  
  
##  <a name="handler"></a>CAtlServiceModuleT::Handler  
 Procedura programu obsługi dla usługi.  
  
```
void Handler(DWORD dwOpcode) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *dwOpcode*  
 Przełącznik, który definiuje operacji obsługi. Aby uzyskać więcej informacji zobacz uwagi.  
  
### <a name="remarks"></a>Uwagi  
 To jest kod, który wywołuje Menedżera sterowania usługami (SCM) można pobrać stanu usługi i problem instrukcje, takich jak zatrzymać lub wstrzymać. Menedżer sterowania usługami przekazuje kod operacji, pokazano poniżej, do `Handler` wskaż, jakie działanie ma wykonać usługi.  
  
|Kod operacji|Znaczenie|  
|--------------------|-------------|  
|SERVICE_CONTROL_STOP|Umożliwia zatrzymanie usługi. Zastąp metodę [CAtlServiceModuleT::OnStop](#onstop) w atlbase.h w celu zmiany zachowania.|  
|SERVICE_CONTROL_PAUSE|Użytkownik zaimplementowana. Zastąp metodę pusty [CAtlServiceModuleT::OnPause](#onpause) w atlbase.h wstrzymania usługi.|  
|SERVICE_CONTROL_CONTINUE|Użytkownik zaimplementowana. Zastąp metodę pusty [CAtlServiceModuleT::OnContinue](#oncontinue) w atlbase.h kontynuacji usługi.|  
|SERVICE_CONTROL_INTERROGATE|Użytkownik zaimplementowana. Zastąp metodę pusty [CAtlServiceModuleT::OnInterrogate](#oninterrogate) w atlbase.h, aby przejrzeć usługi.|  
|SERVICE_CONTROL_SHUTDOWN|Użytkownik zaimplementowana. Zastąp metodę pusty [CAtlServiceModuleT::OnShutdown](#onshutdown) w atlbase.h zamknięcia usługi.|  
  
 Jeśli kod operacji nie został rozpoznany, Metoda [CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest) jest wywoływana.  
  
 Domyślna usługa wygenerowany ATL obsługuje tylko instrukcje stop. Jeśli Menedżer sterowania usługami przekazuje instrukcje stop, usługa informuje SCM program o zbliżającym się zatrzymać. Wywołuje usługę `PostThreadMessage` można wysłać komunikat o rezygnacji do samej siebie. To kończy pętlę komunikatów i usługa ostatecznie zostanie zamknięte.  
  
##  <a name="initializesecurity"></a>CAtlServiceModuleT::InitializeSecurity  
 Udostępnia domyślne ustawienia zabezpieczeń dla usługi.  
  
```
HRESULT InitializeSecurity() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 W programie Visual Studio .NET 2003 ta metoda nie jest zaimplementowana w klasie podstawowej. Kreator projektu programu Visual Studio zawiera tę metodę w wygenerowanym kodzie, ale wystąpi błąd kompilacji, jeśli projekt utworzony w starszej wersji programu Visual C++ jest skompilowana przy użyciu ATL 7.1. Każda klasa, która pochodzi z `CAtlServiceModuleT` należy zaimplementować tę metodę w klasie pochodnej.  
  
 Użyj PKT poziomu uwierzytelniania, poziom personifikacji rpc_c_imp_level_identify i deskryptora zabezpieczeń odpowiednich inną niż null w wywołaniu **CoInitializeSecurity**.  
  
 Generowane przez Kreatora usługi nonattributed projektów to w  
  
 [!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]  
  
 Dla projektów oparte na atrybutach usługi to w  
  
 [!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]  
  
##  <a name="install"></a>CAtlServiceModuleT::Install  
 Instaluje i tworzy usługi.  
  
```
BOOL Install() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia FALSE w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Instaluje usługę do bazy danych Menedżera sterowania usługami (SCM), a następnie tworzy obiekt usługi. Jeśli nie można utworzyć usługi, zostanie wyświetlone okno komunikatu i metoda zwraca wartość FALSE.  
  
##  <a name="isinstalled"></a>CAtlServiceModuleT::IsInstalled  
 Potwierdza, że usługa została zainstalowana.  
  
```
BOOL IsInstalled() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli usługa jest zainstalowana, wartość FALSE w przeciwnym razie wartość.  
  
##  <a name="logevent"></a>CAtlServiceModuleT::LogEvent  
 Zapisuje w dzienniku zdarzeń.  
  
```
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszFormat`  
 Ciąg do zapisu w dzienniku zdarzeń.  
  
 ...  
 Opcjonalne dodatkowe parametry do zapisania w dzienniku zdarzeń.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda szczegóły dokonuje zapisu do dziennika zdarzeń przy użyciu funkcji [ReportEvent](http://msdn.microsoft.com/library/windows/desktop/aa363679). Jeśli usługa nie działa, ciąg są wysyłane do konsoli.  
  
##  <a name="m_bservice"></a>CAtlServiceModuleT::m_bService  
 Flaga wskazująca, że program działa jako usługa.  
  
```
BOOL m_bService;
```  
  
### <a name="remarks"></a>Uwagi  
 Używany do odróżnienia EXE usługi EXE aplikacji.  
  
##  <a name="m_dwthreadid"></a>CAtlServiceModuleT::m_dwThreadID  
 Zmiennej członkowskiej przechowywania identyfikator wątku usługi.  
  
```
DWORD m_dwThreadID;
```  
  
### <a name="remarks"></a>Uwagi  
 Ta zmienna przechowuje identyfikator wątku bieżącego wątku.  
  
##  <a name="m_hservicestatus"></a>CAtlServiceModuleT::m_hServiceStatus  
 Zmiennej członkowskiej przechowywania dojścia do stanu struktury informacje dla bieżącej usługi.  
  
```
SERVICE_STATUS_HANDLE m_hServiceStatus;
```  
  
### <a name="remarks"></a>Uwagi  
 [SERVICE_STATUS](http://msdn.microsoft.com/library/windows/desktop/ms685996) struktura zawiera informacje dotyczące usługi.  
  
##  <a name="m_status"></a>CAtlServiceModuleT::m_status  
 Zmiennej członkowskiej przechowywanie stanu struktury informacje dla bieżącej usługi.  
  
```
SERVICE_STATUS m_status;
```  
  
### <a name="remarks"></a>Uwagi  
 [SERVICE_STATUS](http://msdn.microsoft.com/library/windows/desktop/ms685996) struktura zawiera informacje dotyczące usługi.  
  
##  <a name="m_szservicename"></a>CAtlServiceModuleT::m_szServiceName  
 Nazwa usługi jest zarejestrowana.  
  
```
TCHAR [256] m_szServiceName;
```  
  
### <a name="remarks"></a>Uwagi  
 Ciąg zerem służący do przechowywania nazwy usługi.  
  
##  <a name="oncontinue"></a>CAtlServiceModuleT::OnContinue  
 Zastępuje tę metodę, aby kontynuować korzystanie z usługi.  
  
```
void OnContinue() throw();
```  
  
##  <a name="oninterrogate"></a>CAtlServiceModuleT::OnInterrogate  
 Zastępuje tę metodę, aby przejrzeć usługi.  
  
```
void OnInterrogate() throw();
```  
  
##  <a name="onpause"></a>CAtlServiceModuleT::OnPause  
 Zastępuje tę metodę można wstrzymać usługi.  
  
```
void OnPause() throw();
```  
  
##  <a name="onshutdown"></a>CAtlServiceModuleT::OnShutdown  
 Należy przesłonić tę metodę w celu zatrzymania usługi.  
  
```
void OnShutdown() throw();
```  
  
##  <a name="onstop"></a>CAtlServiceModuleT::OnStop  
 Zastępuje tę metodę w celu zatrzymania usługi.  
  
```
void OnStop() throw();
```  
  
##  <a name="onunknownrequest"></a>CAtlServiceModuleT::OnUnknownRequest  
 Zastępuje tę metodę do obsługi nieznanych żądań do usługi.  
  
```
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```  
  
### <a name="parameters"></a>Parametry  
 */\*dwOpcode\*/*  
 Zastrzeżone.  
  
##  <a name="parsecommandline"></a>CAtlServiceModuleT::ParseCommandLine  
 Analizuje wiersz polecenia i wykonuje rejestrację, jeśli to konieczne.  
  
```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpCmdLine`  
 Wiersz polecenia.  
  
 `pnRetCode`  
 Wynik HRESULT odpowiadającej rejestracji (jeśli miało to miejsce).  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA na powodzenie lub wartość false, jeśli nie można zarejestrować pliku RGS podana w wierszu polecenia.  
  
### <a name="remarks"></a>Uwagi  
 Analizuje wiersz polecenia i rejestruje lub wyrejestrowuje dostarczonego pliku RGS w razie potrzeby. Ta metoda wywołuje [CAtlExeModuleT::ParseCommandLine](../../atl/reference/catlexemodulet-class.md#parsecommandline) do wyszukania **/regserver** i **/Unregserver**. Dodawanie argument **- / Service** zarejestruje usługi.  
  
##  <a name="premessageloop"></a>CAtlServiceModuleT::PreMessageLoop  
 Ta metoda jest wywoływana bezpośrednio przed wprowadzania pętli komunikatów.  
  
```
HRESULT PreMessageLoop(int nShowCmd) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nShowCmd`  
 Ten parametr jest przekazywany do [CAtlExeModuleT::PreMessageLoop](../../atl/reference/catlexemodulet-class.md#premessageloop).  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę metodę, aby dodać kod inicjujący niestandardowych dla usługi.  
  
##  <a name="registerappid"></a>CAtlServiceModuleT::RegisterAppId  
 Rejestruje usługę w rejestrze.  
  
```
inline HRESULT RegisterAppId(bool bService = false) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *bUsługa*  
 Musi mieć wartość true, aby zarejestrować jako usługa.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="run"></a>CAtlServiceModuleT::Run  
 Uruchamia usługę.  
  
```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nShowCmd`  
 Określa, jaki ma być wyświetlana okna. Ten parametr może być jedna z wartości omówione w [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559) sekcji. Wartość domyślna to SW_HIDE.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Po wywołaniu, **Uruchom** wywołania [CAtlServiceModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::RunMessageLoop](../../atl/reference/catlexemodulet-class.md#runmessageloop), i [CAtlExeModuleT:: PostMessageLoop](../../atl/reference/catlexemodulet-class.md#postmessageloop).  
  
##  <a name="servicemain"></a>CAtlServiceModuleT::ServiceMain  
 Ta metoda jest wywoływana przez Menedżera sterowania usługami.  
  
```
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *dwArgc*  
 Argc — argument.  
  
 *lpszArgv*  
 ARGV — argument.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje Menedżera sterowania usługami (SCM) `ServiceMain` po otwarciu aplikacji usługi w Panelu sterowania, wybierz usługę i kliknij przycisk Start.  
  
 Po SCM wywołuje `ServiceMain`, usługa musi nadać SCM funkcji obsługi. Ta funkcja umożliwia SCM uzyskać stanu usługi i podaj szczegółowe instrukcje (na przykład wstrzymanie lub zatrzymanie). Następnie [CAtlServiceModuleT::Run](#run) jest wywoływana w celu wykonywania głównych pracy usługi. **Uruchom** kontynuuje wykonywanie aż do zatrzymania usługi.  
  
##  <a name="setservicestatus"></a>CAtlServiceModuleT::SetServiceStatus  
 Ta metoda aktualizuje stan usługi.  
  
```
void SetServiceStatus(DWORD dwState) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dwState`  
 Nowy stan. Zobacz [SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241) prawidłowych wartości.  
  
### <a name="remarks"></a>Uwagi  
 Aktualizuje informacje o stanie menedżera kontroli usług dla usługi. Jest ona wywoływana przez [CAtlServiceModuleT::Run](#run), [CAtlServiceModuleT::ServiceMain](#servicemain) i innych metod obsługi. Stan jest również przechowywane w zmiennej członkowskiej [CAtlServiceModuleT::m_status](#m_status).  
  
##  <a name="start"></a>CAtlServiceModuleT::Start  
 Wywoływane przez `CAtlServiceModuleT::WinMain` po uruchomieniu usługi.  
  
```
HRESULT Start(int nShowCmd) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nShowCmd`  
 Określa, jaki ma być wyświetlana okna. Ten parametr może być jedna z wartości omówione w [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559) sekcji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 [CAtlServiceModuleT::WinMain](#winmain) metoda obsługuje zarówno rejestrację i instalacji, a także zadania wykonywane w usuwanie wpisów rejestru i odinstalowywania modułu. Po uruchomieniu usługi `WinMain` wywołania **Start**.  
  
##  <a name="uninstall"></a>CAtlServiceModuleT::Uninstall  
 Zatrzymuje i usuwa usługę.  
  
```
BOOL Uninstall() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia FALSE w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Zatrzymuje usługę uruchamianie i usuwa go z bazy danych menedżera kontroli usług.  
  
##  <a name="unlock"></a>CAtlServiceModuleT::Unlock  
 Zmniejsza liczbę blokad usługi.  
  
```
LONG Unlock() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę blokad, które mogą być przydatne w przypadku diagnostyki i debugowania.  
  
##  <a name="unregisterappid"></a>CAtlServiceModuleT::UnregisterAppId  
 Usługa usuwa z rejestru.  
  
```
HRESULT UnregisterAppId() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="winmain"></a>CAtlServiceModuleT::WinMain  
 Ta metoda implementuje kod wymagany do uruchomienia usługi.  
  
```
int WinMain(int nShowCmd) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nShowCmd`  
 Określa, jaki ma być wyświetlana okna. Ten parametr może być jedna z wartości omówione w [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559) sekcji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość zwrotna usługi.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda przetwarza wiersza polecenia (z [CAtlServiceModuleT::ParseCommandLine](#parsecommandline)), a następnie uruchamia usługę (przy użyciu [CAtlServiceModuleT::Start](#start)).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
