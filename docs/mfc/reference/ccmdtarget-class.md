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
ms.openlocfilehash: 1ef7040f3be1e4c30a6dc19e6093727299c9f1c3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752715"
---
# <a name="ccmdtarget-class"></a>Klasa CCmdTarget

Klasa podstawowa dla architektury mapy wiadomości biblioteki klas programu Microsoft Foundation.

## <a name="syntax"></a>Składnia

```
class CCmdTarget : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCmdTarget::CCmdTarget](#ccmdtarget)|Konstruuje `CCmdTarget` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCmdTarget::BeginWaitCursor](#beginwaitcursor)|Wyświetla kursor jako kursor klepsydry.|
|[CCmdTarget::DoOleVerb](#dooleverb)|Powoduje wykonanie akcji określonej przez zlecenie OLE.|
|[CCmdTarget::EnableAutomation](#enableautomation)|Umożliwia automatyzację `CCmdTarget` OLE dla obiektu.|
|[CCmdTarget::EnableConnections](#enableconnections)|Włącza wypalania zdarzeń za połączeniowe.|
|[CCmdTarget::EnableTypeLib](#enabletypelib)|Włącza bibliotekę typów obiektu.|
|[CCmdTarget::EndWaitCursor](#endwaitcursor)|Zwraca poprzedni kursor.|
|[CCmdTarget::EnumOleVerbs](#enumoleverbs)|Wylicza ole zleceń ole obiektu.|
|[CCmdTarget::FromIDispatch](#fromidispatch)|Zwraca wskaźnik do `CCmdTarget` obiektu skojarzonego `IDispatch` ze wskaźnikiem.|
|[CCmdTarget::GetDispatchIID](#getdispatchiid)|Pobiera identyfikator interfejsu wysyłki podstawowej.|
|[CCmdTarget::GetIDispatch](#getidispatch)|Zwraca wskaźnik do `IDispatch` obiektu skojarzonego `CCmdTarget` z obiektem.|
|[CCmdTarget::GetTypeInfoCount](#gettypeinfocount)|Pobiera liczbę interfejsów informacji o typie, które udostępnia obiekt.|
|[CCmdTarget::GetTypeInfoOfGuid](#gettypeinfoofguid)|Pobiera opis typu odpowiadający określonemu identyfikatorowi GUID.|
|[CCmdTarget::GetTypeLib](#gettypelib)|Pobiera wskaźnik do biblioteki typów.|
|[CCmdTarget::GetTypeLibCache](#gettypelibcache)|Pobiera pamięć podręczną biblioteki typów.|
|[CCmdTarget::IsInvokeAllowed](#isinvokeallowed)|Umożliwia wywołanie metody automatyzacji.|
|[CCmdTarget::IsResultExpected](#isresultexpected)|Zwraca wartość niezerową, jeśli funkcja automatyzacji powinna zwrócić wartość.|
|[CCmdTarget::OnCmdMsg](#oncmdmsg)|Trasy i wysyłki komunikatów poleceń.|
|[CCmdTarget::OnFinalRelease](#onfinalrelease)|Czyści po zwolnieniu ostatniego odwołania OLE.|
|[CCmdTarget::RestoreWaitCursor](#restorewaitcursor)|Przywraca kursor klepsydry.|

## <a name="remarks"></a>Uwagi

Mapa wiadomości kieruje polecenia lub wiadomości do zapisywanych funkcji członkowskich w celu ich obsługi. (Polecenie to komunikat z elementu menu, przycisku polecenia lub klawisza akceleratora).

Klasy struktury klucza `CCmdTarget` pochodzące z obejmują [CView](../../mfc/reference/cview-class.md), [CWinApp](../../mfc/reference/cwinapp-class.md), [CDocument](../../mfc/reference/cdocument-class.md), [CWnd](../../mfc/reference/cwnd-class.md)i [CFrameWnd](../../mfc/reference/cframewnd-class.md). Jeśli zamierzasz dla nowej klasy do obsługi wiadomości, wywołuj klasę z jednej z tych `CCmdTarget`klas pochodnych. Rzadko można wyprowadzić klasę `CCmdTarget` bezpośrednio.

Aby uzyskać przegląd obiektów `OnCmdMsg` docelowych i routingu poleceń, zobacz [Cele poleceń,](../../mfc/command-targets.md) [Routing poleceń](../../mfc/command-routing.md)i [Wiadomości mapowania](../../mfc/mapping-messages.md).

`CCmdTarget`zawiera funkcje członkowskie obsługujące wyświetlanie kursora klepsydry. Wyświetl kursor klepsydry, gdy oczekujesz, że polecenie zajmie zauważalny przedział czasu do wykonania.

Mapy wysyłki, podobnie jak mapy komunikatów, `IDispatch` są używane do uwidaczniania funkcji automatyzacji OLE. Uwidaczniając ten interfejs, inne aplikacje (takie jak Visual Basic) można wywołać w aplikacji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CCmdTarget`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="ccmdtargetbeginwaitcursor"></a><a name="beginwaitcursor"></a>CCmdTarget::BeginWaitCursor

