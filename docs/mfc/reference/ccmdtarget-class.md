---
title: Klasa CCmdTarget
ms.date: 11/04/2016
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
ms.openlocfilehash: 583b685295bf77910ef134776c1c4fa39baf93ad
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816339"
---
# <a name="ccmdtarget-class"></a>Klasa CCmdTarget

Klasa bazowa dla architektury mapy komunikatów biblioteka MFC.

## <a name="syntax"></a>Składnia

```
class CCmdTarget : public CObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CCmdTarget:: CCmdTarget](#ccmdtarget)|Konstruuje obiekt `CCmdTarget`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CCmdTarget:: BeginWaitCursor](#beginwaitcursor)|Wyświetla kursor jako klepsydrę kursora.|
|[CCmdTarget::D oOleVerb](#dooleverb)|Powoduje wykonanie akcji określonej przez zlecenie OLE.|
|[CCmdTarget:: EnableAutomation](#enableautomation)|Umożliwia automatyzację OLE dla obiektu `CCmdTarget`.|
|[CCmdTarget:: EnableConnections](#enableconnections)|Włącza Wyzwalanie zdarzeń przez punkty połączenia.|
|[CCmdTarget::EnableTypeLib](#enabletypelib)|Włącza bibliotekę typów obiektu.|
|[CCmdTarget:: EndWaitCursor](#endwaitcursor)|Powraca do poprzedniego kursora.|
|[CCmdTarget:: EnumOleVerbs](#enumoleverbs)|Wylicza zlecenia OLE obiektu.|
|[CCmdTarget:: FromIDispatch](#fromidispatch)|Zwraca wskaźnik do obiektu `CCmdTarget` skojarzonego ze wskaźnikiem `IDispatch`.|
|[CCmdTarget:: GetDispatchIID](#getdispatchiid)|Pobiera identyfikator podstawowego interfejsu wysyłania.|
|[CCmdTarget:: GetIDispatch](#getidispatch)|Zwraca wskaźnik do obiektu `IDispatch` skojarzonego z obiektem `CCmdTarget`.|
|[CCmdTarget:: GetTypeInfoCount](#gettypeinfocount)|Pobiera liczbę interfejsów informacji o typie, które zapewnia obiekt.|
|[CCmdTarget:: GetTypeInfoOfGuid](#gettypeinfoofguid)|Pobiera opis typu, który odpowiada określonemu identyfikatorowi GUID.|
|[CCmdTarget:: GetTypeLib](#gettypelib)|Pobiera wskaźnik do biblioteki typów.|
|[CCmdTarget::GetTypeLibCache](#gettypelibcache)|Pobiera pamięć podręczną biblioteki typów.|
|[CCmdTarget:: IsInvokeAllowed](#isinvokeallowed)|Włącza wywołanie metody automatyzacji.|
|[CCmdTarget:: IsResultExpected](#isresultexpected)|Zwraca wartość różną od zera, jeśli funkcja automatyzacji powinna zwracać wartości.|
|[CCmdTarget:: OnCmdMsg](#oncmdmsg)|Kieruje i wysyła komunikaty poleceń.|
|[CCmdTarget:: OnFinalRelease](#onfinalrelease)|Czyści po zwolnieniu ostatniego odwołania OLE.|
|[CCmdTarget:: RestoreWaitCursor](#restorewaitcursor)|Przywraca klepsydrę kursora.|

## <a name="remarks"></a>Uwagi

Mapa komunikatów kieruje polecenia lub komunikaty do funkcji składowych, które można napisać, aby je obsłużyć. (Polecenie to komunikat z elementu menu, przycisku polecenia lub klawisza skrótu).

Klasy najważniejszych klas, które pochodzą z `CCmdTarget` obejmują [CView](../../mfc/reference/cview-class.md), [CWinApp](../../mfc/reference/cwinapp-class.md), [CDocument](../../mfc/reference/cdocument-class.md), [CWnd](../../mfc/reference/cwnd-class.md)i [obiektu CFrameWnd](../../mfc/reference/cframewnd-class.md). Jeśli zamierzasz, aby nowa klasa obsługiwała komunikaty, należy utworzyć klasę z jednej z tych klas pochodnych `CCmdTarget`. Klasa jest rzadko wyprowadzana bezpośrednio z `CCmdTarget`.

Aby zapoznać się z omówieniem obiektów docelowych poleceń i routingu `OnCmdMsg`, zobacz temat [cele poleceń](../../mfc/command-targets.md), [routing poleceń](../../mfc/command-routing.md)i [komunikaty dotyczące mapowania](../../mfc/mapping-messages.md).

`CCmdTarget` obejmuje funkcje członkowskie, które obsługują wyświetlanie wskaźnika klepsydry. Wyświetl kursor klepsydry, gdy oczekuje się, że polecenie przekroczy przedział czasu do wykonania.

Mapy wysyłania, podobnie jak mapy komunikatów, są używane do udostępniania funkcji automatyzacji OLE `IDispatch`. Przez udostępnienie tego interfejsu inne aplikacje (takie jak Visual Basic) mogą wywołać aplikację.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CCmdTarget`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

