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
ms.openlocfilehash: d37cc8e97d29cbedfeb4ba79502d44529485399f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418056"
---
# <a name="catlexemodulet-class"></a>Klasa CAtlExeModuleT

Ta klasa reprezentuje moduł aplikacji.

## <a name="syntax"></a>Składnia

```
template <class T>
class ATL_NO_VTABLE CAtlExeModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>Parametry

*&*<br/>
Klasa pochodna od `CAtlExeModuleT`.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CAtlExeModuleT::CAtlExeModuleT](#catlexemodulet)|Konstruktor.|
|[CAtlExeModuleT:: ~ CAtlExeModuleT](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CAtlExeModuleT::InitializeCom](#initializecom)|Inicjuje model COM.|
|[CAtlExeModuleT::P arseCommandLine](#parsecommandline)|Analizuje wiersz polecenia i przeprowadza rejestrację w razie potrzeby.|
|[CAtlExeModuleT::P ostMessageLoop](#postmessageloop)|Ta metoda jest wywoływana natychmiast po zakończeniu pętli komunikatów.|
|[CAtlExeModuleT::P reMessageLoop](#premessageloop)|Ta metoda jest wywoływana bezpośrednio przed wprowadzeniem pętli komunikatów.|
|[CAtlExeModuleT::RegisterClassObjects](#registerclassobjects)|Rejestruje obiekt klasy.|
|[CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects)|Odwołuje obiekt klasy.|
|[CAtlExeModuleT:: Run](#run)|Ta metoda wykonuje kod w module EXE, aby inicjować, uruchamiać pętlę komunikatów i czyścić.|
|[CAtlExeModuleT::RunMessageLoop](#runmessageloop)|Ta metoda wykonuje pętlę komunikatów.|
|[CAtlExeModuleT::UninitializeCom](#uninitializecom)|Inicjuje model COM.|
|[CAtlExeModuleT:: Unlock](#unlock)|Zmniejsza liczbę blokad modułu.|
|[CAtlExeModuleT:: WinMain](#winmain)|Ta metoda implementuje kod wymagany do uruchomienia pliku EXE.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CAtlExeModuleT:: m_bDelayShutdown](#m_bdelayshutdown)|Flaga wskazująca, że należy zamknąć moduł.|
|[CAtlExeModuleT:: m_dwPause](#m_dwpause)|Wartość wstrzymania używana do upewnienia się, że wszystkie obiekty zostały wydane przed zamknięciem.|
|[CAtlExeModuleT:: m_dwTimeOut](#m_dwtimeout)|Wartość limitu czasu używana do opóźniania zwalniania modułu.|

## <a name="remarks"></a>Uwagi

`CAtlExeModuleT` reprezentuje moduł aplikacji (EXE) i zawiera kod, który obsługuje tworzenie pliku EXE, przetwarzanie wiersza polecenia, rejestrowanie obiektów klasy, uruchamianie pętli komunikatów i czyszczenie przy zamykaniu.

Ta klasa została zaprojektowana w celu zwiększenia wydajności, gdy obiekty COM na serwerze EXE są ciągle tworzone i niszczone. Po wydaniu ostatniego obiektu COM, plik EXE czeka przez czas określony przez element członkowski danych [CAtlExeModuleT:: m_dwTimeOut](#m_dwtimeout) . Jeśli w tym okresie nie ma żadnych działań (oznacza to, że żadne obiekty COM nie są tworzone), proces zamykania zostanie zainicjowany.

Element członkowski danych [CAtlExeModuleT:: m_bDelayShutdown](#m_bdelayshutdown) jest flagą używaną do ustalenia, czy exe powinien używać mechanizmu zdefiniowanego powyżej. Jeśli wartość jest równa false, moduł zostanie natychmiast zakończony.

Aby uzyskać więcej informacji na temat modułów w ATL, zobacz [klasy modułów ATL](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlExeModuleT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

##  <a name="catlexemodulet"></a>CAtlExeModuleT::CAtlExeModuleT

Konstruktor.

```
CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Uwagi

Jeśli nie można zainicjować modułu EXE, WinMain natychmiast zwróci bez przetwarzania.

##  <a name="dtor"></a>CAtlExeModuleT:: ~ CAtlExeModuleT

Destruktor.

```
~CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzieloną zasoby.

##  <a name="initializecom"></a>CAtlExeModuleT::InitializeCom

Inicjuje model COM.

```
static HRESULT InitializeCom() throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana z konstruktora i można ją zastąpić, aby zainicjować COM w sposób inny niż domyślna. Domyślna implementacja to wywołania `CoInitializeEx(NULL, COINIT_MULTITHREADED)` lub `CoInitialize(NULL)` w zależności od konfiguracji projektu.