Wywołanie tej funkcji, aby wyświetlić kursor jako klepsydry, gdy oczekujesz, że polecenie do wykonania zauważalny przedział czasu.

```cpp
void BeginWaitCursor();
```

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę funkcję, aby pokazać użytkownikowi, że `CDocument` jest zajęty, na przykład gdy obiekt ładuje lub zapisuje się do pliku.

Akcje nie `BeginWaitCursor` zawsze są skuteczne poza programem obsługi pojedynczej `OnSetCursor` wiadomości, ponieważ inne akcje, takie jak obsługa, mogą zmienić kursor.

Wywołanie, `EndWaitCursor` aby przywrócić poprzedni kursor.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="ccmdtargetccmdtarget"></a><a name="ccmdtarget"></a>CCmdTarget::CCmdTarget

Konstruuje `CCmdTarget` obiekt.

```
CCmdTarget();
```

## <a name="ccmdtargetdooleverb"></a><a name="dooleverb"></a>CCmdTarget::DoOleVerb

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
Identyfikator numeryczny czasownika.

*lpMsg*<br/>
Wskaźnik do struktury [MSG](/windows/win32/api/winuser/ns-winuser-msg) opisujące zdarzenie (takie jak dwukrotne kliknięcie), który wywołał zlecenie.

*hWndRodziciek*<br/>
Dojście okna dokumentu zawierającego obiekt.

