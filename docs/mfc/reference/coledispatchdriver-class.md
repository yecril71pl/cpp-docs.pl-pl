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
ms.openlocfilehash: 265fca7288ca2aa760fb1faffa94f9d74896a975
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214103"
---
# <a name="coledispatchdriver-class"></a>Klasa COleDispatchDriver

Implementuje po stronie klienta Automatyzacja OLE.

## <a name="syntax"></a>Składnia

```
class COleDispatchDriver
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDispatchDriver:: COleDispatchDriver](#coledispatchdriver)|Konstruuje `COleDispatchDriver` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDispatchDriver:: AttachDispatch](#attachdispatch)|Dołącza `IDispatch` połączenie do `COleDispatchDriver` obiektu.|
|[COleDispatchDriver:: nie wysyłaj](#createdispatch)|Tworzy `IDispatch` połączenie i dołącza je do `COleDispatchDriver` obiektu.|
|[COleDispatchDriver::D etachDispatch](#detachdispatch)|Odłącza `IDispatch` połączenie bez jego zwolnienia.|
|[COleDispatchDriver:: GetProperty](#getproperty)|Pobiera właściwość automatyzacji.|
|[COleDispatchDriver:: InvokeHelper](#invokehelper)|Pomocnik wywoływania metod automatyzacji.|
|[COleDispatchDriver:: ReleaseDispatch](#releasedispatch)|Zwalnia `IDispatch` połączenie.|
|[COleDispatchDriver:: SetProperty](#setproperty)|Ustawia właściwość automatyzacji.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDispatchDriver:: operator =](#operator_eq)|Kopiuje wartość źródłową do `COleDispatchDriver` obiektu.|
|[COleDispatchDriver:: operator LPDISPATCH](#operator_lpdispatch)|Uzyskuje dostęp do podstawowego `IDispatch` wskaźnika.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleDispatchDriver:: m_bAutoRelease](#m_bautorelease)|Określa, czy zwalniać dane w `IDispatch` trakcie `ReleaseDispatch` lub zniszczenie obiektu.|
|[COleDispatchDriver:: m_lpDispatch](#m_lpdispatch)|Wskazuje wskaźnik do `IDispatch` interfejsu dołączonego do tej `COleDispatchDriver` .|

## <a name="remarks"></a>Uwagi

`COleDispatchDriver`nie ma klasy bazowej.

Interfejsy wysyłania OLE zapewniają dostęp do metod i właściwości obiektu. Funkcje składowe `COleDispatchDriver` dołączania, odłączania, tworzenia i zwalniania połączenia wysyłki typu `IDispatch` . Inne funkcje członkowskie używają list argumentów zmiennych, aby uprościć wywoływanie `IDispatch::Invoke` .

Ta klasa może być używana bezpośrednio, ale zazwyczaj jest używana tylko przez klasy utworzone przez Kreatora dodawania klasy. Podczas tworzenia nowych klas C++ przez zaimportowanie biblioteki typów, nowe klasy są wyprowadzane z `COleDispatchDriver` .

Aby uzyskać więcej informacji na temat korzystania z programu `COleDispatchDriver` , zobacz następujące artykuły:

- [Klienci automatyzacji](../../mfc/automation-clients.md)

- [Serwery automatyzacji](../../mfc/automation-servers.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`COleDispatchDriver`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDISP. h

## <a name="coledispatchdriverattachdispatch"></a><a name="attachdispatch"></a>COleDispatchDriver:: AttachDispatch

Wywołaj `AttachDispatch` funkcję członkowską, aby dołączyć `IDispatch` wskaźnik do `COleDispatchDriver` obiektu. Aby uzyskać więcej informacji, zobacz [implementowanie interfejsu IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

```cpp
void AttachDispatch(
    LPDISPATCH lpDispatch,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>Parametry

*lpDispatch*<br/>
Wskaźnik do obiektu OLE `IDispatch` , który ma zostać dołączony do `COleDispatchDriver` obiektu.

*bAutoRelease*<br/>
Określa, czy wysyłka ma zostać wydana, gdy ten obiekt wykracza poza zakres.

### <a name="remarks"></a>Uwagi

Ta funkcja zwalnia wszystkie wskaźniki `IDispatch` , które są już dołączone do `COleDispatchDriver` obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#3](../../mfc/codesnippet/cpp/coledispatchdriver-class_1.cpp)]

## <a name="coledispatchdrivercoledispatchdriver"></a><a name="coledispatchdriver"></a>COleDispatchDriver:: COleDispatchDriver

Konstruuje `COleDispatchDriver` obiekt.

```
COleDispatchDriver();
COleDispatchDriver(LPDISPATCH lpDispatch, BOOL bAutoRelease = TRUE);
COleDispatchDriver(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>Parametry

*lpDispatch*<br/>
Wskaźnik do obiektu OLE `IDispatch` , który ma zostać dołączony do `COleDispatchDriver` obiektu.

*bAutoRelease*<br/>
Określa, czy wysyłka ma zostać wydana, gdy ten obiekt wykracza poza zakres.

*dispatchSrc*<br/>
Odwołanie do istniejącego `COleDispatchDriver` obiektu.

### <a name="remarks"></a>Uwagi

Formularz `COleDispatchDriver` ( `LPDISPATCH lpDispatch` , **bool** `bAutoRelease`  =  **true**) łączy Interfejs [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) .

Formularz `COleDispatchDriver` ( **`const`** `COleDispatchDriver` &  `dispatchSrc` ) kopiuje istniejący `COleDispatchDriver` obiekt i zwiększa liczbę odwołań.

Formularz `COleDispatchDriver` () tworzy `COleDispatchDriver` obiekt, ale nie łączy się z `IDispatch` interfejsem. Przed użyciem `COleDispatchDriver` () bez argumentów należy połączyć się z `IDispatch` nim za pomocą [COleDispatchDriver::](#createdispatch) lub [COleDispatchDriver:: AttachDispatch](#attachdispatch). Aby uzyskać więcej informacji, zobacz [implementowanie interfejsu IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

### <a name="example"></a>Przykład

  Zobacz przykład dla [COleDispatchDriver::](#createdispatch)...

## <a name="coledispatchdrivercreatedispatch"></a><a name="createdispatch"></a>COleDispatchDriver:: nie wysyłaj

Tworzy obiekt interfejsu [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) i dołącza go do `COleDispatchDriver` obiektu.

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
Identyfikator klasy `IDispatch` obiektu połączenia, który ma zostać utworzony.

*pError*<br/>
Wskaźnik do obiektu wyjątku OLE, który będzie przechowywać kod stanu wynikający z utworzenia.

*lpszProgID*<br/>
Wskaźnik na identyfikator programistyczny, taki jak "Excel.Document. 5" obiektu automatyzacji, dla którego ma zostać utworzony obiekt wysyłki.

### <a name="return-value"></a>Wartość zwracana

Niezerowe po powodzeniu; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#4](../../mfc/codesnippet/cpp/coledispatchdriver-class_2.cpp)]

## <a name="coledispatchdriverdetachdispatch"></a><a name="detachdispatch"></a>COleDispatchDriver::D etachDispatch

Odłącza bieżące `IDispatch` połączenie z tego obiektu.

```
LPDISPATCH DetachDispatch();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do wcześniej dołączonego obiektu OLE `IDispatch` .

### <a name="remarks"></a>Uwagi

`IDispatch`Nie jest on wydawany.

Aby uzyskać więcej informacji na temat typu LPDISPATCH, zobacz [implementowanie interfejsu IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#5](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]

## <a name="coledispatchdrivergetproperty"></a><a name="getproperty"></a>COleDispatchDriver:: GetProperty

Pobiera właściwość obiektu określoną przez *dwDispID*.

```cpp
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

## <a name="coledispatchdriverinvokehelper"></a><a name="invokehelper"></a>COleDispatchDriver:: InvokeHelper

Wywołuje metodę obiektu lub właściwość określoną przez *dwDispID*w kontekście określonym przez *wFlags*.

```cpp
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
Flagi opisujące kontekst wywołania do `IDispatch::Invoke` . . Aby uzyskać listę możliwych wartości, zobacz parametr *wFlags* w elemencie [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) w Windows SDK.

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
|VT_EMPTY|**`void`**|
|VT_I2|**`short`**|
|VT_I4|**`long`**|
|VT_R4|**`float`**|
|VT_R8|**`double`**|
|VT_CY|**CY**|
|VT_DATE|**DNIU**|
|VT_BSTR|ANI|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|**LOGICZNA**|
|VT_VARIANT|**TYPU**|
|VT_UNKNOWN|LPUNKNOWN|

Argument *pbParamInfo* jest rozdzieloną spacjami listą stałych **VTS_** . Co najmniej jedna z tych wartości rozdzielonych spacjami (nie przecinkami) określa listę parametrów funkcji. Możliwe wartości są wyświetlane za pomocą makra [EVENT_CUSTOM](event-maps.md#event_custom) .

Ta funkcja konwertuje parametry na wartości VARIANTARG, a następnie wywołuje metodę [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) . Jeśli wywołanie `Invoke` zakończy się niepowodzeniem, ta funkcja zgłosi wyjątek. Jeśli SCODE (kod stanu) zwrócony przez `IDispatch::Invoke` jest DISP_E_EXCEPTION, ta funkcja zgłasza obiekt [COleException](../../mfc/reference/coleexception-class.md) ; w przeciwnym razie zgłasza [COleDispatchException](../../mfc/reference/coledispatchexception-class.md).

Aby uzyskać więcej informacji, zobacz [VARIANTARG](/windows/win32/api/oaidl/ns-oaidl-variant), [implementując interfejs IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface), [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)i [strukturę kodów błędów com](/windows/win32/com/structure-of-com-error-codes) w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [COleDispatchDriver::](#createdispatch)...

## <a name="coledispatchdriverm_bautorelease"></a><a name="m_bautorelease"></a>COleDispatchDriver:: m_bAutoRelease

W przypadku wartości TRUE obiekt COM, do którego uzyskuje się dostęp [m_lpDispatch](#m_lpdispatch) , zostanie automatycznie wypublikowany, gdy zostanie wywołana [ReleaseDispatch](#releasedispatch) lub gdy ten `COleDispatchDriver` obiekt zostanie zniszczony.

```
BOOL m_bAutoRelease;
```

### <a name="remarks"></a>Uwagi

Domyślnie `m_bAutoRelease` jest ustawiona na wartość true w konstruktorze.

Aby uzyskać więcej informacji o zwalnianiu obiektów COM, zobacz [implementację zliczania odwołań](/windows/win32/com/implementing-reference-counting) i [IUnknown:: Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#9](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]

## <a name="coledispatchdriverm_lpdispatch"></a><a name="m_lpdispatch"></a>COleDispatchDriver:: m_lpDispatch

Wskaźnik do `IDispatch` interfejsu dołączonego do tej `COleDispatchDriver` .

```
LPDISPATCH m_lpDispatch;
```

### <a name="remarks"></a>Uwagi

`m_lpDispatch`Element członkowski danych jest publiczną zmienną typu LPDISPATCH.

Aby uzyskać więcej informacji, zobacz [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [COleDispatchDriver:: AttachDispatch](#attachdispatch).

## <a name="coledispatchdriveroperator-"></a><a name="operator_eq"></a>COleDispatchDriver:: operator =

Kopiuje wartość źródłową do `COleDispatchDriver` obiektu.

```
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>Parametry

*dispatchSrc*<br/>
Wskaźnik do istniejącego `COleDispatchDriver` obiektu.

## <a name="coledispatchdriveroperator-lpdispatch"></a><a name="operator_lpdispatch"></a>COleDispatchDriver:: operator LPDISPATCH

Uzyskuje dostęp do podstawowego `IDispatch` wskaźnika `COleDispatchDriver` obiektu.

```
operator LPDISPATCH();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#8](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]

## <a name="coledispatchdriverreleasedispatch"></a><a name="releasedispatch"></a>COleDispatchDriver:: ReleaseDispatch

Zwalnia `IDispatch` połączenie. Aby uzyskać więcej informacji, zobacz [implementowanie interfejsu IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) .

```cpp
void ReleaseDispatch();
```

### <a name="remarks"></a>Uwagi

Jeśli dla tego połączenia ustawiono opcję autowydanie, ta funkcja wywołuje `IDispatch::Release` przed zwolnieniem interfejsu.

### <a name="example"></a>Przykład

  Zobacz przykład dla [COleDispatchDriver:: AttachDispatch](#attachdispatch).

## <a name="coledispatchdriversetproperty"></a><a name="setproperty"></a>COleDispatchDriver:: SetProperty

Ustawia właściwość obiektu OLE określoną przez *dwDispID*.

```cpp
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

## <a name="see-also"></a>Zobacz także

[Przykład CALCDRIV MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład ACDUAL MFC](../../overview/visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)
