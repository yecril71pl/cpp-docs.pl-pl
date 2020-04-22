---
title: Klasa CAtlExeModuleT
ms.date: 11/04/2016
f1_keywords:
- CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT::CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT::InitializeCom
- ATLBASE/ATL::CAtlExeModuleT::ParseCommandLine
- ATLBASE/ATL::CAtlExeModuleT::PostMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::PreMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::RegisterClassObjects
- ATLBASE/ATL::CAtlExeModuleT::RevokeClassObjects
- ATLBASE/ATL::CAtlExeModuleT::Run
- ATLBASE/ATL::CAtlExeModuleT::RunMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::UninitializeCom
- ATLBASE/ATL::CAtlExeModuleT::Unlock
- ATLBASE/ATL::CAtlExeModuleT::WinMain
- ATLBASE/ATL::CAtlExeModuleT::m_bDelayShutdown
- ATLBASE/ATL::CAtlExeModuleT::m_dwPause
- ATLBASE/ATL::CAtlExeModuleT::m_dwTimeOut
helpviewer_keywords:
- CAtlExeModuleT class
ms.assetid: 82245f3d-91d4-44fa-aa86-7cc7fbd758d9
ms.openlocfilehash: 33edd8f2483bc21ea6cf8b68f80a2501c37d1a40
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748750"
---
# <a name="catlexemodulet-class"></a>Klasa CAtlExeModuleT

Ta klasa reprezentuje moduł dla aplikacji.

## <a name="syntax"></a>Składnia

```
template <class T>
class ATL_NO_VTABLE CAtlExeModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa pochodzi `CAtlExeModuleT`od .

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlExeModuleT::CAtlExeModuleT](#catlexemodulet)|Konstruktor.|
|[CAtlExeModuleT::~CAtlExeModuleT](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlExeModuleT::InitializeCom](#initializecom)|Inicjuje com.|
|[CAtlExeModuleT::ParseCommandLine](#parsecommandline)|Analizuje wiersz polecenia i w razie potrzeby wykonuje rejestrację.|
|[CAtlExeModuleT::PostMessageLoop](#postmessageloop)|Ta metoda jest wywoływana natychmiast po zamknięciu pętli komunikatów.|
|[CAtlExeModuleT::PreMessageLoop](#premessageloop)|Ta metoda jest wywoływana bezpośrednio przed wprowadzeniem pętli komunikatów.|
|[CAtlExeModuleT::RegisterClassObjects](#registerclassobjects)|Rejestruje obiekt klasy.|
|[CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects)|Odwołuje obiekt klasy.|
|[CAtlExeModuleT::Uruchom](#run)|Ta metoda wykonuje kod w module EXE, aby zainicjować, uruchomić pętlę komunikatów i oczyścić.|
|[CAtlExeModuleT::RunMessageLoop](#runmessageloop)|Ta metoda wykonuje pętlę komunikatów.|
|[CAtlExeModuleT::UninitializeCom](#uninitializecom)|Uninitializes COM.|
|[CAtlExeModuleT::Odblokuj](#unlock)|Zmniejsza liczbę blokad modułu.|
|[CAtlExeModuleT::WinMain](#winmain)|Ta metoda implementuje kod wymagany do uruchomienia EXE.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown)|Flaga wskazująca, że powinno być opóźnienie zamknięcia modułu.|
|[CAtlExeModuleT::m_dwPause](#m_dwpause)|Wartość pauzy używana w celu zapewnienia, że wszystkie obiekty są zwalniane przed zamknięciem.|
|[CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout)|Wartość przesuwu używanego do opóźnienia rozładunku modułu.|

## <a name="remarks"></a>Uwagi

`CAtlExeModuleT`reprezentuje moduł dla aplikacji (EXE) i zawiera kod, który obsługuje tworzenie EXE, przetwarzanie wiersza polecenia, rejestrowanie obiektów klasy, uruchamianie pętli komunikatów i czyszczenie przy wyjściu.

Ta klasa ma na celu zwiększenie wydajności, gdy obiekty COM na serwerze EXE są stale tworzone i niszczone. Po wydaniu ostatniego obiektu COM exe czeka na czas określony przez [CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout) element członkowski danych. Jeśli w tym okresie nie ma żadnych działań (oznacza to, że nie są tworzone żadne obiekty COM), jest inicjowany proces zamykania.

[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown) data element członkowski jest flagą używaną do określenia, czy EXE należy użyć mechanizmu zdefiniowanego powyżej. Jeśli jest ustawiona na false, moduł zostanie natychmiast zakończony.

Aby uzyskać więcej informacji na temat modułów w ATL, zobacz [klasy modułów ATL](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[Catlmodule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlExeModuleT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="catlexemoduletcatlexemodulet"></a><a name="catlexemodulet"></a>CAtlExeModuleT::CAtlExeModuleT

Konstruktor.

```
CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Uwagi

