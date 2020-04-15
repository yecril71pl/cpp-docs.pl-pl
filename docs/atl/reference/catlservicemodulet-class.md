---
title: Klasa CAtlServiceModuleT
ms.date: 05/06/2019
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
ms.openlocfilehash: 5d87eada997d0bbfe44cd07a819f6b012a7a3a20
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321336"
---
# <a name="catlservicemodulet-class"></a>Klasa CAtlServiceModuleT

Ta klasa implementuje usługę.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T, UINT nServiceNameID>
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa pochodzi `CAtlServiceModuleT`od .

*nNameID usługi*<br/>
Identyfikator zasobu usługi.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlServiceModuleT::CAtlServiceModuleT](#catlservicemodulet)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlServiceModuleT::Handler](#handler)|Procedura obsługi dla usługi.|
|[CAtlServiceModuleT::InitializeSecurity](#initializesecurity)|Zawiera domyślne ustawienia zabezpieczeń usługi.|
|[CAtlServiceModuleT::Zainstaluj](#install)|Instaluje i tworzy usługę.|
|[CAtlServiceModuleT::IsIninstalowany](#isinstalled)|Potwierdza, że usługa została zainstalowana.|
|[CAtlServiceModuleT::LogEvent](#logevent)|Zapisuje w dzienniku zdarzeń.|
|[CAtlServiceModuleT::OnContinue](#oncontinue)|Zastąpuj tę metodę, aby kontynuować usługę.|
|[CAtlServiceModuleT::OnInterrogate](#oninterrogate)|Zastąpuj tę metodę, aby przesłuchiwać usługę.|
|[CAtlServiceModuleT::OnPause](#onpause)|Zastąpuj tę metodę, aby wstrzymać usługę.|
|[CAtlServiceModuleT::OnShutdown](#onshutdown)|Zastąpić tę metodę, aby zamknąć usługę|
|[CAtlServiceModuleT::OnStop](#onstop)|Zastąpuj tę metodę, aby zatrzymać usługę|
|[CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest)|Zastąpuj tę metodę do obsługi nieznanych żądań do usługi|
|[CAtlServiceModuleT::ParseCommandLine](#parsecommandline)|Analizuje wiersz polecenia i w razie potrzeby wykonuje rejestrację.|
|[CAtlServiceModuleT::PreMessageLoop](#premessageloop)|Ta metoda jest wywoływana bezpośrednio przed wprowadzeniem pętli komunikatów.|
|[CAtlServiceModuleT::RegisterAppId](#registerappid)|Rejestruje usługę w rejestrze.|
|[CAtlServiceModuleT::Uruchom](#run)|Uruchamia usługę.|
|[CAtlServiceModuleT::ServiceMain](#servicemain)|Metoda wywoływana przez Menedżera sterowania usługami.|
|[CAtlServiceModuleT::SetServiceStatus](#setservicestatus)|Aktualizuje stan usługi.|
|[CAtlServiceModuleT::Start](#start)|Wywoływana `CAtlServiceModuleT::WinMain` przez po uruchomieniu usługi.|
|[CAtlServiceModuleT::Odinstaluj](#uninstall)|Zatrzymuje i usuwa usługę.|
|[CAtlServiceModuleT::Odblokuj](#unlock)|Zmniejsza liczbę blokad usługi.|
|[CAtlServiceModuleT::Wyrównaj wyrejestrowy](#unregisterappid)|Usuwa usługę z rejestru.|
|[CAtlServiceModuleT::WinMain](#winmain)|Ta metoda implementuje kod wymagany do uruchomienia usługi.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAtlServiceModuleT::m_bService](#m_bservice)|Flaga wskazująca, że program jest uruchomiony jako usługa.|
|[CAtlServiceModuleT::m_dwThreadID](#m_dwthreadid)|Zmienna elementu członkowskiego przechowujący identyfikator wątku.|
|[CAtlServiceModuleT::m_hServiceStatus](#m_hservicestatus)|Zmienna elementu członkowskiego przechowująca dojście do struktury informacji o stanie dla bieżącej usługi.|
|[CAtlServiceModuleT::m_status](#m_status)|Zmienna elementu członkowskiego przechowująca strukturę informacji o stanie dla bieżącej usługi.|
|[CAtlServiceModuleT::m_szServiceName](#m_szservicename)|Nazwa usługi jest rejestrowana.|

## <a name="remarks"></a>Uwagi

`CAtlServiceModuleT`, pochodzące z [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md), implementuje moduł usługi ATL. `CAtlServiceModuleT`zawiera metody przetwarzania wiersza polecenia, instalacji, rejestracji i usuwania. Jeśli wymagana jest dodatkowa funkcjonalność, te i inne metody mogą zostać zastąpione.

Ta klasa zastępuje przestarzałe [CComModule Class](../../atl/reference/ccommodule-class.md) używane we wcześniejszych wersjach ATL. Zobacz [klasy modułów ATL, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[Catlmodule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[Catlexemodulet](../../atl/reference/catlexemodulet-class.md)

`CAtlServiceModuleT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="catlservicemoduletcatlservicemodulet"></a><a name="catlservicemodulet"></a>CAtlServiceModuleT::CAtlServiceModuleT

Konstruktor.

```
CAtlServiceModuleT() throw();
```

### <a name="remarks"></a>Uwagi

Inicjuje elementy członkowskie danych i ustawia początkowy stan usługi.

## <a name="catlservicemodulethandler"></a><a name="handler"></a>CAtlServiceModuleT::Handler

Procedura obsługi dla usługi.

```
void Handler(DWORD dwOpcode) throw();
```

### <a name="parameters"></a>Parametry

*dwOpcode (kod)*<br/>
Przełącznik, który definiuje operację obsługi. Aby uzyskać szczegółowe informacje, zobacz Uwagi.

### <a name="remarks"></a>Uwagi

Jest to kod, który menedżer sterowania usługą (SCM) wywołuje w celu pobrania stanu usługi i wydania instrukcji, takich jak zatrzymanie lub wstrzymanie. SCM przekazuje kod operacji, pokazano `Handler` poniżej, aby wskazać, co usługa powinna zrobić.

|Kod operacji|Znaczenie|
|--------------------|-------------|
|SERVICE_CONTROL_STOP|Zatrzymuje usługę. Zastąp metodę [CAtlServiceModuleT::OnStop](#onstop) w atlbase.h, aby zmienić zachowanie.|
|SERVICE_CONTROL_PAUSE|Użytkownik zaimplementowany. Zastąp pustą metodę [CAtlServiceModuleT::OnPause](#onpause) w atlbase.h, aby wstrzymać usługę.|
|SERVICE_CONTROL_CONTINUE|Użytkownik zaimplementowany. Zastąp pustą metodę [CAtlServiceModuleT::OnContinue](#oncontinue) w atlbase.h, aby kontynuować usługę.|
|SERVICE_CONTROL_INTERROGATE|Użytkownik zaimplementowany. Zastąp pustą metodę [CAtlServiceModuleT::OnInterrogate](#oninterrogate) w atlbase.h, aby przesłuchiwać usługę.|
|SERVICE_CONTROL_SHUTDOWN|Użytkownik zaimplementowany. Zastąp pustą metodę [CAtlServiceModuleT::OnShutdown](#onshutdown) w atlbase.h, aby zamknąć usługę.|

Jeśli kod operacji nie jest rozpoznawany, wywoływana jest metoda [CAtlServiceModuleT::OnUnknownRequest.](#onunknownrequest)

Domyślna usługa generowana przez ATL obsługuje tylko instrukcję zatrzymania. Jeśli SCM przekazuje instrukcję zatrzymania, usługa informuje SCM, że program ma się zatrzymać. Następnie usługa `PostThreadMessage` wywołuje, aby opublikować wiadomość zamknięcia do siebie. Spowoduje to zakończenie pętli komunikatów i usługa zostanie ostatecznie zamknięta.

## <a name="catlservicemoduletinitializesecurity"></a><a name="initializesecurity"></a>CAtlServiceModuleT::InitializeSecurity

Zawiera domyślne ustawienia zabezpieczeń usługi.

```
HRESULT InitializeSecurity() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Każda klasa, która `CAtlServiceModuleT` wywodzi się z musi zaimplementować tę metodę w klasie pochodnej.

Użyj uwierzytelniania na poziomie PKT, poziomu personifikacji RPC_C_IMP_LEVEL_IDENTIFY i odpowiedniego deskryptora zabezpieczeń innych niż null w wywołaniu `CoInitializeSecurity`.

W przypadku projektów usług generowanych przez kreatora, które nie są przypisane,

[!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]

W przypadku przypisanych projektów usługowych

[!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]

## <a name="catlservicemoduletinstall"></a><a name="install"></a>CAtlServiceModuleT::Zainstaluj

Instaluje i tworzy usługę.

```
BOOL Install() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Instaluje usługę w bazie danych Programu Service Control Manager (SCM), a następnie tworzy obiekt usługi. Jeśli nie można utworzyć usługi, zostanie wyświetlone okno komunikatu, a metoda zwraca wartość FAŁSZ.

## <a name="catlservicemoduletisinstalled"></a><a name="isinstalled"></a>CAtlServiceModuleT::IsIninstalowany

Potwierdza, że usługa została zainstalowana.

```
BOOL IsInstalled() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli usługa jest zainstalowana, w przeciwnym razie wartość FAŁszuj.

## <a name="catlservicemoduletlogevent"></a><a name="logevent"></a>CAtlServiceModuleT::LogEvent

Zapisuje w dzienniku zdarzeń.

```
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Ciąg do zapisu w dzienniku zdarzeń.

*...*<br/>
Opcjonalne dodatkowe ciągi, które mają być zapisywane w dzienniku zdarzeń.

### <a name="remarks"></a>Uwagi

Ta metoda zapisuje szczegóły w dzienniku zdarzeń przy użyciu funkcji [ReportEvent](/windows/win32/api/winbase/nf-winbase-reporteventw). Jeśli żadna usługa nie jest uruchomiona, ciąg jest wysyłany do konsoli.

## <a name="catlservicemoduletm_bservice"></a><a name="m_bservice"></a>CAtlServiceModuleT::m_bService

Flaga wskazująca, że program jest uruchomiony jako usługa.

```
BOOL m_bService;
```

### <a name="remarks"></a>Uwagi

Służy do odróżniania exe usługi od exe aplikacji.

## <a name="catlservicemoduletm_dwthreadid"></a><a name="m_dwthreadid"></a>CAtlServiceModuleT::m_dwThreadID

Zmienna elementu członkowskiego przechowujący identyfikator wątku usługi.

```
DWORD m_dwThreadID;
```

### <a name="remarks"></a>Uwagi

Ta zmienna przechowuje identyfikator wątku bieżącego wątku.

## <a name="catlservicemoduletm_hservicestatus"></a><a name="m_hservicestatus"></a>CAtlServiceModuleT::m_hServiceStatus

Zmienna elementu członkowskiego przechowująca dojście do struktury informacji o stanie dla bieżącej usługi.

```
SERVICE_STATUS_HANDLE m_hServiceStatus;
```

### <a name="remarks"></a>Uwagi

Struktura [SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) zawiera informacje o usłudze.

## <a name="catlservicemoduletm_status"></a><a name="m_status"></a>CAtlServiceModuleT::m_status

Zmienna elementu członkowskiego przechowująca strukturę informacji o stanie dla bieżącej usługi.

```
SERVICE_STATUS m_status;
```

### <a name="remarks"></a>Uwagi

Struktura [SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) zawiera informacje o usłudze.

## <a name="catlservicemoduletm_szservicename"></a><a name="m_szservicename"></a>CAtlServiceModuleT::m_szServiceName

Nazwa usługi jest rejestrowana.

```
TCHAR [256] m_szServiceName;
```

### <a name="remarks"></a>Uwagi

Ciąg zakończony zerem, który przechowuje nazwę usługi.

## <a name="catlservicemoduletoncontinue"></a><a name="oncontinue"></a>CAtlServiceModuleT::OnContinue

Zastąpuj tę metodę, aby kontynuować usługę.

```
void OnContinue() throw();
```

## <a name="catlservicemoduletoninterrogate"></a><a name="oninterrogate"></a>CAtlServiceModuleT::OnInterrogate

Zastąpuj tę metodę, aby przesłuchiwać usługę.

```
void OnInterrogate() throw();
```

## <a name="catlservicemoduletonpause"></a><a name="onpause"></a>CAtlServiceModuleT::OnPause

Zastąpuj tę metodę, aby wstrzymać usługę.

```
void OnPause() throw();
```

## <a name="catlservicemoduletonshutdown"></a><a name="onshutdown"></a>CAtlServiceModuleT::OnShutdown

Zastąpuj tę metodę, aby zamknąć usługę.

```
void OnShutdown() throw();
```

## <a name="catlservicemoduletonstop"></a><a name="onstop"></a>CAtlServiceModuleT::OnStop

Zastąpuj tę metodę, aby zatrzymać usługę.

```
void OnStop() throw();
```

## <a name="catlservicemoduletonunknownrequest"></a><a name="onunknownrequest"></a>CAtlServiceModuleT::OnUnknownRequest

Zastąpuj tę metodę do obsługi nieznanych żądań do usługi.

```
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```

### <a name="parameters"></a>Parametry

*dwOpcode (kod)*<br/>
Zarezerwowany.

## <a name="catlservicemoduletparsecommandline"></a><a name="parsecommandline"></a>CAtlServiceModuleT::ParseCommandLine

Analizuje wiersz polecenia i w razie potrzeby wykonuje rejestrację.

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Parametry

*lpCmdLine (linia lpCmdLine)*<br/>
Wiersz polecenia.

*Kod pnRet*<br/>
HRESULT odpowiadający rejestracji (jeśli miała miejsce).

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true na sukces lub false, jeśli plik RGS dostarczone w wierszu polecenia nie może być zarejestrowany.

### <a name="remarks"></a>Uwagi

Analizuje wiersz polecenia i rejestruje lub wyrejestrowyje dostarczony plik RGS, jeśli to konieczne. Ta metoda wywołuje [CAtlExeModuleT::ParseCommandLine,](../../atl/reference/catlexemodulet-class.md#parsecommandline) aby **sprawdzić/RegServer** i **/UnregServer**. Dodanie argumentu **-/Service** spowoduje zarejestrowanie usługi.

## <a name="catlservicemoduletpremessageloop"></a><a name="premessageloop"></a>CAtlServiceModuleT::PreMessageLoop

Ta metoda jest wywoływana bezpośrednio przed wprowadzeniem pętli komunikatów.

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Ten parametr jest przekazywany do [CAtlExeModuleT::PreMessageLoop](../../atl/reference/catlexemodulet-class.md#premessageloop).

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby dodać niestandardowy kod inicjowania usługi.

## <a name="catlservicemoduletregisterappid"></a><a name="registerappid"></a>CAtlServiceModuleT::RegisterAppId

Rejestruje usługę w rejestrze.

```
inline HRESULT RegisterAppId(bool bService = false) throw();
```

### <a name="parameters"></a>Parametry

*bSługa*<br/>
Musi być prawdziwe, aby zarejestrować się jako usługa.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="catlservicemoduletrun"></a><a name="run"></a>CAtlServiceModuleT::Uruchom

Uruchamia usługę.

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Określa sposób pokazywany okna. Ten parametr może być jedną z wartości omówionych w sekcji [WinMain.](/windows/win32/api/winbase/nf-winbase-winmain) Wartość domyślna to SW_HIDE.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Po wywołaniu `Run` wywołuje [CAtlServiceModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::RunMessageLoop](../../atl/reference/catlexemodulet-class.md#runmessageloop)i [CAtlExeModuleT::PostMessageLoop](../../atl/reference/catlexemodulet-class.md#postmessageloop).

## <a name="catlservicemoduletservicemain"></a><a name="servicemain"></a>CAtlServiceModuleT::ServiceMain

Ta metoda jest wywoływana przez Menedżera sterowania usługami.

```
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```

### <a name="parameters"></a>Parametry

*dwArgc (dwArgc)*<br/>
Argument argc.

*lpszArgv*<br/>
Argument argv.

### <a name="remarks"></a>Uwagi

Menedżer sterowania usługami (SCM) wywołuje `ServiceMain` po otwarciu aplikacji Usługi w Panelu sterowania, wybierz usługę i kliknij przycisk Start.

Po wywołaniu `ServiceMain`SCM usługa musi dać funkcji obsługi SCM. Ta funkcja umożliwia SCM uzyskać stan usługi i przekazać określone instrukcje (takie jak wstrzymywanie lub zatrzymywanie). Następnie [CAtlServiceModuleT::Run](#run) jest wywoływana do wykonywania głównej pracy usługi. `Run`kontynuuje wykonywanie do momentu zatrzymania usługi.

## <a name="catlservicemoduletsetservicestatus"></a><a name="setservicestatus"></a>CAtlServiceModuleT::SetServiceStatus

Ta metoda aktualizuje stan usługi.

```
void SetServiceStatus(DWORD dwState) throw();
```

### <a name="parameters"></a>Parametry

*dwPaństwo*<br/>
Nowy stan. Zobacz [SetServiceStatus](/windows/win32/api/winsvc/nf-winsvc-setservicestatus) dla możliwych wartości.

### <a name="remarks"></a>Uwagi

Aktualizuje informacje o stanie usługi menedżera sterowania usługami. Jest wywoływana przez [CAtlServiceModuleT::Run](#run), [CAtlServiceModuleT::ServiceMain](#servicemain) i innych metod obsługi. Stan jest również przechowywany w zmiennej członkowskiej [CAtlServiceModuleT::m_status](#m_status).

## <a name="catlservicemoduletstart"></a><a name="start"></a>CAtlServiceModuleT::Start

Wywoływana `CAtlServiceModuleT::WinMain` przez po uruchomieniu usługi.

```
HRESULT Start(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Określa sposób pokazywany okna. Ten parametr może być jedną z wartości omówionych w sekcji [WinMain.](/windows/win32/api/winbase/nf-winbase-winmain)

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

[Metoda CAtlServiceModuleT::WinMain](#winmain) obsługuje zarówno rejestrację, jak i instalację, a także zadania związane z usuwaniem wpisów rejestru i odinstalowywaniem modułu. Po uruchomieniu usługi `WinMain` wywołaj . `Start`

## <a name="catlservicemoduletuninstall"></a><a name="uninstall"></a>CAtlServiceModuleT::Odinstaluj

Zatrzymuje i usuwa usługę.

```
BOOL Uninstall() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Zatrzymuje uruchomienie usługi i usuwa ją z bazy danych Programu Service Control Manager.

## <a name="catlservicemoduletunlock"></a><a name="unlock"></a>CAtlServiceModuleT::Odblokuj

Zmniejsza liczbę blokad usługi.

```
LONG Unlock() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę blokad, które mogą być przydatne do diagnostyki i debugowania.

## <a name="catlservicemoduletunregisterappid"></a><a name="unregisterappid"></a>CAtlServiceModuleT::Wyrównaj wyrejestrowy

Usuwa usługę z rejestru.

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="catlservicemoduletwinmain"></a><a name="winmain"></a>CAtlServiceModuleT::WinMain

Ta metoda implementuje kod wymagany do uruchomienia usługi.

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Określa sposób pokazywany okna. Ten parametr może być jedną z wartości omówionych w sekcji [WinMain.](/windows/win32/api/winbase/nf-winbase-winmain)

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość zwracaną usługi.

### <a name="remarks"></a>Uwagi

Ta metoda przetwarza wiersz polecenia (z [CAtlServiceModuleT::ParseCommandLine),](#parsecommandline)a następnie uruchamia usługę (przy użyciu [CAtlServiceModuleT::Start](#start)).

## <a name="see-also"></a>Zobacz też

[Klasa CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