##  <a name="beginwaitcursor"></a>CCmdTarget:: BeginWaitCursor

Wywołaj tę funkcję, aby wyświetlić kursor jako klepsydrę, gdy oczekuje się, że polecenie przekroczy przedział czasu do wykonania.

```
void BeginWaitCursor();
```

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę funkcję, aby pokazać, że jest zajęta, na przykład gdy obiekt `CDocument` załaduje lub zapisywany w pliku.

Akcje `BeginWaitCursor` nie zawsze są skuteczne poza pojedynczym programem obsługi komunikatów jako innymi akcjami, takimi jak obsługa `OnSetCursor`, może zmienić kursor.

Wywołaj `EndWaitCursor`, aby przywrócić poprzedni kursor.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

##  <a name="ccmdtarget"></a>CCmdTarget:: CCmdTarget

Konstruuje obiekt `CCmdTarget`.

```
CCmdTarget();
```

##  <a name="dooleverb"></a>CCmdTarget::D oOleVerb

Powoduje wykonanie akcji określonej przez zlecenie OLE.

```
BOOL DoOleVerb(
    LONG iVerb,
    LPMSG lpMsg,
    HWND hWndParent,
    LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Liczbowy identyfikator zlecenia.

*lpMsg*<br/>
Wskaźnik na strukturę [MSG](/windows/win32/api/winuser/ns-winuser-msg) opisującą zdarzenie (takie jak dwukrotne kliknięcie), które wywołało zlecenie.

*hWndParent*<br/>
Uchwyt okna dokumentu zawierającego obiekt.

*lpRect*<br/>
Wskaźnik do struktury [Rect](/previous-versions/dd162897\(v=vs.85\)) zawierający współrzędne, w pikselach, które definiują prostokąt ograniczający obiekt w *hwndParent*.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli powodzenie, w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest zasadniczo implementacją [IOleObject::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb). Możliwe akcje są wyliczane przez [CCmdTarget:: EnumOleVerbs](#enumoleverbs).

##  <a name="enableautomation"></a>CCmdTarget:: EnableAutomation

Wywołaj tę funkcję, aby włączyć automatyzację OLE dla obiektu.

```
void EnableAutomation();
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest zazwyczaj wywoływana z konstruktora obiektu i powinna być wywoływana tylko wtedy, gdy została zadeklarowana Mapa wysyłania dla klasy. Aby uzyskać więcej informacji na temat automatyzacji, zobacz artykuły [klienci automatyzacji](../../mfc/automation-clients.md) i [serwery automatyzacji](../../mfc/automation-servers.md).

##  <a name="enableconnections"></a>CCmdTarget:: EnableConnections

Włącza Wyzwalanie zdarzeń przez punkty połączenia.

```
void EnableConnections();
```

### <a name="remarks"></a>Uwagi

Aby włączyć punkty połączenia, Wywołaj tę funkcję elementu członkowskiego w konstruktorze klasy pochodnej.

##  <a name="enabletypelib"></a>CCmdTarget:: EnableTypeLib

Włącza bibliotekę typów obiektu.

