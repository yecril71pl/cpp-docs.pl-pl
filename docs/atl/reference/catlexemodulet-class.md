---
title: Klasa CAtlExeModuleT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAtlExeModuleT class
ms.assetid: 82245f3d-91d4-44fa-aa86-7cc7fbd758d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aa212a6a58d1de417035f002b2caf3e206dabf1c
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757588"
---
# <a name="catlexemodulet-class"></a>Klasa CAtlExeModuleT

Ta klasa reprezentuje modułu dla aplikacji.

## <a name="syntax"></a>Składnia

```
template <class T>  
class ATL_NO_VTABLE CAtlExeModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>Parametry

*T*  
Klasa jest pochodną `CAtlExeModuleT`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlExeModuleT::CAtlExeModuleT](#catlexemodulet)|Konstruktor.|
|[CAtlExeModuleT:: ~ CAtlExeModuleT](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlExeModuleT::InitializeCom](#initializecom)|Inicjuje COM.|
|[CAtlExeModuleT::ParseCommandLine](#parsecommandline)|Analizuje wiersz polecenia i wykonuje rejestrację, jeśli to konieczne.|
|[CAtlExeModuleT::PostMessageLoop](#postmessageloop)|Ta metoda jest wywoływana natychmiast po zakończeniu pętli komunikatów.|
|[CAtlExeModuleT::PreMessageLoop](#premessageloop)|Ta metoda jest wywoływana tuż przed wprowadzania pętli komunikatów.|
|[CAtlExeModuleT::RegisterClassObjects](#registerclassobjects)|Rejestruje obiekt klasy.|
|[CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects)|Odwołuje obiektu klasy.|
|[CAtlExeModuleT::Run](#run)|Ta metoda wykonuje kod w module EXE, aby zainicjować, uruchom pętli komunikatów i wyczyścić.|
|[CAtlExeModuleT::RunMessageLoop](#runmessageloop)|Ta metoda jest wykonywana pętli komunikatów.|
|[CAtlExeModuleT::UninitializeCom](#uninitializecom)|Deinicjuje modelu COM.|
|[CAtlExeModuleT::Unlock](#unlock)|Zmniejsza liczbę blokad modułu.|
|[CAtlExeModuleT::WinMain](#winmain)|Ta metoda implementuje kodu wymaganego do uruchomienia pliku EXE.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown)|Flaga wskazująca, czy ma być opóźnienie zamykania modułu.|
|[CAtlExeModuleT::m_dwPause](#m_dwpause)|Wartość Wstrzymaj używane w celu zapewnienia, że wszystkie obiekty są wydawane przed zamknięciem.|
|[CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout)|Wartość limitu czasu, które umożliwia opóźnienie zwalnianie modułu.|

## <a name="remarks"></a>Uwagi

`CAtlExeModuleT` reprezentuje moduł dla aplikacji (z rozszerzeniem EXE) i zawiera kod, który obsługuje tworzenie pliku EXE, przetwarzania wiersza polecenia, rejestrowanie obiektów klasy, systemem pętli komunikatów i oczyszczanie przy zamykaniu.

Ta klasa jest przeznaczona do zwiększenia wydajności w przypadku obiektów COM w serwerze EXE ciągle są tworzone i niszczone. Po wydaniu ostatni obiekt COM, EXE czeka przez czas określony przez [CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout) element członkowski danych. Jeśli nie ma działania w tym okresie (oznacza to, że żadne obiekty COM są tworzone), jest inicjowane procesu zamykania.

[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown) element członkowski danych jest używany w celu określenia, w przypadku pliku EXE należy używać mechanizmu zdefiniowanych powyżej. Jeśli ma wartość false, moduł przestanie obowiązywać natychmiast.

Aby uzyskać więcej informacji na temat modułów ATL, zobacz [klasy modułów ATL](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_MODULE](atl-typedefs.md#_atl_module)  

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlExeModuleT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="catlexemodulet"></a>  CAtlExeModuleT::CAtlExeModuleT

Konstruktor.

```
CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Uwagi

Jeśli nie można zainicjować modułu EXE, WinMain natychmiast zwróci bez dalszego przetwarzania.

##  <a name="dtor"></a>  CAtlExeModuleT:: ~ CAtlExeModuleT

Destruktor.

```
~CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby.

##  <a name="initializecom"></a>  CAtlExeModuleT::InitializeCom

Inicjuje COM.

```
static HRESULT InitializeCom() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana z konstruktora i może zostać zastąpiona w celu zainicjować modelu COM w sposób inny niż domyślna implementacja. Domyślna implementacja albo wywołuje `CoInitializeEx(NULL, COINIT_MULTITHREADED)` lub `CoInitialize(NULL)` w zależności od konfiguracji projektu.

