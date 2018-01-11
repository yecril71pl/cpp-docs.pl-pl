---
title: Klasa CAtlExeModuleT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords: CAtlExeModuleT class
ms.assetid: 82245f3d-91d4-44fa-aa86-7cc7fbd758d9
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c45b1f95aba4f11e6995bf5c4c1cfff00627e4b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="catlexemodulet-class"></a>Klasa CAtlExeModuleT
Ta klasa reprezentuje module dla aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>  
class ATL_NO_VTABLE CAtlExeModuleT : public CAtlModuleT<T>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Klasy pochodne `CAtlExeModuleT`.  
  
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
|[CAtlExeModuleT::PostMessageLoop](#postmessageloop)|Ta metoda jest wywoływana natychmiast po opuszcza pętlę komunikatów.|  
|[CAtlExeModuleT::PreMessageLoop](#premessageloop)|Ta metoda jest wywoływana bezpośrednio przed wprowadzania pętli komunikatów.|  
|[CAtlExeModuleT::RegisterClassObjects](#registerclassobjects)|Rejestruje obiekt klasy.|  
|[CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects)|Odwołuje się obiekt klasy.|  
|[CAtlExeModuleT::Run](#run)|Ta metoda wykonuje kod w module EXE, aby zainicjować, uruchom pętli komunikatów i wyczyścić.|  
|[CAtlExeModuleT::RunMessageLoop](#runmessageloop)|Ta metoda wykonuje pętlę komunikatów.|  
|[CAtlExeModuleT::UninitializeCom](#uninitializecom)|Uninitializes modelu COM.|  
|[CAtlExeModuleT::Unlock](#unlock)|Zmniejsza liczbę blokad modułu.|  
|[CAtlExeModuleT::WinMain](#winmain)|Ta metoda implementuje kod wymagany do uruchomienia pliku EXE.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown)|Flaga wskazująca, że powinny być opóźnienie zamykanie modułu.|  
|[CAtlExeModuleT::m_dwPause](#m_dwpause)|Wartość Wstrzymaj pozwala upewnić się, że wszystkie obiekty są wydawane zamknięcia systemu.|  
|[CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout)|Wartość limitu czasu można opóźnić zwalnianie modułu.|  
  
## <a name="remarks"></a>Uwagi  
 `CAtlExeModuleT`reprezentuje moduł dla aplikacji (EXE) i zawiera kod, który obsługuje tworzenie pliku EXE, przetwarzanie wiersza polecenia, rejestrowanie obiektów klasy, systemem pętli komunikatów i czyszczenie na wyjściu.  
  
 Ta klasa służy do zwiększenia wydajności, gdy obiekty COM na serwerze EXE stale są tworzone i niszczone. Po wydaniu ostatni obiekt COM, EXE czeka przez czas określony przez [CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout) element członkowski danych. Jeśli nic się nie dzieje podczas tego okresu (to znaczy, że żadne obiekty COM są tworzone), proces zamykania jest inicjowana.  
  
 [CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown) elementu członkowskiego danych jest używany w celu określenia, czy plik EXE powinny używać mechanizmu zdefiniowanych powyżej flagę. Jeśli ustawiono wartość false, moduł zostanie zakończona natychmiast.  
  
 Aby uzyskać więcej informacji o modułach w ATL, zobacz [klasy modułów ALT](../../atl/atl-module-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  

  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CAtlExeModuleT`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="catlexemodulet"></a>CAtlExeModuleT::CAtlExeModuleT  
 Konstruktor.  
  
```
CAtlExeModuleT() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nie można zainicjować modułu EXE, WinMain zwróci się natychmiast bez dalszego przetwarzania.  
  
##  <a name="dtor"></a>CAtlExeModuleT:: ~ CAtlExeModuleT  
 Destruktor.  
  
```
~CAtlExeModuleT() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie przydzielone zasoby.  
  
##  <a name="initializecom"></a>CAtlExeModuleT::InitializeCom  
 Inicjuje COM.  
  
```
static HRESULT InitializeCom() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana z konstruktora i może zostać zastąpiona w celu zainicjować modelu COM w sposób inny niż domyślna implementacja. Domyślna implementacja albo wywołuje **funkcja CoInitializeEx (wartość NULL, COINIT_MULTITHREADED)** lub **CoInitialize(NULL)** w zależności od konfiguracji projektu.  
  
 Zwykle przesłaniania tej metody wymaga zastępowanie [CAtlExeModuleT::UninitializeCom](#uninitializecom).  
  
##  <a name="m_bdelayshutdown"></a>CAtlExeModuleT::m_bDelayShutdown  
 Flaga wskazująca, że powinny być opóźnienie zamykanie modułu.  
  
```
bool m_bDelayShutdown;
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [omówienie CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) szczegółowe informacje.  
  
##  <a name="m_dwpause"></a>CAtlExeModuleT::m_dwPause  
 Wartość Wstrzymaj pozwala upewnić się, że wszystkie obiekty są usunięty zamknięcia systemu.  
  
```
DWORD m_dwPause;
```  
  
### <a name="remarks"></a>Uwagi  
 Zmień tę wartość po wywołaniu [CAtlExeModuleT::InitializeCom](#initializecom) można ustawić liczbę milisekund używany jako wartość Wstrzymaj do zamykania serwera. Wartość domyślna to 1000 milisekund.  
  
##  <a name="m_dwtimeout"></a>CAtlExeModuleT::m_dwTimeOut  
 Wartość limitu czasu można opóźnić zwalnianie modułu.  
  
```
DWORD m_dwTimeOut;
```  
  
### <a name="remarks"></a>Uwagi  
 Zmień tę wartość po wywołaniu [CAtlExeModuleT::InitializeCom](#initializecom) do definiowania wyrażony w milisekundach czas używany jako wartość limitu czasu dla zamykanie serwera. Wartość domyślna to 5000 ms. Zobacz [CAtlExeModuleT omówienie](../../atl/reference/catlexemodulet-class.md) więcej szczegółów.  
  
##  <a name="parsecommandline"></a>CAtlExeModuleT::ParseCommandLine  
 Analizuje wiersz polecenia i wykonuje rejestrację, jeśli to konieczne.  
  
```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpCmdLine`  
 W wierszu polecenia przekazane do aplikacji.  
  
 `pnRetCode`  
 Wynik HRESULT odpowiadającej rejestracji (jeśli miało to miejsce).  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true, jeśli aplikacja ma przejść do uruchomienia, w przeciwnym razie wartość false.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana z [CAtlExeModuleT::WinMain](#winmain) i może zostać zastąpiona w celu obsługi przełączniki wiersza polecenia. Sprawdza, czy domyślna implementacja **/regserver** i **/Unregserver** argumenty wiersza polecenia i wykonuje rejestracji lub wyrejestrowania.  
  
##  <a name="postmessageloop"></a>CAtlExeModuleT::PostMessageLoop  
 Ta metoda jest wywoływana natychmiast po opuszcza pętlę komunikatów.  
  
```
HRESULT PostMessageLoop() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę metodę, aby przeprowadzić czyszczenie aplikacji niestandardowej. Domyślna implementacja wywołuje [CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects).  
  
##  <a name="premessageloop"></a>CAtlExeModuleT::PreMessageLoop  
 Ta metoda jest wywoływana bezpośrednio przed wprowadzania pętli komunikatów.  
  
```
HRESULT PreMessageLoop(int nShowCmd) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nShowCmd`  
 Wartość przekazana jako `nShowCmd` parametru w WinMain.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę metodę, aby dodać niestandardową inicjalizację kod aplikacji. Domyślna implementacja rejestruje obiektów klasy.  
  
##  <a name="registerclassobjects"></a>CAtlExeModuleT::RegisterClassObjects  
 Rejestruje obiekt klasy OLE inne aplikacje do połączenia się do niego.  
  
```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *dwClsContext*  
 Określa kontekst, w którym ma być uruchomiona obiektu klasy. Możliwe wartości to CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER lub CLSCTX_LOCAL_SERVER.  
  
 `dwFlags`  
 Określa typy połączeń z obiektem klasy. Możliwe wartości to REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE lub REGCLS_MULTI_SEPARATE.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK sukces, wartości S_FALSE, jeśli nie było żadnych klas, aby zarejestrować lub błąd HRESULT w przypadku awarii.  
  
##  <a name="revokeclassobjects"></a>CAtlExeModuleT::RevokeClassObjects  
 Usuwa obiekt klasy.  
  
```
HRESULT RevokeClassObjects() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK sukces, wartości S_FALSE, jeśli nie było żadnych klas, aby zarejestrować lub błąd HRESULT w przypadku awarii.  
  
##  <a name="run"></a>CAtlExeModuleT::Run  
 Ta metoda wykonuje kod w module EXE, aby zainicjować, uruchom pętli komunikatów i wyczyścić.  
  
```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nShowCmd`  
 Określa, jaki ma być wyświetlana okna. Ten parametr może być jedna z wartości omówione w [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559) sekcji. Wartość domyślna to SW_HIDE.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda może zostać zastąpiona. Jednak w praktyce lepiej jest zastąpienie [CAtlExeModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::RunMessageLoop](#runmessageloop), lub [CAtlExeModuleT::PostMessageLoop](#postmessageloop) Zamiast tego.  
  
##  <a name="runmessageloop"></a>CAtlExeModuleT::RunMessageLoop  
 Ta metoda wykonuje pętlę komunikatów.  
  
```
void RunMessageLoop() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda może zostać zastąpiona w celu zmiany zachowania pętli komunikatów.  
  
##  <a name="uninitializecom"></a>CAtlExeModuleT::UninitializeCom  
 Uninitializes modelu COM.  
  
```
static void UninitializeCom() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta metoda wywołuje po prostu [CoUninitialize](http://msdn.microsoft.com/library/windows/desktop/ms688715) i jest wywoływana z destruktor. Zastępuje tę metodę w razie przesłonięcia [CAtlExeModuleT::InitializeCom](#initializecom).  
  
##  <a name="unlock"></a>CAtlExeModuleT::Unlock  
 Zmniejsza liczbę blokad modułu.  
  
```
LONG Unlock() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość, która może być przydatne w przypadku diagnostyki lub testowania.  
  
##  <a name="winmain"></a>CAtlExeModuleT::WinMain  
 Ta metoda implementuje kod wymagany do uruchomienia pliku EXE.  
  
```
int WinMain(int nShowCmd) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nShowCmd`  
 Określa, jaki ma być wyświetlana okna. Ten parametr może być jedna z wartości omówione w [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559) sekcji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość zwracaną przez plik wykonywalny.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda może zostać zastąpiona. Jeśli zastępowanie [CAtlExeModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::PostMessageLoop](#postmessageloop), lub [CAtlExeModuleT::RunMessageLoop](#runmessageloop) nie zapewnia elastyczność za mało , można zastąpić `WinMain` funkcji za pomocą tej metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe ATLDuck](../../visual-cpp-samples.md)   
 [Klasa CAtlModuleT](../../atl/reference/catlmodulet-class.md)   
 [Klasa CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