```
void EnableTypeLib();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego w konstruktorze obiektu pochodnego `CCmdTarget`, jeśli zawiera on informacje o typie.

##  <a name="endwaitcursor"></a>CCmdTarget:: EndWaitCursor

Wywołaj tę funkcję po wywołaniu funkcji składowej `BeginWaitCursor`, aby wrócić z kursora klepsydry do poprzedniego kursora.

```
void EndWaitCursor();
```

### <a name="remarks"></a>Uwagi

Struktura wywołuje również tę funkcję elementu członkowskiego po wywołaniu klepsydry kursora.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

##  <a name="enumoleverbs"></a>CCmdTarget:: EnumOleVerbs

Wylicza zlecenia OLE obiektu.

```
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```

### <a name="parameters"></a>Parametry

*ppenumOleVerb*<br/>
Wskaźnik do wskaźnika do interfejsu [IEnumOLEVERB](/windows/win32/api/oleidl/nn-oleidl-ienumoleverb) .

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli obiekt obsługuje co najmniej jedno zlecenie OLE (w tym przypadku \* *ppenumOleVerb* wskazuje na interfejs modułu wyliczającego `IEnumOLEVERB`), w przeciwnym razie false.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest zasadniczo implementacją [IOleObject:: EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs).

##  <a name="fromidispatch"></a>CCmdTarget:: FromIDispatch

Wywołaj tę funkcję, aby zmapować wskaźnik `IDispatch` otrzymany z funkcji elementów członkowskich automatyzacji klasy do obiektu `CCmdTarget`, który implementuje interfejsy obiektu `IDispatch`.

```
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```

### <a name="parameters"></a>Parametry

*lpDispatch*<br/>
Wskaźnik do obiektu `IDispatch`.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu `CCmdTarget` skojarzonego z *LPDISPATCH*. Ta funkcja zwraca wartość NULL, jeśli obiekt `IDispatch` nie jest rozpoznawany jako obiekt `IDispatch` Microsoft Foundation Class.

### <a name="remarks"></a>Uwagi

Wynikiem tej funkcji jest odwrotność wywołania funkcji składowej `GetIDispatch`.

##  <a name="getdispatchiid"></a>CCmdTarget:: GetDispatchIID

Pobiera identyfikator podstawowego interfejsu wysyłania.

```
virtual BOOL GetDispatchIID(IID* pIID);
```

### <a name="parameters"></a>Parametry

*pIID*<br/>
Wskaźnik do identyfikatora interfejsu ( [GUID](/previous-versions/cc317743(v%3dmsdn.10)).

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli powodzenie, w przeciwnym razie FALSE. Jeśli to się powiedzie, \* *piid* jest ustawiony na podstawowy identyfikator interfejsu wysyłania.

### <a name="remarks"></a>Uwagi

Klasy pochodne powinny przesłaniać tę funkcję elementu członkowskiego (jeśli nie zostanie ona zastąpiona, `GetDispatchIID` zwraca wartość FALSE). Zobacz [COleControl](../../mfc/reference/colecontrol-class.md).

##  <a name="getidispatch"></a>CCmdTarget:: GetIDispatch

Wywołaj tę funkcję elementu członkowskiego, aby pobrać wskaźnik `IDispatch` z metody automatyzacji, która zwraca wskaźnik `IDispatch` lub pobiera `IDispatch` wskaźnik przez odwołanie.

```
LPDISPATCH GetIDispatch(BOOL bAddRef);
```

### <a name="parameters"></a>Parametry

*bAddRef*<br/>
Określa, czy zwiększyć liczbę odwołań dla obiektu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik `IDispatch` skojarzony z obiektem.

### <a name="remarks"></a>Uwagi

W przypadku obiektów, które wywołują `EnableAutomation` w ich konstruktorach, dzięki czemu Automatyzacja jest włączona, ta funkcja zwraca wskaźnik do implementacji klasy Foundation `IDispatch`, który jest używany przez klientów komunikujących się za pośrednictwem interfejsu `IDispatch`. Wywołanie tej funkcji automatycznie dodaje odwołanie do wskaźnika, więc nie trzeba wykonywać wywołania [IUnknown:: AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref).

##  <a name="gettypeinfocount"></a>CCmdTarget:: GetTypeInfoCount

Pobiera liczbę interfejsów informacji o typie, które zapewnia obiekt.

```
virtual UINT GetTypeInfoCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba interfejsów informacji o typie.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska zasadniczo implementuje element [IDispatch:: GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount).

