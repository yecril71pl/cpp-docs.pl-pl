---
title: Klasa Funkcja CAtlServiceModuleT
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
ms.openlocfilehash: 2854d0902700b268383eca094bed35843ea73272
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418035"
---
# <a name="catlservicemodulet-class"></a>Klasa Funkcja CAtlServiceModuleT

Ta klasa implementuje usługę.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T, UINT nServiceNameID>
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```

#### <a name="parameters"></a>Parametry

*&*<br/>
Klasa pochodna od `CAtlServiceModuleT`.

*nServiceNameID*<br/>
Identyfikator zasobu usługi.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Funkcja CAtlServiceModuleT:: Funkcja CAtlServiceModuleT](#catlservicemodulet)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Funkcja CAtlServiceModuleT:: Handler](#handler)|Procedura obsługi dla usługi.|
|[Funkcja CAtlServiceModuleT:: InitializeSecurity](#initializesecurity)|Udostępnia domyślne ustawienia zabezpieczeń usługi.|
|[Funkcja CAtlServiceModuleT:: Install](#install)|Instaluje i tworzy usługę.|
|[Funkcja CAtlServiceModuleT:: IsInstalled](#isinstalled)|Potwierdza, że usługa została zainstalowana.|
|[Funkcja CAtlServiceModuleT:: metody LogEvent](#logevent)|Zapisuje dane w dzienniku zdarzeń.|
|[Funkcja CAtlServiceModuleT:: OnContinue](#oncontinue)|Zastąp tę metodę, aby kontynuować działanie usługi.|
|[Funkcja CAtlServiceModuleT:: OnInterrogate](#oninterrogate)|Zastąp tę metodę, aby przejrzeć usługę.|
|[Funkcja CAtlServiceModuleT:: OnPause](#onpause)|Zastąp tę metodę, aby wstrzymać usługę.|
|[Funkcja CAtlServiceModuleT:: OnShutdown](#onshutdown)|Zastąp tę metodę, aby zamknąć usługę|
|[Funkcja CAtlServiceModuleT:: OnStop](#onstop)|Zastąp tę metodę, aby zatrzymać usługę|
|[Funkcja CAtlServiceModuleT:: OnUnknownRequest](#onunknownrequest)|Zastąp tę metodę, aby obsłużyć nieznane żądania do usługi|
|[Funkcja CAtlServiceModuleT::P arseCommandLine](#parsecommandline)|Analizuje wiersz polecenia i przeprowadza rejestrację w razie potrzeby.|
|[Funkcja CAtlServiceModuleT::P reMessageLoop](#premessageloop)|Ta metoda jest wywoływana bezpośrednio przed wprowadzeniem pętli komunikatów.|
|[Funkcja CAtlServiceModuleT:: RegisterAppId](#registerappid)|Rejestruje usługę w rejestrze.|
|[Funkcja CAtlServiceModuleT:: Run](#run)|Uruchamia usługę.|
|[Funkcja CAtlServiceModuleT:: ServiceMain](#servicemain)|Metoda wywoływana przez menedżera kontroli usług.|
|[Funkcja CAtlServiceModuleT:: SetServiceStatus](#setservicestatus)|Aktualizuje stan usługi.|
|[Funkcja CAtlServiceModuleT:: Start](#start)|Wywoływane przez `CAtlServiceModuleT::WinMain`, gdy usługa zostanie uruchomiona.|
|[Funkcja CAtlServiceModuleT:: Uninstall](#uninstall)|Powoduje zatrzymanie i usunięcie usługi.|
|[Funkcja CAtlServiceModuleT:: Unlock](#unlock)|Zmniejsza liczbę blokad usługi.|
|[Funkcja CAtlServiceModuleT:: UnregisterAppId](#unregisterappid)|Usuwa usługę z rejestru.|
|[Funkcja CAtlServiceModuleT:: WinMain](#winmain)|Ta metoda implementuje kod wymagany do uruchomienia usługi.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Funkcja CAtlServiceModuleT:: m_bService](#m_bservice)|Flaga wskazująca, że program jest uruchomiony jako usługa.|
|[Funkcja CAtlServiceModuleT:: m_dwThreadID](#m_dwthreadid)|Zmienna członkowska przechowująca identyfikator wątku.|
|[Funkcja CAtlServiceModuleT:: m_hServiceStatus](#m_hservicestatus)|Zmienna członkowska przechowująca dojście do struktury informacji o stanie dla bieżącej usługi.|
|[Funkcja CAtlServiceModuleT:: m_status](#m_status)|Zmienna członkowska przechowująca strukturę informacji o stanie dla bieżącej usługi.|
|[Funkcja CAtlServiceModuleT:: m_szServiceName](#m_szservicename)|Nazwa rejestrowanej usługi.|

## <a name="remarks"></a>Uwagi

`CAtlServiceModuleT`pochodzący z [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md), implementuje moduł usługi ATL. `CAtlServiceModuleT` udostępnia metody przetwarzania, instalowania, rejestrowania i usuwania wiersza polecenia. Jeśli wymagane są dodatkowe funkcje, te i inne metody można przesłonić.

Ta klasa zastępuje przestarzałą [klasę CComModule](../../atl/reference/ccommodule-class.md) używaną we wcześniejszych wersjach ATL. Zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)

`CAtlServiceModuleT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

