---
title: Klasa CCmdTarget | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCmdTarget
- AFXWIN/CCmdTarget
- AFXWIN/CCmdTarget::CCmdTarget
- AFXWIN/CCmdTarget::BeginWaitCursor
- AFXWIN/CCmdTarget::DoOleVerb
- AFXWIN/CCmdTarget::EnableAutomation
- AFXWIN/CCmdTarget::EnableConnections
- AFXWIN/CCmdTarget::EnableTypeLib
- AFXWIN/CCmdTarget::EndWaitCursor
- AFXWIN/CCmdTarget::EnumOleVerbs
- AFXWIN/CCmdTarget::FromIDispatch
- AFXWIN/CCmdTarget::GetDispatchIID
- AFXWIN/CCmdTarget::GetIDispatch
- AFXWIN/CCmdTarget::GetTypeInfoCount
- AFXWIN/CCmdTarget::GetTypeInfoOfGuid
- AFXWIN/CCmdTarget::GetTypeLib
- AFXWIN/CCmdTarget::GetTypeLibCache
- AFXWIN/CCmdTarget::IsInvokeAllowed
- AFXWIN/CCmdTarget::IsResultExpected
- AFXWIN/CCmdTarget::OnCmdMsg
- AFXWIN/CCmdTarget::OnFinalRelease
- AFXWIN/CCmdTarget::RestoreWaitCursor
dev_langs:
- C++
helpviewer_keywords:
- CCmdTarget [MFC], CCmdTarget
- CCmdTarget [MFC], BeginWaitCursor
- CCmdTarget [MFC], DoOleVerb
- CCmdTarget [MFC], EnableAutomation
- CCmdTarget [MFC], EnableConnections
- CCmdTarget [MFC], EnableTypeLib
- CCmdTarget [MFC], EndWaitCursor
- CCmdTarget [MFC], EnumOleVerbs
- CCmdTarget [MFC], FromIDispatch
- CCmdTarget [MFC], GetDispatchIID
- CCmdTarget [MFC], GetIDispatch
- CCmdTarget [MFC], GetTypeInfoCount
- CCmdTarget [MFC], GetTypeInfoOfGuid
- CCmdTarget [MFC], GetTypeLib
- CCmdTarget [MFC], GetTypeLibCache
- CCmdTarget [MFC], IsInvokeAllowed
- CCmdTarget [MFC], IsResultExpected
- CCmdTarget [MFC], OnCmdMsg
- CCmdTarget [MFC], OnFinalRelease
- CCmdTarget [MFC], RestoreWaitCursor
ms.assetid: 8883b132-2057-4ce0-a5f2-88979f8f2b13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b6630ad9721b7a58e7da2660337660cc7916db01
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2018
ms.locfileid: "42466474"
---
# <a name="ccmdtarget-class"></a>CCmdTarget — klasa
Klasa bazowa dla architektury mapy wiadomości w bibliotece klas Microsoft Foundation.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CCmdTarget : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCmdTarget::CCmdTarget](#ccmdtarget)|Konstruuje `CCmdTarget` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCmdTarget::BeginWaitCursor](#beginwaitcursor)|Wyświetla kursora w postaci klepsydry kursora.|  
|[CCmdTarget::DoOleVerb](#dooleverb)|Powoduje, że określone przez zlecenia OLE do wykonania akcji.|  
|[CCmdTarget::EnableAutomation](#enableautomation)|Umożliwia automatyzację OLE dla `CCmdTarget` obiektu.|  
|[CCmdTarget::EnableConnections](#enableconnections)|Umożliwia inicjowanie zdarzeń za pośrednictwem punktów połączenia.|  
|[CCmdTarget::EnableTypeLib](#enabletypelib)|Włącza bibliotekę typów obiektu.|  
|[CCmdTarget::EndWaitCursor](#endwaitcursor)|Powrót do poprzedniego kursora.|  
|[CCmdTarget::EnumOleVerbs](#enumoleverbs)|Wylicza czasowniki OLE obiektu.|  
|[CCmdTarget::FromIDispatch](#fromidispatch)|Zwraca wskaźnik do `CCmdTarget` obiekt skojarzony z `IDispatch` wskaźnika.|  
|[CCmdTarget::GetDispatchIID](#getdispatchiid)|Pobiera identyfikator wysyłania podstawowego interfejsu.|  
|[CCmdTarget::GetIDispatch](#getidispatch)|Zwraca wskaźnik do `IDispatch` obiekt skojarzony z `CCmdTarget` obiektu.|  
|[CCmdTarget::GetTypeInfoCount](#gettypeinfocount)|Pobiera numer typu informacji interfejsy, które zawiera obiekt.|  
|[CCmdTarget::GetTypeInfoOfGuid](#gettypeinfoofguid)|Pobiera opis typu, który odpowiada określony identyfikator GUID.|  
|[CCmdTarget::GetTypeLib](#gettypelib)|Pobiera wskaźnik do biblioteki typów.|  
|[CCmdTarget::GetTypeLibCache](#gettypelibcache)|Pobiera pamięć podręczną biblioteki typów.|  
|[CCmdTarget::IsInvokeAllowed](#isinvokeallowed)|Umożliwia wywołanie metody automatyzacji.|  
|[CCmdTarget::IsResultExpected](#isresultexpected)|Zwraca wartość różną od zera, jeśli funkcja automatyzacji powinna zwrócić wartość.|  
|[CCmdTarget::OnCmdMsg](#oncmdmsg)|Trasy i wysyła komunikaty poleceń.|  
|[CCmdTarget::OnFinalRelease](#onfinalrelease)|Czyści po zwolnieniu ostatnie odwołanie OLE.|  
|[CCmdTarget::RestoreWaitCursor](#restorewaitcursor)|Przywraca klepsydry kursora.|  
  
## <a name="remarks"></a>Uwagi  
 Mapy komunikatów kieruje poleceń i komunikatów do funkcji Członkowskich, do zapisu do ich obsługi. (Polecenie jest komunikat z elementu menu, przycisk polecenia lub klawisza skrótu).  
  
 Framework klucza klasy pochodne `CCmdTarget` obejmują [CView](../../mfc/reference/cview-class.md), [CWinApp](../../mfc/reference/cwinapp-class.md), [CDocument](../../mfc/reference/cdocument-class.md), [CWnd](../../mfc/reference/cwnd-class.md), i [ CFrameWnd](../../mfc/reference/cframewnd-class.md). Jeśli jest planowane dla nowej klasy do obsługi komunikatów, klasy klasy pochodnej z jednego z tych `CCmdTarget`-klas pochodnych. Będą rzadko wyprowadzić klasę z `CCmdTarget` bezpośrednio.  
  
 Aby uzyskać przegląd obiekty docelowe poleceń i `OnCmdMsg` routingu, zobacz [obiekty docelowe poleceń](../../mfc/command-targets.md), [Routing poleceń](../../mfc/command-routing.md), i [mapowanie komunikatów](../../mfc/mapping-messages.md).  
  
 `CCmdTarget` obejmuje funkcje Członkowskie, które obsługują wyświetlanie klepsydry kursora. Wyświetl klepsydry kursora, gdy oczekujesz, że polecenie, aby wykonać przedział czasu zauważalne do wykonania.  
  
 Mapy, podobnie jak mapy komunikatów wysyłania, są używane do udostępnienia automatyzacji OLE `IDispatch` funkcji. Dzięki uwidocznieniu działania tego interfejsu, inne aplikacje (takie jak Visual Basic), można wywołać w aplikacji.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CCmdTarget`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="beginwaitcursor"></a>  CCmdTarget::BeginWaitCursor  
 Wywołaj tę funkcję, aby wyświetlić kursora jako Klepsydra, jeśli oczekujesz, że polecenie, aby wykonać przedział czasu zauważalne do wykonania.  
  
```  
void BeginWaitCursor();
```  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tę funkcję, aby pokazać mu, że jest zajęty, takie jak czas `CDocument` obiektu ładuje lub zapisuje się do pliku.  
  
 Akcje `BeginWaitCursor` nie zawsze są skuteczne poza obsługi komunikatów w jednym jako inne akcje, takie jak `OnSetCursor` obsługi, można zmienić kursora.  
  
 Wywołaj `EndWaitCursor` można przywrócić poprzednie kursora.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
##  <a name="ccmdtarget"></a>  CCmdTarget::CCmdTarget  
 Konstruuje `CCmdTarget` obiektu.  
  
```  
CCmdTarget();
```  
  
##  <a name="dooleverb"></a>  CCmdTarget::DoOleVerb  
 Powoduje, że określone przez zlecenia OLE do wykonania akcji.  
  
```  
BOOL DoOleVerb(
    LONG iVerb,  
    LPMSG lpMsg,  
    HWND hWndParent,  
    LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 *iVerb*  
 Identyfikator numeryczny zlecenia.  
  
 *lpMsg*  
 Wskaźnik do [MSG](http://msdn.microsoft.com/library/windows/desktop/ms644958) struktury opisujące zdarzenie (takie jak dwukrotne kliknięcie), która wywołała zlecenie.  
  
 *hWndParent*  
 Uchwyt okna dokumentu z obiektem.  
  
 *lprect —*  
 Wskaźnik do [Prostokąt](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury zawierającej współrzędne, w pikselach, które definiują obiekt użytkownika blokujących prostokąta w *hwndParent*.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli pomyślnie, w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska jest zasadniczo implementację [IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508). Możliwe działania są wyliczane przez [CCmdTarget::EnumOleVerbs](#enumoleverbs).  
  
##  <a name="enableautomation"></a>  CCmdTarget::EnableAutomation  
 Wywołaj tę funkcję, aby włączyć obiekt automatyzacji OLE.  
  
```  
void EnableAutomation();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest zazwyczaj wywoływana z konstruktora obiektu i powinna być wywoływana tylko, jeśli Mapa wysyłania została zadeklarowana w klasie. Aby uzyskać więcej informacji na temat automatyzacji, zobacz artykuły [klientów automatyzacji](../../mfc/automation-clients.md) i [serwerów automatyzacji](../../mfc/automation-servers.md).  
  
##  <a name="enableconnections"></a>  CCmdTarget::EnableConnections  
 Umożliwia inicjowanie zdarzeń za pośrednictwem punktów połączenia.  
  
```  
void EnableConnections();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby włączyć punkty połączenia, należy wywołać tej funkcji elementu członkowskiego w konstruktorze klasy pochodnej.  
  
##  <a name="enabletypelib"></a>  CCmdTarget::EnableTypeLib  
 Włącza bibliotekę typów obiektu.  
  
```  
void EnableTypeLib();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę funkcję składowej w Konstruktorze typu usługi `CCmdTarget`-pochodne obiektu, jeśli zawiera on informacje o typie. Aby uzyskać więcej informacji, zobacz artykuł bazy wiedzy Q185720, "Porada: Podaj informacje o typie z serwera automatyzacji MFC." Artykuły bazy wiedzy są dostępne pod adresem [ http://support.microsoft.com ](http://support.microsoft.com/).  
  
##  <a name="endwaitcursor"></a>  CCmdTarget::EndWaitCursor  
 Wywołaj tę funkcję, po wywołaniu `BeginWaitCursor` funkcja elementu członkowskiego do zwrócenia z klepsydry kursor do poprzedniego kursora.  
  
```  
void EndWaitCursor();
```  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje również tej funkcji elementu członkowskiego, po jest określana mianem klepsydry kursora.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
##  <a name="enumoleverbs"></a>  CCmdTarget::EnumOleVerbs  
 Wylicza czasowniki OLE obiektu.  
  
```  
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```  
  
### <a name="parameters"></a>Parametry  
 *ppenumOleVerb*  
 Wskaźnik do wskaźnika do [IEnumOLEVERB](http://msdn.microsoft.com/library/windows/desktop/ms695084) interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli obiekt obsługuje co najmniej jeden zlecenia OLE (w którym to przypadku \* *ppenumOleVerb* wskazuje `IEnumOLEVERB` interfejsu modułu wyliczającego), w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska jest zasadniczo implementację [IOleObject::EnumVerbs](http://msdn.microsoft.com/library/windows/desktop/ms692781).  
  
##  <a name="fromidispatch"></a>  CCmdTarget::FromIDispatch  
 Wywołaj tę funkcję, aby zamapować `IDispatch` wskaźnika, otrzymane od automatyzacji funkcji elementów członkowskich klasy do `CCmdTarget` obiekt, który implementuje interfejsy `IDispatch` obiektu.  
  
```  
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```  
  
### <a name="parameters"></a>Parametry  
 *lpDispatch*  
 Wskaźnik do `IDispatch` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CCmdTarget` obiekt skojarzony z *lpDispatch*. Ta funkcja zwraca wartość NULL, jeśli `IDispatch` obiekt nie został rozpoznany jako klasy Microsoft Foundation `IDispatch` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wynikiem tej funkcji jest przeciwieństwem wywołanie funkcji elementu członkowskiego `GetIDispatch`.  
  
##  <a name="getdispatchiid"></a>  CCmdTarget::GetDispatchIID  
 Pobiera identyfikator wysyłania podstawowego interfejsu.  
  
```  
virtual BOOL GetDispatchIID(IID* pIID);
```  
  
### <a name="parameters"></a>Parametry  
 *pIID*  
 Wskaźnik do Identyfikatora interfejsu ( [GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931)).  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli pomyślnie, w przeciwnym razie wartość FALSE. W przypadku powodzenia \* *pIID* jest ustawiona na identyfikator wysyłania podstawowego interfejsu.  
  
### <a name="remarks"></a>Uwagi  
 Klasy pochodne powinny przesłaniać tę funkcję elementu członkowskiego (Jeśli nie zostanie zastąpiona `GetDispatchIID` zwraca wartość FALSE). Zobacz [COleControl](../../mfc/reference/colecontrol-class.md).  
  
 Aby uzyskać więcej informacji, zobacz artykuł bazy wiedzy Q185720, "Porada: Podaj informacje o typie z serwera automatyzacji MFC." Artykuły bazy wiedzy są dostępne pod adresem [ http://support.microsoft.com ](http://support.microsoft.com/).  
  
##  <a name="getidispatch"></a>  CCmdTarget::GetIDispatch  
 Wywołanie tej funkcji elementu członkowskiego, aby pobrać `IDispatch` wskaźnika z metody automatyzacji dowolna zwraca `IDispatch` wskaźnika lub przyjmuje `IDispatch` wskaźnika przez odwołanie.  
  
```  
LPDISPATCH GetIDispatch(BOOL bAddRef);
```  
  
### <a name="parameters"></a>Parametry  
 *bAddRef*  
 Określa, czy należy zwiększyć licznik odwołań dla obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `IDispatch` Kursor skojarzony z obiektem.  
  
### <a name="remarks"></a>Uwagi  
 Dla obiektów to wywołanie `EnableAutomation` w ich konstruktory mogę nadawania automatyzacji włączona, ta funkcja zwraca wskaźnik do implementacji MFC `IDispatch` używanego przez klientów, którzy komunikują się za pośrednictwem `IDispatch` interfejsu. Wywołaniu tej funkcji, automatycznie dodaje odwołanie do wskaźnika, tak nie jest konieczne było wywołanie [IUnknown::AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379).  
  
##  <a name="gettypeinfocount"></a>  CCmdTarget::GetTypeInfoCount  
 Pobiera numer typu informacji interfejsy, które zawiera obiekt.  
  
```  
virtual UINT GetTypeInfoCount();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba typów informacji interfejsów.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego w zasadzie implementuje [IDispatch::GetTypeInfoCount](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfocount).  
  
 Klasy pochodne powinny przesłaniać tę funkcję, aby zwrócić liczbę typu informacji dostarczanych (0 lub 1). Jeśli nie zostanie zastąpiona `GetTypeInfoCount` zwraca wartość 0. Aby zastąpić, użyj [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) makra, która implementuje również `GetTypeLib` i `GetTypeLibCache`.  
  
##  <a name="gettypeinfoofguid"></a>  CCmdTarget::GetTypeInfoOfGuid  
 Pobiera opis typu, który odpowiada określony identyfikator GUID.  
  
```  
HRESULT GetTypeInfoOfGuid(
    LCID lcid,  
    const GUID& guid,  
    LPTYPEINFO* ppTypeInfo);
```  
  
### <a name="parameters"></a>Parametry  
 *lcid*  
 Identyfikator ustawień regionalnych ( `LCID`).  
  
 *Identyfikator GUID*  
 [GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931) opisu typu.  
  
 *ppTypeInfo*  
 Wskaźnik do wskaźnika do `ITypeInfo` interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość HRESULT powodzeniu lub niepowodzeniu wywołania. W przypadku powodzenia \* *ppTypeInfo* wskazuje na typ interfejsu informacji.  
  
##  <a name="gettypelib"></a>  CCmdTarget::GetTypeLib  
 Pobiera wskaźnik do biblioteki typów.  
  
```  
virtual HRESULT GetTypeLib(
    LCID lcid,  
    LPTYPELIB* ppTypeLib);
```  
  
### <a name="parameters"></a>Parametry  
 *lcid*  
 Identyfikator ustawień regionalnych (LCID).  
  
 *ppTypeLib*  
 Wskaźnik do wskaźnika do `ITypeLib` interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość HRESULT powodzeniu lub niepowodzeniu wywołania. W przypadku powodzenia \* *ppTypeLib* wskazuje interfejs biblioteki typów.  
  
### <a name="remarks"></a>Uwagi  
 Klasy pochodne powinny przesłaniać tę funkcję elementu członkowskiego (Jeśli nie zostanie zastąpiona `GetTypeLib` zwraca TYPE_E_CANTLOADLIBRARY). Użyj [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) makra, która implementuje również `GetTypeInfoCount` i `GetTypeLibCache`.  
  
##  <a name="gettypelibcache"></a>  CCmdTarget::GetTypeLibCache  
 Pobiera pamięć podręczną biblioteki typów.  
  
```  
virtual CTypeLibCache* GetTypeLibCache();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CTypeLibCache` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Klasy pochodne powinny przesłaniać tę funkcję elementu członkowskiego (Jeśli nie zostanie zastąpiona `GetTypeLibCache` zwraca wartość NULL). Użyj [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) makra, która implementuje również `GetTypeInfoCount` i `GetTypeLib`.  
  
##  <a name="isinvokeallowed"></a>  CCmdTarget::IsInvokeAllowed  
 Ta funkcja jest wywoływana przez implementację MFC `IDispatch::Invoke` do określenia, czy dany automation — metoda (identyfikowane przez *dispid*) może być wywołana.  
  
```  
virtual BOOL IsInvokeAllowed(DISPID dispid);
```  
  
### <a name="parameters"></a>Parametry  
 *identyfikator DISPID*  
 Identyfikator alokacji  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli metoda może być wywołana, w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `IsInvokeAllowed` zwraca wartość PRAWDA, `Invoke` przechodzi do wywołania metody; w przeciwnym razie `Invoke` zakończy się niepowodzeniem, zwracając wartość E_UNEXPECTED.  
  
 Klasy pochodne mogą zastąpić tę funkcję, aby zwrócić odpowiednie wartości (Jeśli nie zostanie zastąpiona `IsInvokeAllowed` zwraca wartość PRAWDA). Zobacz, w szczególności [COleControl::IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed).  
  
##  <a name="isresultexpected"></a>  CCmdTarget::IsResultExpected  
 Użyj `IsResultExpected` ustalić, czy klient oczekuje, że wartość zwracana z wywołania do funkcji automatyzacji.  
  
```  
BOOL IsResultExpected();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli funkcja automatyzacji powinna zwrócić wartość; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Interfejs OLE dostarcza informacji z MFC na temat tego, czy przy użyciu klienta lub ignorowanie wyniku wywołania funkcji i MFC z kolei używa tych informacji do ustalenia wyniku wywołania `IsResultExpected`. Wersji produkcyjnej, wartość zwracana jest czasu lub zasobów intensywnie, można zwiększyć wydajność przez wywołanie tej funkcji przed obliczenia wartości zwracanej.  
  
 Ta funkcja zwraca 0, tylko raz, dzięki czemu otrzymasz prawidłowe wartości zwracanej z innych funkcji automatyzacji połączeń je z funkcji automatyzacji, klienta została wywołana.  
  
 `IsResultExpected` Zwraca wartość różną od zera, jeśli jest wywoływana, gdy wywołanie funkcji automatyzacji nie jest w toku.  
  
##  <a name="oncmdmsg"></a>  CCmdTarget::OnCmdMsg  
 Wywoływane przez platformę, by kierować i wysyłać komunikaty poleceń, a także do obsługi aktualizacji poleceń, obiektów interfejsu użytkownika.  
  
```  
virtual BOOL OnCmdMsg(
    UINT nID,  
    int nCode,  
    void* pExtra,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>Parametry  
 *nID*  
 Zawiera identyfikator polecenia.  
  
 *nCode*  
 Określa kod powiadomień polecenia. Zobacz **uwagi** Aby uzyskać więcej informacji na temat wartości *nCode*.  
  
 *pExtra*  
 Używane zgodnie z wartością *nCode*. Zobacz **uwagi** Aby uzyskać więcej informacji na temat *pExtra*.  
  
 *pHandlerInfo*  
 Jeśli nie ma wartość NULL, `OnCmdMsg` wypełnia *pTarget* i *pmf* członkowie *pHandlerInfo* struktury zamiast wysyłania polecenia. Zazwyczaj ten parametr powinien mieć wartości NULL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli komunikat jest obsługiwany; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jest to procedura implementacji głównej architektury polecenia framework.  
  
 W czasie wykonywania `OnCmdMsg` wysyła polecenia do innych obiektów lub obsługuje samego polecenia, wywołując Klasa główna `CCmdTarget::OnCmdMsg`, który jest wyszukiwanie rzeczywiste mapy komunikatów. Aby uzyskać pełny opis poleceń domyślny routing, zobacz [wiadomościami i mapowanie tematów](../../mfc/message-handling-and-mapping.md).  
  
 W rzadkich przypadkach warto zastąpić tej funkcji elementu członkowskiego, aby rozszerzyć struktury standardowego routingu poleceń. Zapoznaj się [techniczne 21 Uwaga](../../mfc/tn021-command-and-message-routing.md) zaawansowane szczegółowe informacje o architekturze routing poleceń.  
  
 Jeśli zastąpisz `OnCmdMsg`, należy podać wartość odpowiednią dla *nCode*, kod powiadomień polecenia, a *pExtra*, która jest zależna od wartości *nCode* . W poniższej tabeli wymieniono odpowiadające im wartości:  
  
|*nCode* wartość|*pExtra* wartość|  
|-------------------|--------------------|  
|CN_COMMAND|[CCmdUI](../../mfc/reference/ccmdui-class.md)\*|  
|CN_EVENT|AFX_EVENT\*|  
|CN_UPDATE_COMMAND_UI|CCmdUI\*|  
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)\*|  
|CN_OLE_UNREGISTER|NULL|  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]  
  
##  <a name="onfinalrelease"></a>  CCmdTarget::OnFinalRelease  
 Wywoływane przez platformę po udostępnieniu ostatnie odwołanie OLE do z lub do obiektu.  
  
```  
virtual void OnFinalRelease();
```  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję, aby zapewnić specjalnej obsługi dla tej sytuacji. Domyślna implementacja usuwa obiekt.  
  
##  <a name="restorewaitcursor"></a>  CCmdTarget::RestoreWaitCursor  
 Wywołaj tę funkcję, aby przywrócić odpowiednie klepsydry kursor po zmianie kursora systemu (na przykład po okno komunikatu otworzył i zamknął następnie w trakcie wykonywania długotrwałej operacji).  
  
```  
void RestoreWaitCursor();
```  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Próbki MFC acdual —](../../visual-cpp-samples.md)   
 [Klasa CObject](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CCmdUI](../../mfc/reference/ccmdui-class.md)   
 [Klasa CDocument](../../mfc/reference/cdocument-class.md)   
 [Cdoctemplate — klasa](../../mfc/reference/cdoctemplate-class.md)   
 [Klasa CWinApp](../../mfc/reference/cwinapp-class.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Cview — klasa](../../mfc/reference/cview-class.md)   
 [Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)   
 [Klasa COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)