Zastąpienie tej metody zwykle wymaga przesłaniania [CAtlExeModuleT:: UninitializeCom](#uninitializecom).

##  <a name="m_bdelayshutdown"></a>CAtlExeModuleT:: m_bDelayShutdown

Flaga wskazująca, że należy zamknąć moduł.

```
bool m_bDelayShutdown;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [Omówienie usługi CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) .

##  <a name="m_dwpause"></a>CAtlExeModuleT:: m_dwPause

Wartość wstrzymania używana do upewnienia się, że wszystkie obiekty zostały utracone przed zamknięciem.

```
DWORD m_dwPause;
```

### <a name="remarks"></a>Uwagi

Zmień tę wartość po wywołaniu [CAtlExeModuleT:: InitializeCom](#initializecom) , aby ustawić liczbę milisekund użytą jako wartość wstrzymania na potrzeby zamykania serwera. Wartość domyślna to 1000 milisekund.

##  <a name="m_dwtimeout"></a>CAtlExeModuleT:: m_dwTimeOut

Wartość limitu czasu używana do opóźniania zwalniania modułu.

```
DWORD m_dwTimeOut;
```

### <a name="remarks"></a>Uwagi

Zmień tę wartość po wywołaniu [CAtlExeModuleT:: InitializeCom](#initializecom) , aby określić liczbę milisekund użytych jako wartość limitu czasu na potrzeby zamykania serwera. Wartość domyślna to 5000 milisekund. Aby uzyskać więcej informacji, zobacz [Omówienie CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) .

##  <a name="parsecommandline"></a>CAtlExeModuleT::P arseCommandLine

Analizuje wiersz polecenia i przeprowadza rejestrację w razie potrzeby.

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Parametry

*lpCmdLine*<br/>
Wiersz polecenia przeszedł do aplikacji.

*pnRetCode*<br/>
WYNIK HRESULT odpowiadający rejestracji (jeśli miało miejsce).

### <a name="return-value"></a>Wartość zwrócona

Zwróć wartość true, jeśli aplikacja powinna nadal działać, w przeciwnym razie false.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana z [CAtlExeModuleT:: WinMain](#winmain) i można ją zastąpić, aby obsługiwała przełączniki wiersza polecenia. Domyślna implementacja dla argumentów wiersza polecenia **/regserver** i **przełącznikiem/unregserver** i przeprowadza rejestrację lub Wyrejestrowanie.

##  <a name="postmessageloop"></a>CAtlExeModuleT::P ostMessageLoop

Ta metoda jest wywoływana natychmiast po zakończeniu pętli komunikatów.

```
HRESULT PostMessageLoop() throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby przeprowadzić oczyszczanie aplikacji niestandardowych. Domyślne wywołania implementacji [CAtlExeModuleT:: RevokeClassObjects](#revokeclassobjects).

##  <a name="premessageloop"></a>CAtlExeModuleT::P reMessageLoop

Ta metoda jest wywoływana bezpośrednio przed wprowadzeniem pętli komunikatów.

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Wartość przeniesiona jako parametr *nShowCmd* w WinMain.

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby dodać niestandardowy kod inicjujący dla aplikacji. Domyślna implementacja rejestruje obiekty klas.

##  <a name="registerclassobjects"></a>CAtlExeModuleT::RegisterClassObjects

Rejestruje obiekt klasy za pomocą OLE, tak aby inne aplikacje mogły się z nim połączyć.

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Parametry

*dwClsContext*<br/>
Określa kontekst, w którym obiekt klasy ma być uruchamiany. Możliwe wartości to CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER lub CLSCTX_LOCAL_SERVER.

*flagiDW*<br/>
Określa typy połączeń do obiektu klasy. Możliwe wartości to REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE lub REGCLS_MULTI_SEPARATE.

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK po powodzeniu, S_FALSE, jeśli nie ma żadnych klas do zarejestrowania, lub błąd HRESULT w przypadku niepowodzenia.

##  <a name="revokeclassobjects"></a>CAtlExeModuleT::RevokeClassObjects

Usuwa obiekt Class.

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK po powodzeniu, S_FALSE, jeśli nie ma żadnych klas do zarejestrowania, lub błąd HRESULT w przypadku niepowodzenia.

##  <a name="run"></a>CAtlExeModuleT:: Run

Ta metoda wykonuje kod w module EXE, aby inicjować, uruchamiać pętlę komunikatów i czyścić.

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Określa sposób wyświetlania okna. Ten parametr może być jedną z wartości omówionych w sekcji [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) . Wartość domyślna to SW_HIDE.

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Tę metodę można zastąpić. Jednakże w przypadku lepiej przesłonić [CAtlExeModuleT::P remessageloop](#premessageloop), [CAtlExeModuleT:: RunMessageLoop](#runmessageloop)lub [CAtlExeModuleT::P ostmessageloop](#postmessageloop) .

##  <a name="runmessageloop"></a>CAtlExeModuleT::RunMessageLoop

Ta metoda wykonuje pętlę komunikatów.

```
void RunMessageLoop() throw();
```

### <a name="remarks"></a>Uwagi

Tę metodę można zastąpić, aby zmienić zachowanie pętli komunikatów.

##  <a name="uninitializecom"></a>CAtlExeModuleT::UninitializeCom

Inicjuje model COM.

```
static void UninitializeCom() throw();
```

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda wywołuje [CoUninitialize](/windows/win32/api/combaseapi/nf-combaseapi-couninitialize) i jest wywoływana z destruktora. Zastąp tę metodę, jeśli zastąpisz [CAtlExeModuleT:: InitializeCom](#initializecom).

##  <a name="unlock"></a>CAtlExeModuleT:: Unlock

Zmniejsza liczbę blokad modułu.

```
LONG Unlock() throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość, która może być przydatna w przypadku diagnostyki lub testowania.

##  <a name="winmain"></a>CAtlExeModuleT:: WinMain

Ta metoda implementuje kod wymagany do uruchomienia pliku EXE.

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Określa sposób wyświetlania okna. Ten parametr może być jedną z wartości omówionych w sekcji [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) .

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość zwracaną przez plik wykonywalny.

### <a name="remarks"></a>Uwagi

Tę metodę można zastąpić. Jeśli przesłaniasz [CAtlExeModuleT::P remessageloop](#premessageloop), [CAtlExeModuleT::P ostmessageloop](#postmessageloop)lub [CAtlExeModuleT:: RunMessageLoop](#runmessageloop) nie zapewnia wystarczającej elastyczności, można przesłonić funkcję `WinMain` przy użyciu tej metody.

## <a name="see-also"></a>Zobacz też

[Przykład ATLDuck](../../overview/visual-cpp-samples.md)<br/>
[Klasa CAtlModuleT](../../atl/reference/catlmodulet-class.md)<br/>
[Klasa CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