Jeśli nie można zainicjować modułu EXE, winmain natychmiast powróci bez dalszego przetwarzania.

## <a name="catlexemoduletcatlexemodulet"></a><a name="dtor"></a>CAtlExeModuleT::~CAtlExeModuleT

Destruktor.

```
~CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby.

## <a name="catlexemoduletinitializecom"></a><a name="initializecom"></a>CAtlExeModuleT::InitializeCom

Inicjuje com.

```
static HRESULT InitializeCom() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana z konstruktora i może zostać zastąpiona w celu zainicjowania com w sposób inny niż domyślna implementacja. Domyślna implementacja `CoInitializeEx(NULL, COINIT_MULTITHREADED)` wywołuje `CoInitialize(NULL)` lub w zależności od konfiguracji projektu.

Zastąpienie tej metody zwykle wymaga zastąpienia [CAtlExeModuleT::UninitializeCom](#uninitializecom).

## <a name="catlexemoduletm_bdelayshutdown"></a><a name="m_bdelayshutdown"></a>CAtlExeModuleT::m_bDelayShutdown

Flaga wskazująca, że powinno być opóźnienie zamknięcia modułu.

```
bool m_bDelayShutdown;
```

### <a name="remarks"></a>Uwagi

Zobacz [CAtlExeModuleT Omówienie, aby](../../atl/reference/catlexemodulet-class.md) uzyskać szczegółowe informacje.

## <a name="catlexemoduletm_dwpause"></a><a name="m_dwpause"></a>CAtlExeModuleT::m_dwPause

Wartość pauzy używana w celu upewnienia się, że wszystkie obiekty zniknęły przed zamknięciem.

```
DWORD m_dwPause;
```

### <a name="remarks"></a>Uwagi

Zmień tę wartość po wywołaniu [CAtlExeModuleT::InitializeCom,](#initializecom) aby ustawić liczbę milisekund używanych jako wartość pauzy do zamykania serwera. Wartość domyślna to 1000 milisekund.

## <a name="catlexemoduletm_dwtimeout"></a><a name="m_dwtimeout"></a>CAtlExeModuleT::m_dwTimeOut

Wartość przesuwu używanego do opóźnienia rozładunku modułu.

```
DWORD m_dwTimeOut;
```

### <a name="remarks"></a>Uwagi

Zmień tę wartość po wywołaniu [CAtlExeModuleT::InitializeCom,](#initializecom) aby zdefiniować liczbę milisekund używanych jako wartość przekroku czasu do zamykania serwera. Wartość domyślna to 5000 milisekund. Zobacz [Przegląd CAtlExeModuleT, aby](../../atl/reference/catlexemodulet-class.md) uzyskać więcej informacji.

## <a name="catlexemoduletparsecommandline"></a><a name="parsecommandline"></a>CAtlExeModuleT::ParseCommandLine

Analizuje wiersz polecenia i w razie potrzeby wykonuje rejestrację.

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Parametry

*lpCmdLine (linia lpCmdLine)*<br/>
Wiersz polecenia przekazany do aplikacji.

*Kod pnRet*<br/>
HRESULT odpowiadający rejestracji (jeśli miała miejsce).

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli aplikacja powinna nadal działać, w przeciwnym razie false.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana z [CAtlExeModuleT::WinMain](#winmain) i może być zastąpiona do obsługi przełączników wiersza polecenia. Domyślna implementacja sprawdza **/RegServer** i **/UnRegServer** argumenty wiersza polecenia i wykonuje rejestrację lub wyrejestrowanie.

## <a name="catlexemoduletpostmessageloop"></a><a name="postmessageloop"></a>CAtlExeModuleT::PostMessageLoop

Ta metoda jest wywoływana natychmiast po zamknięciu pętli komunikatów.

```
HRESULT PostMessageLoop() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Zastąpuj tę metodę, aby wykonać niestandardowe oczyszczanie aplikacji. Domyślna implementacja wywołuje [CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects).

## <a name="catlexemoduletpremessageloop"></a><a name="premessageloop"></a>CAtlExeModuleT::PreMessageLoop

Ta metoda jest wywoływana bezpośrednio przed wprowadzeniem pętli komunikatów.

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Wartość przekazana jako *parametr nShowCmd* w winmain.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby dodać niestandardowy kod inicjowania dla aplikacji. Domyślna implementacja rejestruje obiekty klasy.

## <a name="catlexemoduletregisterclassobjects"></a><a name="registerclassobjects"></a>CAtlExeModuleT::RegisterClassObjects

Rejestruje obiekt klasy z OLE, dzięki czemu inne aplikacje mogą się z nim łączyć.

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Parametry

*dwClsContext*<br/>
Określa kontekst, w którym ma być uruchamiany obiekt klasy. Możliwe wartości to CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER lub CLSCTX_LOCAL_SERVER.

*Dwflags*<br/>
Określa typy połączeń z obiektem klasy. Możliwe wartości to REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE lub REGCLS_MULTI_SEPARATE.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces, S_FALSE, jeśli nie było żadnych klas do zarejestrowania lub błąd HRESULT na niepowodzenie.

## <a name="catlexemoduletrevokeclassobjects"></a><a name="revokeclassobjects"></a>CAtlExeModuleT::RevokeClassObjects

Usuwa obiekt klasy.

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces, S_FALSE, jeśli nie było żadnych klas do zarejestrowania lub błąd HRESULT na niepowodzenie.

## <a name="catlexemoduletrun"></a><a name="run"></a>CAtlExeModuleT::Uruchom

Ta metoda wykonuje kod w module EXE, aby zainicjować, uruchomić pętlę komunikatów i oczyścić.

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Określa sposób pokazywany okna. Ten parametr może być jedną z wartości omówionych w sekcji [WinMain.](/windows/win32/api/winbase/nf-winbase-winmain) Domyślnie SW_HIDE.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta metoda może zostać zastąpiona. Jednak w praktyce lepiej jest zastąpić [CAtlExeModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::RunMessageLoop](#runmessageloop), lub [CAtlExeModuleT::PostMessageLoop](#postmessageloop) zamiast.

## <a name="catlexemoduletrunmessageloop"></a><a name="runmessageloop"></a>CAtlExeModuleT::RunMessageLoop

Ta metoda wykonuje pętlę komunikatów.

```cpp
void RunMessageLoop() throw();
```

### <a name="remarks"></a>Uwagi

Ta metoda może zostać zastąpiona, aby zmienić zachowanie pętli komunikatów.

## <a name="catlexemoduletuninitializecom"></a><a name="uninitializecom"></a>CAtlExeModuleT::UninitializeCom

Uninitializes COM.

```
static void UninitializeCom() throw();
```

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda po prostu wywołuje [CoUninitialize](/windows/win32/api/combaseapi/nf-combaseapi-couninitialize) i jest wywoływana z destruktora. Zastąp tę metodę, jeśli zastąpisz [CAtlExeModuleT::InitializeCom](#initializecom).

## <a name="catlexemoduletunlock"></a><a name="unlock"></a>CAtlExeModuleT::Odblokuj

Zmniejsza liczbę blokad modułu.

```
LONG Unlock() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość, która może być przydatna do diagnostyki lub testowania.

## <a name="catlexemoduletwinmain"></a><a name="winmain"></a>CAtlExeModuleT::WinMain

Ta metoda implementuje kod wymagany do uruchomienia EXE.

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Określa sposób pokazywany okna. Ten parametr może być jedną z wartości omówionych w sekcji [WinMain.](/windows/win32/api/winbase/nf-winbase-winmain)

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość zwracaną pliku wykonywalnego.

### <a name="remarks"></a>Uwagi

Ta metoda może zostać zastąpiona. Jeśli zastąpienie [CAtlExeModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::PostMessageLoop](#postmessageloop), lub [CAtlExeModuleT::RunMessageLoop](#runmessageloop) nie zapewnia wystarczającej elastyczności, możliwe jest zastąpienie `WinMain` funkcji przy użyciu tej metody.

## <a name="see-also"></a>Zobacz też

[Próbka ATLDuck](../../overview/visual-cpp-samples.md)<br/>
[Klasa CAtlModuleT](../../atl/reference/catlmodulet-class.md)<br/>
[Klasa CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