Klasy pochodne powinny zastąpić tę funkcję, aby zwrócić liczbę dostarczonych interfejsów informacji o typie (0 lub 1). Jeśli nie zostanie zastąpiony, `GetTypeInfoCount` zwraca wartość 0. Aby przesłonić, użyj makra [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) , które implementuje także `GetTypeLib` i `GetTypeLibCache`.

##  <a name="gettypeinfoofguid"></a>CCmdTarget:: GetTypeInfoOfGuid

Pobiera opis typu, który odpowiada określonemu identyfikatorowi GUID.

```
HRESULT GetTypeInfoOfGuid(
    LCID lcid,
    const GUID& guid,
    LPTYPEINFO* ppTypeInfo);
```

### <a name="parameters"></a>Parametry

*lcid*<br/>
Identyfikator ustawień regionalnych (`LCID`).

*guid*<br/>
[Identyfikator GUID](/previous-versions/cc317743(v%3dmsdn.10)) opisu typu.

*ppTypeInfo*<br/>
Wskaźnik do wskaźnika do interfejsu `ITypeInfo`.

### <a name="return-value"></a>Wartość zwracana

WYNIK HRESULT wskazujący powodzenie lub Niepowodzenie wywołania. Jeśli się powiedzie, \* *ppTypeInfo* punkty do interfejsu informacji o typie.

##  <a name="gettypelib"></a>CCmdTarget:: GetTypeLib

Pobiera wskaźnik do biblioteki typów.

```
virtual HRESULT GetTypeLib(
    LCID lcid,
    LPTYPELIB* ppTypeLib);
```

### <a name="parameters"></a>Parametry

*lcid*<br/>
Identyfikator ustawień regionalnych (LCID).

*ppTypeLib*<br/>
Wskaźnik do wskaźnika do interfejsu `ITypeLib`.

### <a name="return-value"></a>Wartość zwracana

WYNIK HRESULT wskazujący powodzenie lub Niepowodzenie wywołania. Jeśli się powiedzie, \* *ppTypeLib* wskazuje interfejs biblioteki typów.

### <a name="remarks"></a>Uwagi

Klasy pochodne powinny przesłaniać tę funkcję elementu członkowskiego (jeśli nie zostanie ona zastąpiona, `GetTypeLib` zwraca TYPE_E_CANTLOADLIBRARY). Użyj makra [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) , które implementuje także `GetTypeInfoCount` i `GetTypeLibCache`.

##  <a name="gettypelibcache"></a>CCmdTarget:: GetTypeLibCache

Pobiera pamięć podręczną biblioteki typów.

```
virtual CTypeLibCache* GetTypeLibCache();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu `CTypeLibCache`.

### <a name="remarks"></a>Uwagi

Klasy pochodne powinny przesłaniać tę funkcję elementu członkowskiego (jeśli nie zostanie ona zastąpiona, `GetTypeLibCache` zwraca wartość NULL). Użyj makra [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) , które implementuje także `GetTypeInfoCount` i `GetTypeLib`.

##  <a name="isinvokeallowed"></a>CCmdTarget:: IsInvokeAllowed

Ta funkcja jest wywoływana przez implementację `IDispatch::Invoke` MFC, aby określić, czy dana metoda automatyzacji (identyfikowana przez identyfikator *DISPID*) może zostać wywołana.

```
virtual BOOL IsInvokeAllowed(DISPID dispid);
```

### <a name="parameters"></a>Parametry

*DISPID*<br/>
Identyfikator wysyłania.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli metoda może być wywoływana, w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli `IsInvokeAllowed` zwraca wartość TRUE, `Invoke` przechodzi do wywołania metody; w przeciwnym razie `Invoke` zakończy się niepowodzeniem, zwracając E_UNEXPECTED.

Klasy pochodne mogą przesłaniać tę funkcję, aby zwracały odpowiednie wartości (jeśli nie zostały zastąpione, `IsInvokeAllowed` zwraca wartość TRUE). Zobacz w szczególności [COleControl:: IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed).

##  <a name="isresultexpected"></a>CCmdTarget:: IsResultExpected

Użyj `IsResultExpected`, aby upewnić się, czy klient oczekuje wartości zwracanej od wywołania funkcji automatyzacji.

```
BOOL IsResultExpected();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja automatyzacji powinna zwrócić wartość; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Interfejs OLE dostarcza informacje do MFC dotyczące tego, czy klient używa lub ignoruje wynik wywołania funkcji, a MFC z kolei używa tych informacji do określenia wyniku wywołania `IsResultExpected`. Jeśli produkcja zwracanych wartości jest czasochłonna lub intensywnie wykorzystujących zasoby, można zwiększyć wydajność, wywołując tę funkcję przed obliczaniem wartości zwracanej.

