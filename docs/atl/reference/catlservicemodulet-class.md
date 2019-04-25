---
title: Klasa CAtlServiceModuleT
ms.date: 11/04/2016
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
helpviewer_keywords:
- CAtlServiceModuleT class
ms.assetid: 8fc753ce-4a50-402b-9b4a-0a4ce5dd496c
ms.openlocfilehash: 2d4d5d4a5c4d8a52f792cc04a968974967c1e13a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260204"
---
# <a name="catlservicemodulet-class"></a>Klasa CAtlServiceModuleT

Ta klasa implementuje usługi.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template <class T, UINT nServiceNameID>
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa jest pochodną `CAtlServiceModuleT`.

*nServiceNameID*<br/>
Identyfikator zasobu usługi.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlServiceModuleT::CAtlServiceModuleT](#catlservicemodulet)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlServiceModuleT::Handler](#handler)|Procedury obsługi dla usługi.|
|[CAtlServiceModuleT::InitializeSecurity](#initializesecurity)|Udostępnia domyślne ustawienia zabezpieczeń dla usługi.|
|[CAtlServiceModuleT::Install](#install)|Instaluje i tworzy usługę.|
|[CAtlServiceModuleT::IsInstalled](#isinstalled)|Potwierdza, że usługa została zainstalowana.|
|[CAtlServiceModuleT::LogEvent](#logevent)|Zapisuje w dzienniku zdarzeń.|
|[CAtlServiceModuleT::OnContinue](#oncontinue)|Zastępuje tę metodę, aby kontynuować usługę.|
|[CAtlServiceModuleT::OnInterrogate](#oninterrogate)|Zastąpienie tej metody na potrzeby analizowania usługi.|
|[CAtlServiceModuleT::OnPause](#onpause)|Zastępuje tę metodę, aby wstrzymać usługę.|
|[CAtlServiceModuleT::OnShutdown](#onshutdown)|Przesłoń tę metodę w celu zatrzymania usługi|
|[CAtlServiceModuleT::OnStop](#onstop)|Przesłonić tę metodę, aby zatrzymać usługę|
|[CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest)|Przesłoń tę metodę w celu obsługi nieznanych żądań do usługi|
|[CAtlServiceModuleT::ParseCommandLine](#parsecommandline)|Analizuje wiersz polecenia i wykonuje rejestrację, jeśli to konieczne.|
|[CAtlServiceModuleT::PreMessageLoop](#premessageloop)|Ta metoda jest wywoływana tuż przed wprowadzania pętli komunikatów.|
|[CAtlServiceModuleT::RegisterAppId](#registerappid)|Rejestruje usługę w rejestrze.|
|[CAtlServiceModuleT::Run](#run)|Uruchamia usługę.|
|[CAtlServiceModuleT::ServiceMain](#servicemain)|Metoda wywoływana przez Menedżera sterowania usługami.|
|[CAtlServiceModuleT::SetServiceStatus](#setservicestatus)|Aktualizuje stan usługi.|
|[CAtlServiceModuleT::Start](#start)|Wywoływane przez `CAtlServiceModuleT::WinMain` podczas uruchamiania usługi.|
|[CAtlServiceModuleT::Uninstall](#uninstall)|Zatrzymuje i spowoduje usunięcie usługi.|
|[CAtlServiceModuleT::Unlock](#unlock)|Zmniejsza liczbę blokad tej usługi.|
|[CAtlServiceModuleT::UnregisterAppId](#unregisterappid)|Usługa usuwa z rejestru.|
|[CAtlServiceModuleT::WinMain](#winmain)|Ta metoda implementuje kodu wymaganego do uruchomienia usługi.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAtlServiceModuleT::m_bService](#m_bservice)|Flaga wskazująca, że program jest uruchomiony jako usługa.|
|[CAtlServiceModuleT::m_dwThreadID](#m_dwthreadid)|Przechowywanie identyfikator wątku zmiennej składowej.|
|[CAtlServiceModuleT::m_hServiceStatus](#m_hservicestatus)|Przechowywanie dojścia do struktury informacji o stan usługi bieżącej zmiennej składowej.|
|[CAtlServiceModuleT::m_status](#m_status)|Przechowywanie struktury informacji o stan usługi bieżącej zmiennej składowej.|
|[CAtlServiceModuleT::m_szServiceName](#m_szservicename)|Nazwa usługi jest zarejestrowana.|

## <a name="remarks"></a>Uwagi

`CAtlServiceModuleT`, pochodzące z [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md), implementuje modułu ATL usługi. `CAtlServiceModuleT` zawiera metody służące do przetwarzania w wierszu polecenia, instalacji, rejestrowania i usuwania. Jeśli wymagane jest dodatkowe funkcje, można zastąpić tych i innych metod.

Ta klasa zastępuje przestarzałe [klasa CComModule](../../atl/reference/ccommodule-class.md) stosowane we wcześniejszych wersjach ATL. Zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)

`CAtlServiceModuleT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="catlservicemodulet"></a>  CAtlServiceModuleT::CAtlServiceModuleT

Konstruktor.

```
CAtlServiceModuleT() throw();
```

### <a name="remarks"></a>Uwagi

Inicjuje elementy członkowskie danych i ustawia stan początkowy usługi.

##  <a name="handler"></a>  CAtlServiceModuleT::Handler

Procedury obsługi dla usługi.

```
void Handler(DWORD dwOpcode) throw();
```

### <a name="parameters"></a>Parametry

*dwOpcode*<br/>
Przełącznik, który definiuje procedurę obsługi operacji. Aby uzyskać szczegółowe informacje Zobacz uwagi.

### <a name="remarks"></a>Uwagi

Jest to kod, który wywołuje Menedżera sterowania usługami (SCM), aby pobrać stan instrukcji usługi i problemów, takich jak zatrzymać lub wstrzymać. Menedżer sterowania usługami przekazuje kod operacji, pokazano poniżej, do `Handler` do wskazania, co należy zrobić.

|Kod operacji|Znaczenie|
|--------------------|-------------|
|SERVICE_CONTROL_STOP|Zatrzymuje usługę. Zastąp metodę [CAtlServiceModuleT::OnStop](#onstop) w atlbase.h, aby zmienić to zachowanie.|
|SERVICE_CONTROL_PAUSE|Użytkownik jest zaimplementowana. Zastąp metodę pustego [CAtlServiceModuleT::OnPause](#onpause) w atlbase.h, aby wstrzymać usługę.|
|SERVICE_CONTROL_CONTINUE|Użytkownik jest zaimplementowana. Zastąp metodę pustego [CAtlServiceModuleT::OnContinue](#oncontinue) w atlbase.h kontynuować usługi.|
|SERVICE_CONTROL_INTERROGATE|Użytkownik jest zaimplementowana. Zastąp metodę pustego [CAtlServiceModuleT::OnInterrogate](#oninterrogate) w atlbase.h na potrzeby analizowania usługi.|
|SERVICE_CONTROL_SHUTDOWN|Użytkownik jest zaimplementowana. Zastąp metodę pustego [CAtlServiceModuleT::OnShutdown](#onshutdown) w atlbase.h zamknięcie usługi.|

Jeśli kod operacji nie został rozpoznany, Metoda [CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest) jest wywoływana.

Domyślna usługa generowane ATL obsługuje tylko instrukcji zatrzymania. Jeśli Menedżer sterowania usługami przekazuje instrukcje stop, usługa informuje Menedżer sterowania usługami, program zostanie zatrzymana. Następnie wywołuje usługę `PostThreadMessage` publikować komunikat o sobie. To kończy pętli komunikatów, a usługa ostatecznie zostanie zamknięte.

##  <a name="initializesecurity"></a>  CAtlServiceModuleT::InitializeSecurity

Udostępnia domyślne ustawienia zabezpieczeń dla usługi.

```
HRESULT InitializeSecurity() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

W programie Visual Studio .NET 2003 ta metoda nie jest zaimplementowana w klasie bazowej. Kreator projektu programu Visual Studio zawiera tę metodę w wygenerowanym kodzie, ale występuje błąd kompilacji, jeśli projekt utworzony w starszej wersji programu Visual C++ jest skompilowana przy użyciu biblioteki ATL 7.1. Dowolną klasę pochodzącą od `CAtlServiceModuleT` należy zaimplementować tę metodę w klasie pochodnej.

Użyj PKT poziom uwierzytelniania, poziom personifikacji rpc_c_imp_level_identify i deskryptora zabezpieczeń odpowiednich inna niż null w wywołaniu `CoInitializeSecurity`.

Dla projektów generowane przez Kreatora usługi nonattributed takie rozwiązanie byłoby w

[!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]

W przypadku projektów opartego na atrybutach usługi takie rozwiązanie byłoby w

[!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]

##  <a name="install"></a>  CAtlServiceModuleT::Install

Instaluje i tworzy usługę.

```
BOOL Install() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Instaluje usługę do bazy danych Menedżera sterowania usługami (SCM), a następnie tworzy obiekt usługi. Jeśli nie można utworzyć usługi, zostanie wyświetlone okno komunikatu, a metoda zwraca wartość FALSE.

##  <a name="isinstalled"></a>  CAtlServiceModuleT::IsInstalled

Potwierdza, że usługa została zainstalowana.

```
BOOL IsInstalled() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli usługa jest zainstalowana, wartość FALSE w przeciwnym razie.

##  <a name="logevent"></a>  CAtlServiceModuleT::LogEvent

Zapisuje w dzienniku zdarzeń.

```
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Ciąg do zapisu w dzienniku zdarzeń.

*...*<br/>
Opcjonalne dodatkowe ciągi są zapisywane w dzienniku zdarzeń.

### <a name="remarks"></a>Uwagi

Ta metoda szczegóły dokonuje zapisu do dziennika zdarzeń, przy użyciu funkcji [ReportEvent](/windows/desktop/api/winbase/nf-winbase-reporteventa). Jeśli żadna usługa nie jest uruchomiona, ciąg jest wysyłany do konsoli.

##  <a name="m_bservice"></a>  CAtlServiceModuleT::m_bService

Flaga wskazująca, że program jest uruchomiony jako usługa.

```
BOOL m_bService;
```

### <a name="remarks"></a>Uwagi

Używany do odróżnienia EXE usługi z pliku EXE aplikacji.

##  <a name="m_dwthreadid"></a>  CAtlServiceModuleT::m_dwThreadID

Przechowywanie identyfikator wątku usługi zmiennej składowej.

```
DWORD m_dwThreadID;
```

### <a name="remarks"></a>Uwagi

Ta zmienna przechowuje identyfikator wątku dla bieżącego wątku.

##  <a name="m_hservicestatus"></a>  CAtlServiceModuleT::m_hServiceStatus

Przechowywanie dojścia do struktury informacji o stan usługi bieżącej zmiennej składowej.

```
SERVICE_STATUS_HANDLE m_hServiceStatus;
```

### <a name="remarks"></a>Uwagi

[SERVICE_STATUS](/windows/desktop/api/winsvc/ns-winsvc-_service_status) struktura zawiera informacje dotyczące usługi.

##  <a name="m_status"></a>  CAtlServiceModuleT::m_status

Przechowywanie struktury informacji o stan usługi bieżącej zmiennej składowej.

```
SERVICE_STATUS m_status;
```

### <a name="remarks"></a>Uwagi

[SERVICE_STATUS](/windows/desktop/api/winsvc/ns-winsvc-_service_status) struktura zawiera informacje dotyczące usługi.

##  <a name="m_szservicename"></a>  CAtlServiceModuleT::m_szServiceName

Nazwa usługi jest zarejestrowana.

```
TCHAR [256] m_szServiceName;
```

### <a name="remarks"></a>Uwagi

Ciąg zakończony znakiem null, która przechowuje nazwę usługi.

##  <a name="oncontinue"></a>  CAtlServiceModuleT::OnContinue

Zastępuje tę metodę, aby kontynuować usługę.

```
void OnContinue() throw();
```

##  <a name="oninterrogate"></a>  CAtlServiceModuleT::OnInterrogate

Zastąpienie tej metody na potrzeby analizowania usługi.

```
void OnInterrogate() throw();
```

##  <a name="onpause"></a>  CAtlServiceModuleT::OnPause

Zastępuje tę metodę, aby wstrzymać usługę.

```
void OnPause() throw();
```

##  <a name="onshutdown"></a>  CAtlServiceModuleT::OnShutdown

Przesłoń tę metodę w celu zatrzymania usługi.

```
void OnShutdown() throw();
```

##  <a name="onstop"></a>  CAtlServiceModuleT::OnStop

Zastępuje tę metodę w celu zatrzymania usługi.

```
void OnStop() throw();
```

##  <a name="onunknownrequest"></a>  CAtlServiceModuleT::OnUnknownRequest

Zastępuje tę metodę do obsługi nieznanego żądań do usługi.

```
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```

### <a name="parameters"></a>Parametry

*dwOpcode*<br/>
Zastrzeżone.

##  <a name="parsecommandline"></a>  CAtlServiceModuleT::ParseCommandLine

Analizuje wiersz polecenia i wykonuje rejestrację, jeśli to konieczne.

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Parametry

*lpCmdLine*<br/>
Wiersz polecenia.

*pnRetCode*<br/>
Wartość HRESULT odpowiadający rejestracji (jeśli miało to miejsce).

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA na powodzenia lub wartość false, jeśli nie można zarejestrować plik RGS podane w wierszu polecenia.

### <a name="remarks"></a>Uwagi

Analizuje wiersz polecenia i rejestruje lub Wyrejestrowuje podany plik RGS, jeśli to konieczne. Ta metoda wywołuje [CAtlExeModuleT::ParseCommandLine](../../atl/reference/catlexemodulet-class.md#parsecommandline) pod kątem **/regserver** i **/Unregserver**. Dodawanie argument **- / Service** zarejestruje usługi.

##  <a name="premessageloop"></a>  CAtlServiceModuleT::PreMessageLoop

Ta metoda jest wywoływana tuż przed wprowadzania pętli komunikatów.

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Ten parametr jest przekazywany do [CAtlExeModuleT::PreMessageLoop](../../atl/reference/catlexemodulet-class.md#premessageloop).

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Zastępuje tę metodę, aby dodać kod inicjujący niestandardowych dla usługi.

##  <a name="registerappid"></a>  CAtlServiceModuleT::RegisterAppId

Rejestruje usługę w rejestrze.

```
inline HRESULT RegisterAppId(bool bService = false) throw();
```

### <a name="parameters"></a>Parametry

*bService*<br/>
Muszą być spełnione, aby zarejestrować się jako usługa.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="run"></a>  CAtlServiceModuleT::Run

Uruchamia usługę.

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Określa, jak ma być wyświetlana okna. Ten parametr może być jedną z wartości omówione w [WinMain](/windows/desktop/api/winbase/nf-winbase-winmain) sekcji. Wartość domyślna to SW_HIDE.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Po wywołaniu, `Run` wywołania [CAtlServiceModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::RunMessageLoop](../../atl/reference/catlexemodulet-class.md#runmessageloop), i [CAtlExeModuleT::PostMessageLoop](../../atl/reference/catlexemodulet-class.md#postmessageloop).

##  <a name="servicemain"></a>  CAtlServiceModuleT::ServiceMain

Ta metoda jest wywoływana przez menedżera kontroli usług.

```
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```

### <a name="parameters"></a>Parametry

*dwArgc*<br/>
Argc — argument.

*lpszArgv*<br/>
ARGV — argument.

### <a name="remarks"></a>Uwagi

Wywołuje Menedżera sterowania usługami (SCM) `ServiceMain` po otwarciu aplikacji usługi w Panelu sterowania, wybierz usługę i kliknij przycisk Uruchom.

Po Menedżer sterowania usługami wywołuje `ServiceMain`, usługa musi udzielić Menedżer sterowania usługami, funkcja obsługi. Ta funkcja pozwala na uzyskanie stanu usługi i przekazać szczegółowych instrukcji (na przykład wstrzymanie lub zatrzymanie) Menedżer sterowania usługami. Następnie [CAtlServiceModuleT::Run](#run) jest wywoływana w celu wykonania pracy głównego usługi. `Run` kontynuuje wykonywanie dopóki nie zostanie zatrzymana.

##  <a name="setservicestatus"></a>  CAtlServiceModuleT::SetServiceStatus

Ta metoda aktualizuje stan usługi.

```
void SetServiceStatus(DWORD dwState) throw();
```

### <a name="parameters"></a>Parametry

*dwState*<br/>
Nowy stan. Zobacz [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) uzyskać odpowiednie wartości.

### <a name="remarks"></a>Uwagi

Aktualizuje informacje o stanie menedżera kontroli usług dla usługi. Jest ona wywoływana przez [CAtlServiceModuleT::Run](#run), [CAtlServiceModuleT::ServiceMain](#servicemain) i innych metod obsługi. Stan także jest przechowywany w zmiennej składowej [CAtlServiceModuleT::m_status](#m_status).

##  <a name="start"></a>  CAtlServiceModuleT::Start

Wywoływane przez `CAtlServiceModuleT::WinMain` podczas uruchamiania usługi.

```
HRESULT Start(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Określa, jak ma być wyświetlana okna. Ten parametr może być jedną z wartości omówione w [WinMain](/windows/desktop/api/winbase/nf-winbase-winmain) sekcji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

[CAtlServiceModuleT::WinMain](#winmain) metoda obsługuje rejestrację i instalacji, a także zadań w usuwanie wpisów rejestru i odinstalowywania modułu. Po uruchomieniu usługi `WinMain` wywołania `Start`.

##  <a name="uninstall"></a>  CAtlServiceModuleT::Uninstall

Zatrzymuje i spowoduje usunięcie usługi.

```
BOOL Uninstall() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Zatrzymuje usługę, uruchamianie i usuwa go z bazy danych Menedżera sterowania usługami.

##  <a name="unlock"></a>  CAtlServiceModuleT::Unlock

Zmniejsza liczbę blokad tej usługi.

```
LONG Unlock() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę blokad, które mogą być przydatne w przypadku diagnostyki i debugowania.

##  <a name="unregisterappid"></a>  CAtlServiceModuleT::UnregisterAppId

Usługa usuwa z rejestru.

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="winmain"></a>  CAtlServiceModuleT::WinMain

Ta metoda implementuje kodu wymaganego do uruchomienia usługi.

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Określa, jak ma być wyświetlana okna. Ten parametr może być jedną z wartości omówione w [WinMain](/windows/desktop/api/winbase/nf-winbase-winmain) sekcji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość zwracaną z tej usługi.

### <a name="remarks"></a>Uwagi

Ta metoda przetwarza wiersza polecenia (przy użyciu [CAtlServiceModuleT::ParseCommandLine](#parsecommandline)), a następnie uruchamia usługę (przy użyciu [CAtlServiceModuleT::Start](#start)).

## <a name="see-also"></a>Zobacz także

[Klasa CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