*Lprect*<br/>
Wskaźnik do struktury [RECT](/windows/win32/api/windef/ns-windef-rect) zawierającej współrzędne w pikselach, które definiują prostokąt obwiedniowy obiektu w *hwndParent*.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli się powiedzie, w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest w zasadzie implementacją [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb). Możliwe akcje są wyliczone przez [CCmdTarget::EnumOleVerbs](#enumoleverbs).

## <a name="ccmdtargetenableautomation"></a><a name="enableautomation"></a>CCmdTarget::EnableAutomation

Wywołanie tej funkcji, aby włączyć automatyzację OLE dla obiektu.

```cpp
void EnableAutomation();
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest zazwyczaj wywoływana z konstruktora obiektu i powinny być wywoływane tylko wtedy, gdy mapa wysyłki została zadeklarowana dla klasy. Aby uzyskać więcej informacji na temat automatyzacji, zobacz artykuły [Klienci automatyzacji](../../mfc/automation-clients.md) i [serwery automatyzacji](../../mfc/automation-servers.md).

## <a name="ccmdtargetenableconnections"></a><a name="enableconnections"></a>CCmdTarget::EnableConnections

Włącza wypalania zdarzeń za połączeniowe.

```cpp
void EnableConnections();
```

### <a name="remarks"></a>Uwagi

Aby włączyć punkty połączenia, wywołać tę funkcję elementu członkowskiego w konstruktorze klasy pochodnej.

## <a name="ccmdtargetenabletypelib"></a><a name="enabletypelib"></a>CCmdTarget::EnableTypeLib

Włącza bibliotekę typów obiektu.

```cpp
void EnableTypeLib();
```

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji elementu członkowskiego `CCmdTarget`w konstruktorze obiektu pochodnego, jeśli zawiera informacje o typie.

## <a name="ccmdtargetendwaitcursor"></a><a name="endwaitcursor"></a>CCmdTarget::EndWaitCursor

Wywołanie tej funkcji po `BeginWaitCursor` wywołaniu funkcji elementu członkowskiego, aby powrócić z kursora klepsydry do poprzedniego kursora.

```cpp
void EndWaitCursor();
```

### <a name="remarks"></a>Uwagi

Struktura wywołuje również tę funkcję elementu członkowskiego po wywołaniu kursora klepsydry.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="ccmdtargetenumoleverbs"></a><a name="enumoleverbs"></a>CCmdTarget::EnumOleVerbs

Wylicza ole zleceń ole obiektu.

```
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```

### <a name="parameters"></a>Parametry

*ppenumOleVerb*<br/>
Wskaźnik do wskaźnika do interfejsu [IEnumOLEVERB.](/windows/win32/api/oleidl/nn-oleidl-ienumoleverb)

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli obiekt obsługuje co najmniej jeden \* czasownik OLE (w którym `IEnumOLEVERB` to przypadku *ppenumOleVerb* wskazuje na interfejs modułu wyliczacza), w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest w zasadzie implementacją [IOleObject::EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs).

## <a name="ccmdtargetfromidispatch"></a><a name="fromidispatch"></a>CCmdTarget::FromIDispatch

Wywołanie tej funkcji `IDispatch` do mapowania wskaźnika, odebrane `CCmdTarget` z funkcji elementów członkowskich `IDispatch` automatyzacji klasy, do obiektu, który implementuje interfejsy obiektu.

```
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```

### <a name="parameters"></a>Parametry

*lpDispatch (Niedysp.*<br/>
Wskaźnik do `IDispatch` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CCmdTarget` obiektu skojarzonego z *lpDispatch*. Ta funkcja zwraca `IDispatch` wartość NULL, jeśli obiekt `IDispatch` nie jest rozpoznawany jako obiekt Microsoft Foundation Class.

### <a name="remarks"></a>Uwagi

Wynikiem tej funkcji jest odwrotność wywołania funkcji `GetIDispatch`elementu członkowskiego .

## <a name="ccmdtargetgetdispatchiid"></a><a name="getdispatchiid"></a>CCmdTarget::GetDispatchIID

Pobiera identyfikator interfejsu wysyłki podstawowej.

```
virtual BOOL GetDispatchIID(IID* pIID);
```

### <a name="parameters"></a>Parametry

*pIID*<br/>
Wskaźnik do identyfikatora interfejsu (a [GUID](/windows/win32/api/guiddef/ns-guiddef-guid.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli się powiedzie, w przeciwnym razie FALSE. W przypadku \* powodzenia *identyfikator pIID* jest ustawiony na identyfikator interfejsu wysyłki podstawowej.

### <a name="remarks"></a>Uwagi

Klasy pochodne powinny zastąpić tę funkcję elementu członkowskiego `GetDispatchIID` (jeśli nie zostanie zastąpiona, zwraca WARTOŚĆ FAŁSZU). Zobacz [COleControl](../../mfc/reference/colecontrol-class.md).

## <a name="ccmdtargetgetidispatch"></a><a name="getidispatch"></a>CCmdTarget::GetIDispatch

Wywołanie tej funkcji elementu `IDispatch` członkowskiego, aby pobrać wskaźnik `IDispatch` z metody `IDispatch` automatyzacji, która zwraca wskaźnik lub przyjmuje wskaźnik przez odwołanie.

```
LPDISPATCH GetIDispatch(BOOL bAddRef);
```

### <a name="parameters"></a>Parametry

*bOdł.*<br/>
Określa, czy należy zwiększać liczbę odwołań dla obiektu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik `IDispatch` skojarzony z obiektem.

### <a name="remarks"></a>Uwagi

Dla obiektów, `EnableAutomation` które wywołują w ich konstruktorów, dzięki czemu `IDispatch` są włączone automatyzacji, `IDispatch` ta funkcja zwraca wskaźnik do implementacji klasy fundacji, który jest używany przez klientów, którzy komunikują się za pośrednictwem interfejsu. Wywołanie tej funkcji automatycznie dodaje odwołanie do wskaźnika, więc nie jest konieczne wywołanie [IUnknown::AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref).

## <a name="ccmdtargetgettypeinfocount"></a><a name="gettypeinfocount"></a>CCmdTarget::GetTypeInfoCount

Pobiera liczbę interfejsów informacji o typie, które udostępnia obiekt.

```
virtual UINT GetTypeInfoCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba interfejsów informacji o typie.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego zasadniczo implementuje [IDispatch::GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount).

Klasy pochodne powinny zastąpić tę funkcję, aby zwrócić liczbę dostarczonych interfejsów informacji o typie (0 lub 1). Jeśli nie zostanie `GetTypeInfoCount` zastąpiony, zwraca wartość 0. Aby zastąpić, należy użyć [makra IMPLEMENT_OLETYPELIB,](../../mfc/reference/type-library-access.md#implement_oletypelib) które `GetTypeLib` również `GetTypeLibCache`implementuje i .

## <a name="ccmdtargetgettypeinfoofguid"></a><a name="gettypeinfoofguid"></a>CCmdTarget::GetTypeInfoOfGuid

Pobiera opis typu odpowiadający określonemu identyfikatorowi GUID.

```
HRESULT GetTypeInfoOfGuid(
    LCID lcid,
    const GUID& guid,
    LPTYPEINFO* ppTypeInfo);
```

### <a name="parameters"></a>Parametry

*lcid*<br/>
Identyfikator ustawień regionalnych `LCID`( ).

*guid*<br/>
[GUID](/windows/win32/api/guiddef/ns-guiddef-guid opisu typu.

*ppTypeInfo (Polski)*<br/>
Wskaźnik do wskaźnika `ITypeInfo` do interfejsu.

### <a name="return-value"></a>Wartość zwracana

HRESULT wskazujący sukces lub niepowodzenie połączenia. Jeśli się \* powiedzie, *ppTypeInfo* wskazuje interfejs informacji o typie.

## <a name="ccmdtargetgettypelib"></a><a name="gettypelib"></a>CCmdTarget::GetTypeLib

Pobiera wskaźnik do biblioteki typów.

```
virtual HRESULT GetTypeLib(
    LCID lcid,
    LPTYPELIB* ppTypeLib);
```

### <a name="parameters"></a>Parametry

*lcid*<br/>
Identyfikator ustawień regionalnych (LCID).

*ppTypeLib (Polski)*<br/>
Wskaźnik do wskaźnika `ITypeLib` do interfejsu.

### <a name="return-value"></a>Wartość zwracana

HRESULT wskazujący sukces lub niepowodzenie połączenia. Jeśli się \* powiedzie, *ppTypeLib* wskazuje interfejs biblioteki typów.

### <a name="remarks"></a>Uwagi

Klasy pochodne powinny zastąpić tę funkcję elementu członkowskiego `GetTypeLib` (jeśli nie zostanie zastąpiona, zwraca TYPE_E_CANTLOADLIBRARY). Użyj makra [IMPLEMENT_OLETYPELIB,](../../mfc/reference/type-library-access.md#implement_oletypelib) które również `GetTypeInfoCount` implementuje i `GetTypeLibCache`.

## <a name="ccmdtargetgettypelibcache"></a><a name="gettypelibcache"></a>CCmdTarget::GetTypeLibCache

Pobiera pamięć podręczną biblioteki typów.

```
virtual CTypeLibCache* GetTypeLibCache();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CTypeLibCache` obiektu.

### <a name="remarks"></a>Uwagi

Klasy pochodne powinny zastąpić tę funkcję elementu członkowskiego `GetTypeLibCache` (jeśli nie zostanie zastąpiona, zwraca wartość NULL). Użyj makra [IMPLEMENT_OLETYPELIB,](../../mfc/reference/type-library-access.md#implement_oletypelib) które również `GetTypeInfoCount` implementuje i `GetTypeLib`.

## <a name="ccmdtargetisinvokeallowed"></a><a name="isinvokeallowed"></a>CCmdTarget::IsInvokeAllowed

Ta funkcja jest wywoływana przez `IDispatch::Invoke` implementację MFC w celu określenia, czy dana metoda automatyzacji (identyfikowane przez *dispid*) mogą być wywoływane.

```
virtual BOOL IsInvokeAllowed(DISPID dispid);
```

### <a name="parameters"></a>Parametry

*Dispid*<br/>
Identyfikator wysyłki.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli można wywołać metodę, w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli `IsInvokeAllowed` zwraca `Invoke` wartość TRUE, przystępuje do wywołania metody; w `Invoke` przeciwnym razie zakończy się niepowodzeniem, zwracając E_UNEXPECTED.

Klasy pochodne mogą zastąpić tę funkcję, aby zwrócić odpowiednie `IsInvokeAllowed` wartości (jeśli nie zostanie zastąpiona, zwraca wartość PRAWDA). Zobacz w szczególności [COleControl::IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed).

## <a name="ccmdtargetisresultexpected"></a><a name="isresultexpected"></a>CCmdTarget::IsResultExpected

Służy `IsResultExpected` do ustalenia, czy klient oczekuje wartości zwracanej z jego wywołania do funkcji automatyzacji.

```
BOOL IsResultExpected();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja automatyzacji powinna zwracać wartość; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Interfejs OLE dostarcza informacje do MFC o tym, czy klient używa lub ignoruje wynik wywołania funkcji, a MFC `IsResultExpected`z kolei używa tych informacji do określenia wyniku wywołania . Jeśli produkcja wartości zwracanej jest czasochłonna lub zasobochłonna, można zwiększyć wydajność, wywołując tę funkcję przed obliczeniem wartości zwracanej.

Ta funkcja zwraca 0 tylko raz, dzięki czemu otrzymasz prawidłowe wartości zwracane z innych funkcji automatyzacji, jeśli wywołasz je z funkcji automatyzacji, która została wywołana przez klienta.

`IsResultExpected`zwraca wartość niezerową, jeśli jest wywoływana, gdy wywołane jest wywołanie funkcji automatyzacji.

## <a name="ccmdtargetoncmdmsg"></a><a name="oncmdmsg"></a>CCmdTarget::OnCmdMsg

Wywoływane przez strukturę do kierowania i wysyłania komunikatów poleceń i obsługi aktualizacji poleceń obiektów interfejsu użytkownika.

```
virtual BOOL OnCmdMsg(
    UINT nID,
    int nCode,
    void* pExtra,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Zawiera identyfikator polecenia.

*kod n*<br/>
Identyfikuje kod powiadomienia polecenia. Zobacz **Uwagi, aby** uzyskać więcej informacji na temat wartości *dla nCode*.

*pExtra (własówce)*<br/>
Używany zgodnie z wartością *nCode*. Zobacz **Uwagi, aby** uzyskać więcej informacji na temat *pExtra*.

*pHandlerInfo*<br/>
Jeśli nie `OnCmdMsg` null, wypełnia *pTarget* i *pmf* członków *pHandlerInfo* struktury zamiast wysyłania polecenia. Zazwyczaj ten parametr powinien mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wiadomość jest obsługiwana; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jest to główna procedura implementacji architektury polecenia framework.

W czasie `OnCmdMsg` wykonywania wywołuje polecenie do innych obiektów lub obsługuje samo `CCmdTarget::OnCmdMsg`polecenie, wywołując klasę główną, która wykonuje rzeczywiste wyszukiwanie mapy wiadomości. Aby uzyskać pełny opis domyślnego routingu poleceń, zobacz [Tematy obsługi i mapowania wiadomości](../../mfc/message-handling-and-mapping.md).

W rzadkich przypadkach można zastąpić tę funkcję elementu członkowskiego, aby rozszerzyć standardowy routing poleceń platformy. Szczegółowe informacje na temat architektury routingu poleceń można znaleźć w [notatce technicznej 21.](../../mfc/tn021-command-and-message-routing.md)

W przypadku zastąpienia `OnCmdMsg`, należy podać odpowiednią wartość dla *nCode*, kod powiadomienia polecenia i *pExtra*, który zależy od wartości *nCode*. W poniższej tabeli wymieniono ich odpowiednie wartości:

|Wartość *nCode*|*pWarta procentowa*|
|-------------------|--------------------|
|CN_COMMAND|[Ccmdui](../../mfc/reference/ccmdui-class.md)\*|
|CN_EVENT|AFX_EVENT\*|
|CN_UPDATE_COMMAND_UI|Ccmdui\*|
|CN_OLECOMMAND|[Colecmdui](../../mfc/reference/colecmdui-class.md)\*|
|CN_OLE_UNREGISTER|NULL|

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]

## <a name="ccmdtargetonfinalrelease"></a><a name="onfinalrelease"></a>CCmdTarget::OnFinalRelease

Wywoływane przez platformę, gdy ostatnie odwołanie OLE do lub z obiektu jest zwolniony.

```
virtual void OnFinalRelease();
```

### <a name="remarks"></a>Uwagi

Zastąd w tej funkcji należy zastąpić tę funkcję, aby zapewnić specjalną obsługę w tej sytuacji. Domyślna implementacja usuwa obiekt.

## <a name="ccmdtargetrestorewaitcursor"></a><a name="restorewaitcursor"></a>CCmdTarget::RestoreWaitCursor

Wywołanie tej funkcji, aby przywrócić odpowiedni kursor klepsydry po zmianie kursora systemowego (na przykład po otwarciu okna komunikatu, a następnie zamknięciu w trakcie długiej operacji).

```cpp
void RestoreWaitCursor();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="see-also"></a>Zobacz też

[Próbka MFC ACDUAL](../../overview/visual-cpp-samples.md)<br/>
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