Ta funkcja zwraca 0 tylko raz, aby otrzymać prawidłowe wartości zwracane z innych funkcji automatyzacji, jeśli są one wywoływane z funkcji automatyzacji, która została wywołana przez klienta.

`IsResultExpected` zwraca wartość różną od zera, jeśli wywoływana, gdy wywołanie funkcji automatyzacji nie jest w toku.

##  <a name="oncmdmsg"></a>CCmdTarget:: OnCmdMsg

Wywoływane przez platformę do rozsyłania i wysyłania komunikatów poleceń oraz do obsługi aktualizacji obiektów interfejsu użytkownika.

```
virtual BOOL OnCmdMsg(
    UINT nID,
    int nCode,
    void* pExtra,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Zawiera identyfikator polecenia.

*nCode*<br/>
Identyfikuje kod powiadomienia polecenia. Zobacz **uwagi** , aby uzyskać więcej informacji na temat wartości dla *nCode*.

*pExtra*<br/>
Używane zgodnie z wartością *nCode*. Aby uzyskać więcej informacji na temat *pExtra*, zobacz **uwagi** .

*pHandlerInfo*<br/>
Jeśli nie ma wartości NULL, `OnCmdMsg` wypełnia elementy członkowskie *pTarget* i *PMF* struktury *pHandlerInfo* zamiast wysyłania polecenia. Zazwyczaj ten parametr powinien mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli komunikat jest obsługiwany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jest to główna procedura implementacji architektury poleceń struktury.

W czasie wykonywania `OnCmdMsg` wysyła polecenie do innych obiektów lub obsługuje polecenie przez wywołanie klasy głównej `CCmdTarget::OnCmdMsg`, która wykonuje rzeczywiste wyszukiwanie w mapie komunikatów. Aby uzyskać pełny opis domyślnego routingu poleceń, zobacz [temat Obsługa komunikatów i mapowanie](../../mfc/message-handling-and-mapping.md).

W rzadkich przypadkach można zastąpić tę funkcję elementu członkowskiego, aby zwiększyć standardowy routing poleceń struktury. Zapoznaj się z [uwagą techniczną 21](../../mfc/tn021-command-and-message-routing.md) , aby uzyskać szczegółowe informacje na temat architektury routingu poleceń.

W przypadku zastąpienia `OnCmdMsg`należy podać odpowiednią wartość dla *nCode*, kod powiadomienia polecenia i *pExtra*, które są zależne od wartości *nCode*. W poniższej tabeli wymieniono odpowiednie wartości:

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

##  <a name="onfinalrelease"></a>CCmdTarget:: OnFinalRelease

Wywoływane przez platformę, gdy następuje zwolnienie ostatniego odwołania OLE do lub z obiektu.

```
virtual void OnFinalRelease();
```

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, aby zapewnić specjalną obsługę tej sytuacji. Implementacja domyślna usuwa obiekt.

##  <a name="restorewaitcursor"></a>CCmdTarget:: RestoreWaitCursor

Wywołaj tę funkcję, aby przywrócić właściwy wskaźnik klepsydry po zmianie kursora systemu (na przykład po otwarciu okna komunikatu, a następnie zamknięciu w środku długotrwałej operacji).

```
void RestoreWaitCursor();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="see-also"></a>Zobacz także

[Przykład ACDUAL MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CCmdUI](../../mfc/reference/ccmdui-class.md)<br/>
[Klasa CDocument](../../mfc/reference/cdocument-class.md)<br/>
[Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Klasa CWinApp](../../mfc/reference/cwinapp-class.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Klasa CView](../../mfc/reference/cview-class.md)<br/>
[Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[Klasa COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)
