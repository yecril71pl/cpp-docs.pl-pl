---
title: Klasa COleDispatchDriver
ms.date: 11/04/2016
f1_keywords:
- COleDispatchDriver
- AFXDISP/COleDispatchDriver
- AFXDISP/COleDispatchDriver::COleDispatchDriver
- AFXDISP/COleDispatchDriver::AttachDispatch
- AFXDISP/COleDispatchDriver::CreateDispatch
- AFXDISP/COleDispatchDriver::DetachDispatch
- AFXDISP/COleDispatchDriver::GetProperty
- AFXDISP/COleDispatchDriver::InvokeHelper
- AFXDISP/COleDispatchDriver::ReleaseDispatch
- AFXDISP/COleDispatchDriver::SetProperty
- AFXDISP/COleDispatchDriver::m_bAutoRelease
- AFXDISP/COleDispatchDriver::m_lpDispatch
helpviewer_keywords:
- COleDispatchDriver [MFC], COleDispatchDriver
- COleDispatchDriver [MFC], AttachDispatch
- COleDispatchDriver [MFC], CreateDispatch
- COleDispatchDriver [MFC], DetachDispatch
- COleDispatchDriver [MFC], GetProperty
- COleDispatchDriver [MFC], InvokeHelper
- COleDispatchDriver [MFC], ReleaseDispatch
- COleDispatchDriver [MFC], SetProperty
- COleDispatchDriver [MFC], m_bAutoRelease
- COleDispatchDriver [MFC], m_lpDispatch
ms.assetid: 3ed98daf-cdc7-4374-8a0c-cf695a8d3657
ms.openlocfilehash: fa88147b57b0506f7f9ab96d4a5d2f43fdd75458
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421262"
---
# <a name="coledispatchdriver-class"></a>Klasa COleDispatchDriver

Implementuje po stronie klienta Automatyzacja OLE.

## <a name="syntax"></a>Składnia