Zastąpienie tej metody zwykle wymaga zastępowanie [CAtlExeModuleT::UninitializeCom](#uninitializecom).

##  <a name="m_bdelayshutdown"></a>  CAtlExeModuleT::m_bDelayShutdown

Flaga wskazująca, czy ma być opóźnienie zamykania modułu.

```
bool m_bDelayShutdown;
```

### <a name="remarks"></a>Uwagi

Zobacz [Przegląd CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) Aby uzyskać szczegółowe informacje.

##  <a name="m_dwpause"></a>  CAtlExeModuleT::m_dwPause

Wartość Wstrzymaj używane w celu zapewnienia, że wszystkie obiekty stała się przed zamknięciem.

```
DWORD m_dwPause;
```

### <a name="remarks"></a>Uwagi

Zmień tę wartość po wywołaniu [CAtlExeModuleT::InitializeCom](#initializecom) można ustawić liczbę milisekund, używane jako wartość Wstrzymaj do zamykania serwera. Wartość domyślna to 1000 milisekund.

##  <a name="m_dwtimeout"></a>  CAtlExeModuleT::m_dwTimeOut

Wartość limitu czasu, które umożliwia opóźnienie zwalnianie modułu.

```
DWORD m_dwTimeOut;
```

### <a name="remarks"></a>Uwagi

Zmień tę wartość po wywołaniu [CAtlExeModuleT::InitializeCom](#initializecom) zdefiniować liczbę milisekund, używane jako wartość limitu czasu dla zamykanie serwera. Wartość domyślna to 5000 ms. Zobacz [Przegląd CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) Aby uzyskać więcej informacji.

##  <a name="parsecommandline"></a>  CAtlExeModuleT::ParseCommandLine

Analizuje wiersz polecenia i wykonuje rejestrację, jeśli to konieczne.

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Parametry

*lpCmdLine*  
Wiersza polecenia przekazywane do aplikacji.

*pnRetCode*  
Wartość HRESULT odpowiadający rejestracji (jeśli miało to miejsce).

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli aplikacja powinny nadal działać, w przeciwnym razie wartość false.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana z [CAtlExeModuleT::WinMain](#winmain) i może zostać zastąpiona w celu obsługi przełączniki wiersza polecenia. Sprawdza, czy domyślna implementacja **/regserver** i **/Unregserver** argumenty wiersza polecenia i wykonuje rejestrację lub wyrejestrowania.

##  <a name="postmessageloop"></a>  CAtlExeModuleT::PostMessageLoop

Ta metoda jest wywoływana natychmiast po zakończeniu pętli komunikatów.

```
HRESULT PostMessageLoop() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Zastępuje tę metodę do wykonywania oczyszczania aplikacji niestandardowych. Domyślna implementacja wywołuje [CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects).

##  <a name="premessageloop"></a>  CAtlExeModuleT::PreMessageLoop

Ta metoda jest wywoływana tuż przed wprowadzania pętli komunikatów.

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*  
Wartość przekazana jako *nShowCmd* parametru w WinMain.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Zastępuje tę metodę, aby dodać niestandardową inicjalizację kod aplikacji. Domyślna implementacja rejestruje obiektów klasy.

##  <a name="registerclassobjects"></a>  CAtlExeModuleT::RegisterClassObjects

Rejestruje obiektu klasy OLE, dzięki czemu inne aplikacje mogą nawiązać z nim.

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Parametry

*dwClsContext*  
Określa kontekst, w którym ma być uruchamiane obiektu klasy. Możliwe wartości to CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER lub CLSCTX_LOCAL_SERVER.

*Flagidw*  
Określa typy połączeń do obiektu klasy. Możliwe wartości to REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE lub REGCLS_MULTI_SEPARATE.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK na sukces, S_FALSE, jeśli nie było żadnych klas, aby zarejestrować lub błąd HRESULT w przypadku niepowodzenia.

##  <a name="revokeclassobjects"></a>  CAtlExeModuleT::RevokeClassObjects

Usuwa obiekt klasy.

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK na sukces, S_FALSE, jeśli nie było żadnych klas, aby zarejestrować lub błąd HRESULT w przypadku niepowodzenia.

##  <a name="run"></a>  CAtlExeModuleT::Run

Ta metoda wykonuje kod w module EXE, aby zainicjować, uruchom pętli komunikatów i wyczyścić.

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*  
Określa, jak ma być wyświetlana okna. Ten parametr może być jedną z wartości omówione w [WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559) sekcji. Wartość domyślna to SW_HIDE.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda może zostać zastąpiona. Jednak w praktyce lepiej jest zastąpienie [CAtlExeModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::RunMessageLoop](#runmessageloop), lub [CAtlExeModuleT::PostMessageLoop](#postmessageloop) Zamiast tego.

##  <a name="runmessageloop"></a>  CAtlExeModuleT::RunMessageLoop

Ta metoda jest wykonywana pętli komunikatów.

```
void RunMessageLoop() throw();
```

### <a name="remarks"></a>Uwagi

Ta metoda może zostać zastąpiona w celu zmiany zachowania pętli komunikatów.

##  <a name="uninitializecom"></a>  CAtlExeModuleT::UninitializeCom

Deinicjuje modelu COM.

```
static void UninitializeCom() throw();
```

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda wywołuje po prostu [CoUninitialize](/windows/desktop/api/combaseapi/nf-combaseapi-couninitialize) i jest wywoływana z destruktora. Należy przesłonić tę metodę w razie przesłonięcia [CAtlExeModuleT::InitializeCom](#initializecom).

##  <a name="unlock"></a>  CAtlExeModuleT::Unlock

Zmniejsza liczbę blokad modułu.

```
LONG Unlock() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość, która może być użyteczna, diagnostykę lub testowania.

##  <a name="winmain"></a>  CAtlExeModuleT::WinMain

Ta metoda implementuje kodu wymaganego do uruchomienia pliku EXE.

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*  
Określa, jak ma być wyświetlana okna. Ten parametr może być jedną z wartości omówione w [WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559) sekcji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość zwracaną przez plik wykonywalny.

### <a name="remarks"></a>Uwagi

Ta metoda może zostać zastąpiona. Jeśli zastępują [CAtlExeModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::PostMessageLoop](#postmessageloop), lub [CAtlExeModuleT::RunMessageLoop](#runmessageloop) nie zapewnią dostateczną elastyczność , można zastąpić `WinMain` funkcji przy użyciu tej metody.

## <a name="see-also"></a>Zobacz też

[Przykładowe ATLDuck](../../visual-cpp-samples.md)   
[Klasa CAtlModuleT](../../atl/reference/catlmodulet-class.md)   
[Klasa CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)   
[Klasa — Przegląd](../../atl/atl-class-overview.md)