##  <a name="catlservicemodulet"></a>Funkcja CAtlServiceModuleT:: Funkcja CAtlServiceModuleT

Konstruktor.

```
CAtlServiceModuleT() throw();
```

### <a name="remarks"></a>Uwagi

Inicjuje składowe danych i ustawia początkowy stan usługi.

##  <a name="handler"></a>Funkcja CAtlServiceModuleT:: Handler

Procedura obsługi dla usługi.

```
void Handler(DWORD dwOpcode) throw();
```

### <a name="parameters"></a>Parametry

*dwOpcode*<br/>
Przełącznik, który definiuje operację programu obsługi. Aby uzyskać szczegółowe informacje, zobacz uwagi.

### <a name="remarks"></a>Uwagi

Jest to kod, który Menedżer kontroli usług (SCM) może pobrać stan usługi i wydać instrukcje, takie jak stopnie lub wstrzymanie. Menedżer SCM przekazuje kod operacji przedstawiony poniżej, aby `Handler` wskazać, co usługa powinna wykonać.

|Kod operacji|Znaczenie|
|--------------------|-------------|
|SERVICE_CONTROL_STOP|Powoduje zatrzymanie usługi. Zastąp metodę [Funkcja CAtlServiceModuleT:: OnStop](#onstop) w atlbase. h, aby zmienić zachowanie.|
|SERVICE_CONTROL_PAUSE|Wdrożony przez użytkownika. Zastąp pustą metodę [Funkcja CAtlServiceModuleT:: OnPause](#onpause) in atlbase. h, aby wstrzymać usługę.|
|SERVICE_CONTROL_CONTINUE|Wdrożony przez użytkownika. Przesłoń pustą metodę [Funkcja CAtlServiceModuleT:: OnContinue](#oncontinue) w atlbase. h, aby kontynuować usługę.|
|SERVICE_CONTROL_INTERROGATE|Wdrożony przez użytkownika. Zastąp pustą metodę [Funkcja CAtlServiceModuleT:: OnInterrogate](#oninterrogate) w atlbase. h, aby przejrzeć usługę.|
|SERVICE_CONTROL_SHUTDOWN|Wdrożony przez użytkownika. Przesłoń pustą metodę [Funkcja CAtlServiceModuleT:: OnShutdown](#onshutdown) w atlbase. h, aby zamknąć usługę.|

Jeśli kod operacji nie zostanie rozpoznany, wywoływana jest metoda [Funkcja CAtlServiceModuleT:: OnUnknownRequest](#onunknownrequest) .

Domyślna usługa wygenerowana przez ATL obsługuje tylko instrukcje Stop. Jeśli Menedżer SCM przejdzie do instrukcji zatrzymania, usługa nakazuje menedżerowi SCM, że program zostanie zatrzymany. Następnie usługa wywołuje `PostThreadMessage`, aby ogłosić komunikat zakończenia do samego siebie. Kończy pętlę komunikatów, a usługa zostanie ostatecznie ZAMKNIĘTA.

##  <a name="initializesecurity"></a>Funkcja CAtlServiceModuleT:: InitializeSecurity

Udostępnia domyślne ustawienia zabezpieczeń usługi.

```
HRESULT InitializeSecurity() throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Każda klasa, która pochodzi od `CAtlServiceModuleT` musi implementować tę metodę w klasie pochodnej.

Użyj uwierzytelniania na poziomie PKT, poziomu personifikacji RPC_C_IMP_LEVEL_IDENTIFY i odpowiedniego deskryptora zabezpieczeń o wartości innej niż null w wywołaniu `CoInitializeSecurity`.

W przypadku nieprzypisanych do kreatora projektów usług, będzie to w

[!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]

W przypadku projektów usług mających atrybut

[!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]

##  <a name="install"></a>Funkcja CAtlServiceModuleT:: Install

Instaluje i tworzy usługę.

```
BOOL Install() throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Instaluje usługę w bazie danych Menedżera sterowania usługami (SCM), a następnie tworzy obiekt usługi. Jeśli nie można utworzyć usługi, wyświetlane jest okno komunikatu, a metoda zwraca wartość FALSE.

##  <a name="isinstalled"></a>Funkcja CAtlServiceModuleT:: IsInstalled

Potwierdza, że usługa została zainstalowana.

```
BOOL IsInstalled() throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość PRAWDA, jeśli usługa jest zainstalowana, w przeciwnym razie FALSE.

##  <a name="logevent"></a>Funkcja CAtlServiceModuleT:: metody LogEvent

Zapisuje dane w dzienniku zdarzeń.

```
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Ciąg do zapisu w dzienniku zdarzeń.

*...*<br/>
Opcjonalne dodatkowe ciągi do zapisania w dzienniku zdarzeń.

### <a name="remarks"></a>Uwagi

Ta metoda zapisuje szczegóły w dzienniku zdarzeń przy użyciu funkcji [ReportEvent](/windows/win32/api/winbase/nf-winbase-reporteventw). Jeśli żadna usługa nie jest uruchomiona, ciąg jest wysyłany do konsoli.

##  <a name="m_bservice"></a>Funkcja CAtlServiceModuleT:: m_bService

Flaga wskazująca, że program jest uruchomiony jako usługa.

```
BOOL m_bService;
```

### <a name="remarks"></a>Uwagi

Służy do rozróżniania pliku EXE usługi z poziomu pliku WYKONYWALNego aplikacji.

##  <a name="m_dwthreadid"></a>Funkcja CAtlServiceModuleT:: m_dwThreadID

Zmienna członkowska przechowująca identyfikator wątku usługi.

```
DWORD m_dwThreadID;
```

### <a name="remarks"></a>Uwagi

Ta zmienna przechowuje identyfikator wątku bieżącego wątku.

##  <a name="m_hservicestatus"></a>Funkcja CAtlServiceModuleT:: m_hServiceStatus

Zmienna członkowska przechowująca dojście do struktury informacji o stanie dla bieżącej usługi.

```
SERVICE_STATUS_HANDLE m_hServiceStatus;
```

### <a name="remarks"></a>Uwagi

Struktura [SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) zawiera informacje o usłudze.

##  <a name="m_status"></a>Funkcja CAtlServiceModuleT:: m_status

Zmienna członkowska przechowująca strukturę informacji o stanie dla bieżącej usługi.

```
SERVICE_STATUS m_status;
```

### <a name="remarks"></a>Uwagi

Struktura [SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) zawiera informacje o usłudze.

##  <a name="m_szservicename"></a>Funkcja CAtlServiceModuleT:: m_szServiceName

Nazwa rejestrowanej usługi.

```
TCHAR [256] m_szServiceName;
```

### <a name="remarks"></a>Uwagi

Ciąg zakończony znakiem null, który przechowuje nazwę usługi.

##  <a name="oncontinue"></a>Funkcja CAtlServiceModuleT:: OnContinue

Zastąp tę metodę, aby kontynuować działanie usługi.

```
void OnContinue() throw();
```

##  <a name="oninterrogate"></a>Funkcja CAtlServiceModuleT:: OnInterrogate

Zastąp tę metodę, aby przejrzeć usługę.

```
void OnInterrogate() throw();
```

##  <a name="onpause"></a>Funkcja CAtlServiceModuleT:: OnPause

Zastąp tę metodę, aby wstrzymać usługę.

```
void OnPause() throw();
```

##  <a name="onshutdown"></a>Funkcja CAtlServiceModuleT:: OnShutdown

Zastąp tę metodę, aby zamknąć usługę.

```
void OnShutdown() throw();
```

##  <a name="onstop"></a>Funkcja CAtlServiceModuleT:: OnStop

Zastąp tę metodę, aby zatrzymać usługę.

```
void OnStop() throw();
```

##  <a name="onunknownrequest"></a>Funkcja CAtlServiceModuleT:: OnUnknownRequest

Zastąp tę metodę, aby obsłużyć nieznane żądania do usługi.

```
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```

### <a name="parameters"></a>Parametry

*dwOpcode*<br/>
Rezerwacj.

##  <a name="parsecommandline"></a>Funkcja CAtlServiceModuleT::P arseCommandLine

Analizuje wiersz polecenia i przeprowadza rejestrację w razie potrzeby.

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Parametry

*lpCmdLine*<br/>
Wiersz polecenia.

*pnRetCode*<br/>
WYNIK HRESULT odpowiadający rejestracji (jeśli miało miejsce).

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość true dla sukcesu lub false, jeśli nie można zarejestrować pliku RGS w wierszu polecenia.

### <a name="remarks"></a>Uwagi

Analizuje wiersz polecenia i rejestruje lub wyrejestrowuje podany plik RGS w razie potrzeby. Ta metoda wywołuje [CAtlExeModuleT::P arsecommandline](../../atl/reference/catlexemodulet-class.md#parsecommandline) , aby sprawdzić, czy jest to **/regserver** i **przełącznikiem/unregserver**. Dodanie argumentu **-/Service** spowoduje zarejestrowanie usługi.

##  <a name="premessageloop"></a>Funkcja CAtlServiceModuleT::P reMessageLoop

Ta metoda jest wywoływana bezpośrednio przed wprowadzeniem pętli komunikatów.

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Ten parametr jest przesyłany do [CAtlExeModuleT::P remessageloop](../../atl/reference/catlexemodulet-class.md#premessageloop).

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby dodać niestandardowy kod inicjujący dla usługi.

##  <a name="registerappid"></a>Funkcja CAtlServiceModuleT:: RegisterAppId

Rejestruje usługę w rejestrze.

```
inline HRESULT RegisterAppId(bool bService = false) throw();
```

### <a name="parameters"></a>Parametry

*bService*<br/>
Aby zarejestrować się jako usługa, należy mieć wartość true.

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

##  <a name="run"></a>Funkcja CAtlServiceModuleT:: Run

Uruchamia usługę.

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Określa sposób wyświetlania okna. Ten parametr może być jedną z wartości omówionych w sekcji [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) . Wartość domyślna to SW_HIDE.

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Po wywołaniu `Run` wywołuje [Funkcja CAtlServiceModuleT::P remessageloop](#premessageloop), [CAtlExeModuleT:: RunMessageLoop](../../atl/reference/catlexemodulet-class.md#runmessageloop)i [CAtlExeModuleT::P ostmessageloop](../../atl/reference/catlexemodulet-class.md#postmessageloop).

##  <a name="servicemain"></a>Funkcja CAtlServiceModuleT:: ServiceMain

Ta metoda jest wywoływana przez menedżera kontroli usług.

```
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```

### <a name="parameters"></a>Parametry

*dwArgc*<br/>
Argument argc.

*lpszArgv*<br/>
Argument argv.

### <a name="remarks"></a>Uwagi

Wywołania Menedżera sterowania usługami (SCM) `ServiceMain` po otwarciu aplikacji usług w panelu sterowania wybierz usługę, a następnie kliknij przycisk Uruchom.

Po `ServiceMain`wywołań SCM usługa musi udzielić funkcji programu obsługi SCM. Ta funkcja umożliwia menedżerowi SCM uzyskanie stanu usługi i przekazywanie określonych instrukcji (takich jak Wstrzymywanie lub zatrzymywanie). Następnie [Funkcja CAtlServiceModuleT:: Run](#run) jest wywoływana w celu wykonania głównej pracy usługi. `Run` nadal wykonywane, dopóki usługa nie zostanie zatrzymana.

##  <a name="setservicestatus"></a>Funkcja CAtlServiceModuleT:: SetServiceStatus

Ta metoda aktualizuje stan usługi.

```
void SetServiceStatus(DWORD dwState) throw();
```

### <a name="parameters"></a>Parametry

*dwState*<br/>
Nowy stan. Zobacz [SetServiceStatus](/windows/win32/api/winsvc/nf-winsvc-setservicestatus) , aby uzyskać możliwe wartości.

### <a name="remarks"></a>Uwagi

Aktualizuje informacje o stanie Menedżera kontroli usług dla usługi. Jest on wywoływany przez [Funkcja CAtlServiceModuleT:: Run](#run), [Funkcja CAtlServiceModuleT:: ServiceMain](#servicemain) i innych metod obsługi. Stan jest również przechowywany w zmiennej składowej [Funkcja CAtlServiceModuleT:: m_status](#m_status).

##  <a name="start"></a>Funkcja CAtlServiceModuleT:: Start

Wywoływane przez `CAtlServiceModuleT::WinMain`, gdy usługa zostanie uruchomiona.

```
HRESULT Start(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Określa sposób wyświetlania okna. Ten parametr może być jedną z wartości omówionych w sekcji [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) .

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Metoda [Funkcja CAtlServiceModuleT:: WinMain](#winmain) obsługuje rejestrację i instalację, a także zadania związane z usuwaniem wpisów rejestru i odinstalowywaniem modułu. Gdy usługa jest uruchomiona, `WinMain` wywołuje `Start`.

##  <a name="uninstall"></a>Funkcja CAtlServiceModuleT:: Uninstall

Powoduje zatrzymanie i usunięcie usługi.

```
BOOL Uninstall() throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Uniemożliwia uruchomienie usługi i usuwa ją z bazy danych Menedżera sterowania usługami.

##  <a name="unlock"></a>Funkcja CAtlServiceModuleT:: Unlock

Zmniejsza liczbę blokad usługi.

```
LONG Unlock() throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca liczbę blokad, która może być przydatna w przypadku diagnostyki i debugowania.

##  <a name="unregisterappid"></a>Funkcja CAtlServiceModuleT:: UnregisterAppId

Usuwa usługę z rejestru.

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

##  <a name="winmain"></a>Funkcja CAtlServiceModuleT:: WinMain

Ta metoda implementuje kod wymagany do uruchomienia usługi.

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Określa sposób wyświetlania okna. Ten parametr może być jedną z wartości omówionych w sekcji [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) .

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość zwracaną przez usługę.

### <a name="remarks"></a>Uwagi

Ta metoda przetwarza wiersz polecenia (z [Funkcja CAtlServiceModuleT::P arsecommandline](#parsecommandline)), a następnie uruchamia usługę (przy użyciu [Funkcja CAtlServiceModuleT:: Start](#start)).

## <a name="see-also"></a>Zobacz też

[Klasa CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
