---
title: CCmdTarget — klasa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 1dfc1c4d5cf753ae102d7656e94d63923004d2cc
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955664"
---
# <a name="ccmdtarget-class"></a>CCmdTarget — klasa
Klasa podstawowa architektura mapy komunikatów Microsoft Foundation Class Library.  
  
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
|[CCmdTarget::DoOleVerb](#dooleverb)|Powoduje, że określone zlecenie OLE do wykonania.|  
|[CCmdTarget::EnableAutomation](#enableautomation)|Umożliwia automatyzację OLE `CCmdTarget` obiektu.|  
|[CCmdTarget::EnableConnections](#enableconnections)|Umożliwia inicjowanie zdarzeń przez punkty połączenia.|  
|[CCmdTarget::EnableTypeLib](#enabletypelib)|Umożliwia biblioteki typów obiektów.|  
|[CCmdTarget::EndWaitCursor](#endwaitcursor)|Zwraca do poprzedniego kursora.|  
|[CCmdTarget::EnumOleVerbs](#enumoleverbs)|Wylicza obiektu OLE zleceń.|  
|[CCmdTarget::FromIDispatch](#fromidispatch)|Zwraca wskaźnik do `CCmdTarget` obiekt skojarzony z `IDispatch` wskaźnika.|  
|[CCmdTarget::GetDispatchIID](#getdispatchiid)|Pobiera identyfikator wysyłania podstawowy interfejs.|  
|[CCmdTarget::GetIDispatch](#getidispatch)|Zwraca wskaźnik do `IDispatch` obiekt skojarzony z `CCmdTarget` obiektu.|  
|[CCmdTarget::GetTypeInfoCount](#gettypeinfocount)|Pobiera liczbę typu informacji interfejsów, które zawiera obiekt.|  
|[CCmdTarget::GetTypeInfoOfGuid](#gettypeinfoofguid)|Pobiera opis typu, który odpowiada określonym identyfikatorem GUID.|  
|[CCmdTarget::GetTypeLib](#gettypelib)|Pobiera wskaźnik do biblioteki typów.|  
|[CCmdTarget::GetTypeLibCache](#gettypelibcache)|Pobiera typ pamięci podręcznej biblioteki.|  
|[CCmdTarget::IsInvokeAllowed](#isinvokeallowed)|Umożliwia wywołanie metody automatyzacji.|  
|[CCmdTarget::IsResultExpected](#isresultexpected)|Zwraca wartość niezerową, jeśli funkcja automatyzacji powinien zwracać wartość.|  
|[CCmdTarget::OnCmdMsg](#oncmdmsg)|Trasy i wysyła komunikaty poleceń.|  
|[CCmdTarget::OnFinalRelease](#onfinalrelease)|Czyści po zwolnieniu ostatnie odwołanie OLE.|  
|[CCmdTarget::RestoreWaitCursor](#restorewaitcursor)|Przywraca klepsydry kursora.|  
  
## <a name="remarks"></a>Uwagi  
 Mapy komunikatów kieruje poleceń lub komunikatów na funkcje elementu członkowskiego, zapisane w ich obsługę. (Polecenia jest wiadomość z pozycji menu, przycisk polecenia lub klawisz skrótu).  
  
 Framework klucza klasy wyprowadzone z `CCmdTarget` obejmują [CView](../../mfc/reference/cview-class.md), [CWinApp](../../mfc/reference/cwinapp-class.md), [CDocument](../../mfc/reference/cdocument-class.md), [CWnd](../../mfc/reference/cwnd-class.md), i [ Cframewnd —](../../mfc/reference/cframewnd-class.md). Jeśli planujesz dla nowej klasy do obsługi wiadomości, klasa wyprowadzona z jednego z tych `CCmdTarget`-klas pochodnych. Rzadko uzyskuje klasy z `CCmdTarget` bezpośrednio.  
  
 Omówienie obiekty docelowe poleceń i `OnCmdMsg` routingu, zobacz [obiekty docelowe poleceń](../../mfc/command-targets.md), [Routing poleceń](../../mfc/command-routing.md), i [mapowanie komunikatów](../../mfc/mapping-messages.md).  
  
 `CCmdTarget` obejmuje funkcje Członkowskie, które obsługują wyświetlanie klepsydry kursora. Wyświetl klepsydry kursora, gdy spodziewasz się polecenie podjęcie zauważalne czas do wykonania.  
  
 Mapy, podobnie jak mapy komunikatów wysyłania, są używane do udostępnienia automatyzacji OLE `IDispatch` funkcji. W przypadku wystawianego interfejsu, inne aplikacje (na przykład w języku Visual Basic) można wywołać w aplikacji.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CCmdTarget`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="beginwaitcursor"></a>  CCmdTarget::BeginWaitCursor  
 Wywołanie tej funkcji, aby wyświetlić kursora jako Klepsydra w oczekiwanym polecenia podjęcie zauważalne czas do wykonania.  
  
```  
void BeginWaitCursor();
```  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tę funkcję, aby pokazać użytkownika jest zajęty, takie jak kiedy `CDocument` obiektu ładuje lub sam jest zapisywany do pliku.  
  
 Akcje `BeginWaitCursor` nie zawsze są skuteczne poza obsługi wiadomości jako inne akcje, takie jak `OnSetCursor` obsługi, można zmienić kursora.  
  
 Wywołanie `EndWaitCursor` do przywrócenia poprzedniej kursora.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
##  <a name="ccmdtarget"></a>  CCmdTarget::CCmdTarget  
 Konstruuje `CCmdTarget` obiektu.  
  
```  
CCmdTarget();
```  
  
##  <a name="dooleverb"></a>  CCmdTarget::DoOleVerb  
 Powoduje, że określone zlecenie OLE do wykonania.  
  
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
 Wskaźnik do [MSG](http://msdn.microsoft.com/library/windows/desktop/ms644958) opisujące zdarzeń (na przykład kliknij dwukrotnie), który wywołał zlecenie struktury.  
  
 *hWndParent*  
 Uchwyt okna dokumentu z obiektem.  
  
 *lprect —*  
 Wskaźnik do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury zawierającej współrzędne, w pikselach, które definiują obiektu do ograniczenia prostokąt w *hwndParent*.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli pomyślne, w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska jest zasadniczo implementacja [IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508). Możliwe działania są wyliczane przez [CCmdTarget::EnumOleVerbs](#enumoleverbs).  
  
##  <a name="enableautomation"></a>  CCmdTarget::EnableAutomation  
 Wywołanie tej funkcji w celu dla obiekt automatyzacji OLE.  
  
```  
void EnableAutomation();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest zazwyczaj wywoływana z konstruktora obiektu i powinna być wywoływana tylko przez mapy wysyłania została zadeklarowana w klasie. Aby uzyskać więcej informacji na temat automatyzacji zobacz artykuły [klientów automatyzacji](../../mfc/automation-clients.md) i [serwery automatyzacji](../../mfc/automation-servers.md).  
  
##  <a name="enableconnections"></a>  CCmdTarget::EnableConnections  
 Umożliwia inicjowanie zdarzeń przez punkty połączenia.  
  
```  
void EnableConnections();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby włączyć punkty połączenia, wywołanie tej funkcji Członkowskich w konstruktorze klasy pochodnej.  
  
##  <a name="enabletypelib"></a>  CCmdTarget::EnableTypeLib  
 Umożliwia biblioteki typów obiektów.  
  
```  
void EnableTypeLib();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji Członkowskich w Konstruktorze Twojej `CCmdTarget`-pochodnych obiektu, jeśli zawiera on informacji o typie. Aby uzyskać więcej informacji, zobacz artykuł bazy wiedzy Knowledge Base Q185720, "Porada: Podaj informacje o typie z serwera automatyzacji MFC." Artykuły bazy wiedzy są dostępne pod adresem [ http://support.microsoft.com ](http://support.microsoft.com/).  
  
##  <a name="endwaitcursor"></a>  CCmdTarget::EndWaitCursor  
 Wywołanie tej funkcji po wywołaniu `BeginWaitCursor` funkcji członkowskiej do zwrócenia z klepsydry kursor do poprzedniego kursora.  
  
```  
void EndWaitCursor();
```  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje również funkcji członkowskiej po została wywołana klepsydry kursora.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
##  <a name="enumoleverbs"></a>  CCmdTarget::EnumOleVerbs  
 Wylicza obiektu OLE zleceń.  
  
```  
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```  
  
### <a name="parameters"></a>Parametry  
 *ppenumOleVerb*  
 Wskaźnik na wskaźnik do [IEnumOLEVERB](http://msdn.microsoft.com/library/windows/desktop/ms695084) interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli obiekt obsługuje co najmniej jedno zlecenie OLE (w takim przypadku \* *ppenumOleVerb* wskazuje `IEnumOLEVERB` interfejsu modułu wyliczającego), w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska jest zasadniczo implementacja [IOleObject::EnumVerbs](http://msdn.microsoft.com/library/windows/desktop/ms692781).  
  
##  <a name="fromidispatch"></a>  CCmdTarget::FromIDispatch  
 Wywołanie tej funkcji do mapowania `IDispatch` wskaźnika otrzymanych od automatyzacji funkcji elementów członkowskich klasy, do `CCmdTarget` obiekt, który implementuje interfejsy `IDispatch` obiektu.  
  
```  
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```  
  
### <a name="parameters"></a>Parametry  
 *lpDispatch*  
 Wskaźnik do `IDispatch` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CCmdTarget` obiekt skojarzony z *lpDispatch*. Ta funkcja zwraca **NULL** Jeśli `IDispatch` obiektu nie został rozpoznany jako klasa Microsoft Foundation `IDispatch` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wynikiem tej funkcji jest odwrotność wywołanie funkcji Członkowskich `GetIDispatch`.  
  
##  <a name="getdispatchiid"></a>  CCmdTarget::GetDispatchIID  
 Pobiera identyfikator wysyłania podstawowy interfejs.  
  
```  
virtual BOOL GetDispatchIID(IID* pIID);
```  
  
### <a name="parameters"></a>Parametry  
 *pIID*  
 Wskaźnik do Identyfikatora interfejsu ( [GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931)).  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli pomyślne, w przeciwnym razie wartość FALSE. W przypadku powodzenia \* *pIID* ma ustawioną wartość identyfikatora wysyłania podstawowy interfejs.  
  
### <a name="remarks"></a>Uwagi  
 Klasy pochodne powinny przesłaniać funkcji członkowskiej (Jeśli nie została zastąpiona, `GetDispatchIID` zwraca wartość FALSE). Zobacz [colecontrol —](../../mfc/reference/colecontrol-class.md).  
  
 Aby uzyskać więcej informacji, zobacz artykuł bazy wiedzy Knowledge Base Q185720, "Porada: Podaj informacje o typie z serwera automatyzacji MFC." Artykuły bazy wiedzy są dostępne pod adresem [ http://support.microsoft.com ](http://support.microsoft.com/).  
  
##  <a name="getidispatch"></a>  CCmdTarget::GetIDispatch  
 Wywołanie tej funkcji Członkowskich pobrać `IDispatch` wskaźnika z metody automatyzacji dowolna zwraca `IDispatch` wskaźnika lub ma `IDispatch` wskaźnika przez odwołanie.  
  
```  
LPDISPATCH GetIDispatch(BOOL bAddRef);
```  
  
### <a name="parameters"></a>Parametry  
 *bAddRef*  
 Określa, czy należy zwiększyć wartość odwołania do obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `IDispatch` Kursor skojarzony z obiektem.  
  
### <a name="remarks"></a>Uwagi  
 Dla obiektów tego wywołania `EnableAutomation` w swoich konstruktorach nadawania automatyzacji włączone, ta funkcja zwraca wskaźnik do implementacji MFC `IDispatch` używany przez klientów, którzy komunikują się za pośrednictwem `IDispatch` interfejsu. Wywołanie tej funkcji, automatycznie dodaje odwołanie do wskaźnika, tak nie jest konieczne do wywoływania [IUnknown::AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379).  
  
##  <a name="gettypeinfocount"></a>  CCmdTarget::GetTypeInfoCount  
 Pobiera liczbę typu informacji interfejsów, które zawiera obiekt.  
  
```  
virtual UINT GetTypeInfoCount();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba interfejsów informacji typu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska zasadniczo implementuje [IDispatch::GetTypeInfoCount](http://msdn.microsoft.com/en-us/da876d53-cb8a-465c-a43e-c0eb272e2a12).  
  
 Klasy pochodne powinny przesłaniać tę funkcję, aby zwrócić liczby typu informacji interfejsami (0 lub 1). Jeśli nie została zastąpiona, `GetTypeInfoCount` zwraca wartość 0. Aby zastąpić, użyj [implement_oletypelib —](../../mfc/reference/type-library-access.md#implement_oletypelib) makra, która implementuje również `GetTypeLib` i `GetTypeLibCache`.  
  
##  <a name="gettypeinfoofguid"></a>  CCmdTarget::GetTypeInfoOfGuid  
 Pobiera opis typu, który odpowiada określonym identyfikatorem GUID.  
  
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
 Wskaźnik na wskaźnik do `ITypeInfo` interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 HRESULT oznaczający powodzenie lub Niepowodzenie wywołania. W przypadku powodzenia * *ppTypeInfo* wskazuje typ interfejsu informacji.  
  
##  <a name="gettypelib"></a>  CCmdTarget::GetTypeLib  
 Pobiera wskaźnik do biblioteki typów.  
  
```  
virtual HRESULT GetTypeLib(
    LCID lcid,  
    LPTYPELIB* ppTypeLib);
```  
  
### <a name="parameters"></a>Parametry  
 *lcid*  
 Identyfikator ustawień regionalnych ( `LCID`).  
  
 *ppTypeLib*  
 Wskaźnik na wskaźnik do `ITypeLib` interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 HRESULT oznaczający powodzenie lub Niepowodzenie wywołania. W przypadku powodzenia * *ppTypeLib* wskazuje typ interfejsu biblioteki.  
  
### <a name="remarks"></a>Uwagi  
 Klasy pochodne powinny przesłaniać funkcji członkowskiej (Jeśli nie została zastąpiona, `GetTypeLib` zwraca TYPE_E_CANTLOADLIBRARY). Użyj [implement_oletypelib —](../../mfc/reference/type-library-access.md#implement_oletypelib) makra, która implementuje również `GetTypeInfoCount` i `GetTypeLibCache`.  
  
##  <a name="gettypelibcache"></a>  CCmdTarget::GetTypeLibCache  
 Pobiera typ pamięci podręcznej biblioteki.  
  
```  
virtual CTypeLibCache* GetTypeLibCache();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CTypeLibCache` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Klasy pochodne powinny przesłaniać funkcji członkowskiej (Jeśli nie została zastąpiona, `GetTypeLibCache` zwraca wartość NULL). Użyj [implement_oletypelib —](../../mfc/reference/type-library-access.md#implement_oletypelib) makra, która implementuje również `GetTypeInfoCount` i `GetTypeLib`.  
  
##  <a name="isinvokeallowed"></a>  CCmdTarget::IsInvokeAllowed  
 Ta funkcja jest wywoływana przez implementacji MFC `IDispatch::Invoke` można określić, czy metoda danego automatyzacji (identyfikowane przez *dispid*) może być wywołany.  
  
```  
virtual BOOL IsInvokeAllowed(DISPID dispid);
```  
  
### <a name="parameters"></a>Parametry  
 *identyfikator DISPID*  
 Identyfikator wysyłania  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli metoda może być wywołana, w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `IsInvokeAllowed` zwraca wartość PRAWDA, `Invoke` będzie kontynuowana, aby wywołać metodę; w przeciwnym razie `Invoke` zakończy się niepowodzeniem, zwracając E_UNEXPECTED.  
  
 Klasy pochodne mogą zastąpić tę funkcję, aby zwrócić wartości odpowiednich (Jeśli nie została zastąpiona, `IsInvokeAllowed` zwraca wartość TRUE). W szczególności zobacz [COleControl::IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed).  
  
##  <a name="isresultexpected"></a>  CCmdTarget::IsResultExpected  
 Użyj `IsResultExpected` ustalić, czy klient oczekuje wartości zwracanych z jego wywołanie funkcji automatyzacji.  
  
```  
BOOL IsResultExpected();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja automatyzacji powinna zwrócić wartość; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Interfejs OLE dostarcza informacje z MFC Określa, czy klient jest przy użyciu lub ignorowanie wynikiem wywołania funkcji i MFC z kolei używa tych informacji do ustalenia wyniku wywołania `IsResultExpected`. Jeśli produkcja zwracanej wartości czasu - lub obciążający zasoby, można zwiększyć wydajność przez wywołanie tej funkcji przed obliczania wartości zwracanej.  
  
 Ta funkcja zwraca wartość 0, tylko raz, aby otrzymasz prawidłowe wartości zwracanych z innych funkcji automatyzacji połączeń je z funkcji automatyzacji który klient została wywołana.  
  
 `IsResultExpected` Zwraca wartość niezerową, jeśli wywołany po wywołaniu funkcji automatyzacji nie jest w toku.  
  
##  <a name="oncmdmsg"></a>  CCmdTarget::OnCmdMsg  
 Wywoływane przez platformę, by kierować i wysyłać komunikaty poleceń i do obsługi aktualizacji obiekty interfejsu użytkownika poleceń.  
  
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
 Określa polecenie kod powiadomienia. Zobacz **uwagi** uzyskać więcej informacji o wartości *nCode*.  
  
 *pExtra*  
 Używane zgodnie z wartością *nCode*. Zobacz **uwagi** uzyskać więcej informacji o *pExtra*.  
  
 *pHandlerInfo*  
 Jeśli nie **NULL**, `OnCmdMsg` wypełnia *pTarget* i *pmf* członkami *pHandlerInfo* struktury zamiast wysyłania polecenie. Zazwyczaj ten parametr powinien być **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli komunikat jest obsługiwany; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jest to procedura implementacji głównego architektury polecenia framework.  
  
 W czasie wykonywania `OnCmdMsg` wywołuje polecenia do innych obiektów lub obsługuje samo polecenie przez wywołanie metody klasy głównym `CCmdTarget::OnCmdMsg`, która jest wyszukiwania rzeczywiste mapy komunikatów. Pełny opis routingu domyślnego polecenia, zobacz [obsługi wiadomości i mapowania tematy](../../mfc/message-handling-and-mapping.md).  
  
 W rzadkich przypadkach można przesłonić tę funkcję elementu członkowskiego, aby rozszerzyć w ramach standardowego routingu poleceń. Zapoznaj się [techniczne notatkę 21](../../mfc/tn021-command-and-message-routing.md) zaawansowane szczegółowe informacje o architekturze routing poleceń.  
  
 Jeśli można zastąpić `OnCmdMsg`, należy podać wartość odpowiednią dla *nCode*, polecenie kod powiadomienia, i *pExtra*, która jest zależna od wartości *nCode* . W poniższej tabeli wymieniono odpowiednimi wartościami:  
  
|*nCode* wartości|*pExtra* wartości|  
|-------------------|--------------------|  
|CN_COMMAND|[Ccmdui —](../../mfc/reference/ccmdui-class.md)*|  
|CN_EVENT|AFX_EVENT *|  
|CN_UPDATE_COMMAND_UI|Ccmdui — *|  
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)*|  
|CN_OLE_UNREGISTER|NULL|  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]  
  
##  <a name="onfinalrelease"></a>  CCmdTarget::OnFinalRelease  
 Wywoływane przez platformę po zwolnieniu ostatnie odwołanie OLE do lub z obiektu.  
  
```  
virtual void OnFinalRelease();
```  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę funkcję, aby zapewnić specjalnej obsługi w takiej sytuacji. Domyślna implementacja usuwa obiekt.  
  
##  <a name="restorewaitcursor"></a>  CCmdTarget::RestoreWaitCursor  
 Wywołanie tej funkcji, aby przywrócić odpowiednie klepsydry kursor po zmianie kursora systemu (na przykład po okno komunikatu ma otwarte, a następnie zamknięte, podczas gdy w trakcie długotrwałej operacji).  
  
```  
void RestoreWaitCursor();
```  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC acdual —](../../visual-cpp-samples.md)   
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Ccmdui — klasa](../../mfc/reference/ccmdui-class.md)   
 [Cdocument — klasa](../../mfc/reference/cdocument-class.md)   
 [Cdoctemplate — klasa](../../mfc/reference/cdoctemplate-class.md)   
 [Cwinapp — klasa](../../mfc/reference/cwinapp-class.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Cview — klasa](../../mfc/reference/cview-class.md)   
 [Cframewnd — klasa](../../mfc/reference/cframewnd-class.md)   
 [Klasa COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)