```
class COleDispatchDriver
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COleDispatchDriver:: COleDispatchDriver](#coledispatchdriver)|Konstruuje obiekt `COleDispatchDriver`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COleDispatchDriver:: AttachDispatch](#attachdispatch)|Dołącza `IDispatch` połączenie z obiektem `COleDispatchDriver`.|
|[COleDispatchDriver:: nie wysyłaj](#createdispatch)|Tworzy połączenie `IDispatch` i dołącza je do obiektu `COleDispatchDriver`.|
|[COleDispatchDriver::D etachDispatch](#detachdispatch)|Odłącza `IDispatch` połączenie bez jego zwolnienia.|
|[COleDispatchDriver:: GetProperty](#getproperty)|Pobiera właściwość automatyzacji.|
|[COleDispatchDriver:: InvokeHelper](#invokehelper)|Pomocnik wywoływania metod automatyzacji.|
|[COleDispatchDriver:: ReleaseDispatch](#releasedispatch)|Zwalnia `IDispatch` połączenie.|
|[COleDispatchDriver:: SetProperty](#setproperty)|Ustawia właściwość automatyzacji.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COleDispatchDriver:: operator =](#operator_eq)|Kopiuje wartość źródłową do `COleDispatchDriver` obiektu.|
|[COleDispatchDriver:: operator LPDISPATCH](#operator_lpdispatch)|Uzyskuje dostęp do bazowego wskaźnika `IDispatch`.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COleDispatchDriver:: m_bAutoRelease](#m_bautorelease)|Określa, czy `IDispatch` podczas niszczenia `ReleaseDispatch` czy obiektu.|
|[COleDispatchDriver:: m_lpDispatch](#m_lpdispatch)|Wskazuje wskaźnik do interfejsu `IDispatch` dołączonego do tego `COleDispatchDriver`.|

## <a name="remarks"></a>Uwagi

`COleDispatchDriver` nie ma klasy bazowej.

Interfejsy wysyłania OLE zapewniają dostęp do metod i właściwości obiektu. Funkcje składowe `COleDispatchDriver` dołączania, odłączania, tworzenia i zwalniania połączenia wysyłki typu `IDispatch`. Inne funkcje członkowskie używają list argumentów zmiennych, aby uprościć wywoływanie `IDispatch::Invoke`.

Ta klasa może być używana bezpośrednio, ale zazwyczaj jest używana tylko przez klasy utworzone przez Kreatora dodawania klasy. Podczas tworzenia nowych C++ klas przez zaimportowanie biblioteki typów, nowe klasy są wyprowadzane z `COleDispatchDriver`.

Aby uzyskać więcej informacji na temat korzystania z `COleDispatchDriver`, zobacz następujące artykuły:

- [Klienci automatyzacji](../../mfc/automation-clients.md)

- [Serwery automatyzacji](../../mfc/automation-servers.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`COleDispatchDriver`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDISP. h

##  <a name="attachdispatch"></a>COleDispatchDriver:: AttachDispatch

Wywołaj funkcję członkowską `AttachDispatch`, aby dołączyć wskaźnik `IDispatch` do obiektu `COleDispatchDriver`. Aby uzyskać więcej informacji, zobacz [implementowanie interfejsu IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

```
void AttachDispatch(
    LPDISPATCH lpDispatch,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>Parametry

*lpDispatch*<br/>
Wskaźnik do obiektu OLE `IDispatch`, który ma zostać dołączony do obiektu `COleDispatchDriver`.

*bAutoRelease*<br/>
Określa, czy wysyłka ma zostać wydana, gdy ten obiekt wykracza poza zakres.

### <a name="remarks"></a>Uwagi

Ta funkcja zwalnia dowolny `IDispatch` wskaźnik, który jest już dołączony do obiektu `COleDispatchDriver`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#3](../../mfc/codesnippet/cpp/coledispatchdriver-class_1.cpp)]

##  <a name="coledispatchdriver"></a>COleDispatchDriver:: COleDispatchDriver

Konstruuje obiekt `COleDispatchDriver`.

```
COleDispatchDriver();
COleDispatchDriver(LPDISPATCH lpDispatch, BOOL bAutoRelease = TRUE);
COleDispatchDriver(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>Parametry

*lpDispatch*<br/>
Wskaźnik do obiektu OLE `IDispatch`, który ma zostać dołączony do obiektu `COleDispatchDriver`.

*bAutoRelease*<br/>
Określa, czy wysyłka ma zostać wydana, gdy ten obiekt wykracza poza zakres.

*dispatchSrc*<br/>
Odwołanie do istniejącego obiektu `COleDispatchDriver`.

### <a name="remarks"></a>Uwagi

Formularz `COleDispatchDriver`(`LPDISPATCH lpDispatch`, **BOOL**`bAutoRelease` = **true**) łączy Interfejs [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) .

Formularz `COleDispatchDriver`( **const**`COleDispatchDriver`& `dispatchSrc`) kopiuje istniejący obiekt `COleDispatchDriver` i zwiększa liczbę odwołań.

Formularz `COleDispatchDriver`() tworzy obiekt `COleDispatchDriver`, ale nie łączy się z interfejsem `IDispatch`. Przed użyciem `COleDispatchDriver`() bez argumentów należy podłączyć `IDispatch` do niego przy użyciu jednej z [COleDispatchDriver::](#createdispatch) lub [COleDispatchDriver:: AttachDispatch](#attachdispatch). Aby uzyskać więcej informacji, zobacz [implementowanie interfejsu IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

### <a name="example"></a>Przykład

  Zobacz przykład dla [COleDispatchDriver::](#createdispatch)...

##  <a name="createdispatch"></a>COleDispatchDriver:: nie wysyłaj

Tworzy obiekt interfejsu [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) i dołącza go do obiektu `COleDispatchDriver`.

```
BOOL CreateDispatch(
    REFCLSID clsid,
    COleException* pError = NULL);

BOOL CreateDispatch(
    LPCTSTR lpszProgID,
    COleException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
Identyfikator klasy obiektu połączenia `IDispatch`, który ma zostać utworzony.

*pError*<br/>
Wskaźnik do obiektu wyjątku OLE, który będzie przechowywać kod stanu wynikający z utworzenia.

*lpszProgID*<br/>
Wskaźnik na identyfikator programistyczny, taki jak "Excel. Document. 5" obiektu automatyzacji, dla którego ma zostać utworzony obiekt wysyłki.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe po powodzeniu; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#4](../../mfc/codesnippet/cpp/coledispatchdriver-class_2.cpp)]

##  <a name="detachdispatch"></a>COleDispatchDriver::D etachDispatch

Odłącza bieżące połączenie `IDispatch` od tego obiektu.

```
LPDISPATCH DetachDispatch();
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do wcześniej dołączonego obiektu OLE `IDispatch`.

### <a name="remarks"></a>Uwagi

Nie wydano `IDispatch`.

Aby uzyskać więcej informacji na temat typu LPDISPATCH, zobacz [implementowanie interfejsu IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#5](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]

##  <a name="getproperty"></a>COleDispatchDriver:: GetProperty

Pobiera właściwość obiektu określoną przez *dwDispID*.

```
void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Określa właściwość, która ma zostać pobrana.

*vtProp*<br/>
Określa właściwość, która ma zostać pobrana. Aby uzyskać możliwe wartości, zobacz sekcję Uwagi dla [COleDispatchDriver:: InvokeHelper](#invokehelper).

*pvProp*<br/>
Adres zmiennej, która będzie odbierać wartość właściwości. Musi być zgodny z typem określonym przez *vtProp*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#6](../../mfc/codesnippet/cpp/coledispatchdriver-class_4.cpp)]

##  <a name="invokehelper"></a>COleDispatchDriver:: InvokeHelper

Wywołuje metodę obiektu lub właściwość określoną przez *dwDispID*w kontekście określonym przez *wFlags*.

```
void AFX_CDECL InvokeHelper(
    DISPID dwDispID,
    WORD wFlags,
    VARTYPE vtRet,
    void* pvRet,
    const BYTE* pbParamInfo, ...);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Identyfikuje metodę lub właściwość, która ma zostać wywołana.

*wFlags*<br/>
Flagi opisujące kontekst wywołania do `IDispatch::Invoke`. . Aby uzyskać listę możliwych wartości, zobacz parametr *wFlags* w elemencie [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) w Windows SDK.

*vtRet*<br/>
Określa typ zwracanej wartości. Aby uzyskać możliwe wartości, zobacz sekcję Uwagi.

*pvRet*<br/>
Adres zmiennej, która będzie odbierać wartość właściwości lub wartość zwracaną. Musi być zgodny z typem określonym przez *vtRet*.

*pbParamInfo*<br/>
Wskaźnik na ciąg zakończony znakiem null bajtów określający typy parametrów po *pbParamInfo*.

*...*<br/>
Zmienna lista parametrów, typów określonych w *pbParamInfo*.

### <a name="remarks"></a>Uwagi

Parametr *pbParamInfo* określa typy parametrów przesłane do metody lub właściwości. Zmienna lista argumentów jest reprezentowana przez **...** w deklaracji składni.

Możliwe wartości argumentu *vtRet* są pobierane z wyliczenia VarEnum. Dopuszczalne są następujące wartości:

|Symbol|Typ zwracany|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|**CY**|
|VT_DATE|**DATE**|
|VT_BSTR|ANI|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|**LOGICZNA**|
|VT_VARIANT|**TYPU**|
|VT_UNKNOWN|LPUNKNOWN|

Argument *pbParamInfo* jest rozdzieloną spacjami listą stałych **VTS_** . Co najmniej jedna z tych wartości rozdzielonych spacjami (nie przecinkami) określa listę parametrów funkcji. Możliwe wartości są wyświetlane za pomocą makra [EVENT_CUSTOM](event-maps.md#event_custom) .

Ta funkcja konwertuje parametry na wartości VARIANTARG, a następnie wywołuje metodę [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) . Jeśli wywołanie `Invoke` nie powiedzie się, ta funkcja zgłosi wyjątek. Jeśli SCODE (kod stanu) zwrócony przez `IDispatch::Invoke` jest DISP_E_EXCEPTION, ta funkcja zgłasza obiekt [COleException](../../mfc/reference/coleexception-class.md) ; w przeciwnym razie zgłasza [COleDispatchException](../../mfc/reference/coledispatchexception-class.md).

Aby uzyskać więcej informacji, zobacz [VARIANTARG](/windows/win32/api/oaidl/ns-oaidl-variant), [implementując interfejs IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface), [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)i [strukturę kodów błędów com](/windows/win32/com/structure-of-com-error-codes) w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [COleDispatchDriver::](#createdispatch)...

##  <a name="m_bautorelease"></a>COleDispatchDriver:: m_bAutoRelease

W przypadku wartości TRUE obiekt COM, do którego uzyskuje się dostęp [m_lpDispatch](#m_lpdispatch) , zostanie automatycznie wypublikowany, gdy zostanie wywołana [ReleaseDispatch](#releasedispatch) lub gdy ten obiekt `COleDispatchDriver` zostanie zniszczony.

```
BOOL m_bAutoRelease;
```

### <a name="remarks"></a>Uwagi

Domyślnie `m_bAutoRelease` ma wartość TRUE w konstruktorze.

Aby uzyskać więcej informacji o zwalnianiu obiektów COM, zobacz [implementację zliczania odwołań](/windows/win32/com/implementing-reference-counting) i [IUnknown:: Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#9](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]

##  <a name="m_lpdispatch"></a>COleDispatchDriver:: m_lpDispatch

Wskaźnik do interfejsu `IDispatch` dołączonego do tego `COleDispatchDriver`.

```
LPDISPATCH m_lpDispatch;
```

### <a name="remarks"></a>Uwagi

Element członkowski danych `m_lpDispatch` jest publiczną zmienną typu LPDISPATCH.

Aby uzyskać więcej informacji, zobacz [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [COleDispatchDriver:: AttachDispatch](#attachdispatch).

##  <a name="operator_eq"></a>COleDispatchDriver:: operator =

Kopiuje wartość źródłową do `COleDispatchDriver` obiektu.

```
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>Parametry

*dispatchSrc*<br/>
Wskaźnik do istniejącego obiektu `COleDispatchDriver`.

##  <a name="operator_lpdispatch"></a>COleDispatchDriver:: operator LPDISPATCH

Uzyskuje dostęp do podstawowego wskaźnika `IDispatch` obiektu `COleDispatchDriver`.

```
operator LPDISPATCH();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#8](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]

##  <a name="releasedispatch"></a>COleDispatchDriver:: ReleaseDispatch

Zwalnia `IDispatch` połączenie. Aby uzyskać więcej informacji, zobacz [implementowanie interfejsu IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) .

```
void ReleaseDispatch();
```

### <a name="remarks"></a>Uwagi

Jeśli dla tego połączenia ustawiono opcję autowydanie, ta funkcja wywołuje `IDispatch::Release` przed zwolnieniem interfejsu.

### <a name="example"></a>Przykład

  Zobacz przykład dla [COleDispatchDriver:: AttachDispatch](#attachdispatch).

##  <a name="setproperty"></a>COleDispatchDriver:: SetProperty

Ustawia właściwość obiektu OLE określoną przez *dwDispID*.

```
void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Określa właściwość, która ma zostać ustawiona.

*vtProp*<br/>
Określa typ właściwości, która ma zostać ustawiona. Aby uzyskać możliwe wartości, zobacz sekcję Uwagi dla [COleDispatchDriver:: InvokeHelper](#invokehelper).

*...*<br/>
Pojedynczy parametr typu określony przez *vtProp*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#7](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]

## <a name="see-also"></a>Zobacz też

[Przykład CALCDRIV MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład ACDUAL MFC](../../overview/visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)
