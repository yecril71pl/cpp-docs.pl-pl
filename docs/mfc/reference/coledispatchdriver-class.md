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
ms.openlocfilehash: 2b52ed3137a9a515278e018d69751aedaddb0cf1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753882"
---
# <a name="coledispatchdriver-class"></a>Klasa COleDispatchDriver

Implementuje po stronie klienta automatyzacji OLE.

## <a name="syntax"></a>Składnia

```
class COleDispatchDriver
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDispatchDriver::COleDispatchDriver](#coledispatchdriver)|Konstruuje `COleDispatchDriver` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDispatchDriver::AttachDispatch](#attachdispatch)|Dołącza `IDispatch` połączenie z `COleDispatchDriver` obiektem.|
|[COleDispatchDriver::CreateDispatch](#createdispatch)|Tworzy `IDispatch` połączenie i dołącza je `COleDispatchDriver` do obiektu.|
|[COleDispatchDriver::DetachDispatch](#detachdispatch)|Odłącza `IDispatch` połączenie, nie zwalniając go.|
|[COleDispatchDriver::GetProperty](#getproperty)|Pobiera właściwości automatyzacji.|
|[COleDispatchDriver::InvokeHelper](#invokehelper)|Pomocnik do wywoływania metod automatyzacji.|
|[COleDispatchDriver::ReleaseDispatch](#releasedispatch)|Zwalnia `IDispatch` połączenie.|
|[COleDispatchDriver::SetProperty](#setproperty)|Ustawia właściwość automatyzacji.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDispatchDriver::operator =](#operator_eq)|Kopiuje wartość źródłową `COleDispatchDriver` do obiektu.|
|[COleDispatchDriver::operator LPDISPATCH](#operator_lpdispatch)|Uzyskuje dostęp `IDispatch` do wskaźnika źródłowego.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleDispatchDriver::m_bAutoRelease](#m_bautorelease)|Określa, czy podczas `IDispatch` `ReleaseDispatch` lub zniszczenia obiektu.|
|[COleDispatchDriver::m_lpDispatch](#m_lpdispatch)|Wskazuje wskaźnik do `IDispatch` interfejsu dołączonego `COleDispatchDriver`do tego .|

## <a name="remarks"></a>Uwagi

`COleDispatchDriver`nie ma klasy podstawowej.

Interfejsy wysyłania OLE zapewniają dostęp do metod i właściwości obiektu. Funkcje `COleDispatchDriver` członkowskie dołączania, odłączania, tworzenia i `IDispatch`zwalniania połączenia wysyłkowego typu . Inne funkcje członkowskie używają list `IDispatch::Invoke`argumentów zmiennych, aby uprościć wywoływanie .

Ta klasa może być używana bezpośrednio, ale jest zwykle używana tylko przez klasy utworzone przez Kreatora dodawania klasy. Podczas tworzenia nowych klas C++ przez importowanie biblioteki typów, `COleDispatchDriver`nowe klasy są uzyskiwane z .

Aby uzyskać więcej `COleDispatchDriver`informacji na temat korzystania z programu , zobacz następujące artykuły:

- [Klienci automatyzacji](../../mfc/automation-clients.md)

- [Serwery automatyzacji](../../mfc/automation-servers.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`COleDispatchDriver`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="coledispatchdriverattachdispatch"></a><a name="attachdispatch"></a>COleDispatchDriver::AttachDispatch

Wywołanie `AttachDispatch` funkcji elementu `IDispatch` członkowskiego, `COleDispatchDriver` aby dołączyć wskaźnik do obiektu. Aby uzyskać więcej informacji, zobacz [Implementowanie interfejsu IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

```cpp
void AttachDispatch(
    LPDISPATCH lpDispatch,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>Parametry

*lpDispatch (Niedysp.*<br/>
Wskaźnik do `IDispatch` obiektu OLE, który `COleDispatchDriver` ma być dołączony do obiektu.

*bAutoRelease*<br/>
Określa, czy wysyłka ma zostać zwolniona, gdy ten obiekt wykracza poza zakres.

### <a name="remarks"></a>Uwagi

Ta funkcja `IDispatch` zwalnia dowolny wskaźnik, który `COleDispatchDriver` jest już dołączony do obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#3](../../mfc/codesnippet/cpp/coledispatchdriver-class_1.cpp)]

## <a name="coledispatchdrivercoledispatchdriver"></a><a name="coledispatchdriver"></a>COleDispatchDriver::COleDispatchDriver

Konstruuje `COleDispatchDriver` obiekt.

```
COleDispatchDriver();
COleDispatchDriver(LPDISPATCH lpDispatch, BOOL bAutoRelease = TRUE);
COleDispatchDriver(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>Parametry

*lpDispatch (Niedysp.*<br/>
Wskaźnik do `IDispatch` obiektu OLE, który `COleDispatchDriver` ma być dołączony do obiektu.

*bAutoRelease*<br/>
Określa, czy wysyłka ma zostać zwolniona, gdy ten obiekt wykracza poza zakres.

*wysyłkaSrc*<br/>
Odwołanie do `COleDispatchDriver` istniejącego obiektu.

### <a name="remarks"></a>Uwagi

Formularz `COleDispatchDriver`( `LPDISPATCH lpDispatch`, **BOOL**`bAutoRelease` = **TRUE**) łączy interfejs [IDispatch.](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)

Formularz `COleDispatchDriver` **(const)**`COleDispatchDriver`& `dispatchSrc`kopiuje `COleDispatchDriver` istniejący obiekt i zwiększa liczbę odwołań.

Formularz `COleDispatchDriver`( ) `COleDispatchDriver` tworzy obiekt, ale `IDispatch` nie łączy interfejsu. Przed `COleDispatchDriver`użyciem ( ) bez `IDispatch` argumentów należy połączyć się z nim za pomocą [COleDispatchDriver::CreateDispatch](#createdispatch) lub [COleDispatchDriver::AttachDispatch](#attachdispatch). Aby uzyskać więcej informacji, zobacz [Implementowanie interfejsu IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

### <a name="example"></a>Przykład

  Zobacz przykład [COleDispatchDriver::CreateDispatch](#createdispatch).

## <a name="coledispatchdrivercreatedispatch"></a><a name="createdispatch"></a>COleDispatchDriver::CreateDispatch

Tworzy obiekt interfejsu [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) i dołącza `COleDispatchDriver` go do obiektu.

```
BOOL CreateDispatch(
    REFCLSID clsid,
    COleException* pError = NULL);

BOOL CreateDispatch(
    LPCTSTR lpszProgID,
    COleException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*Clsid*<br/>
Identyfikator klasy obiektu `IDispatch` połączenia, który ma zostać utworzony.

*Perror*<br/>
Wskaźnik do obiektu wyjątku OLE, który będzie przechowywać kod stanu wynikający z utworzenia.

*lpszProgID*<br/>
Wskaźnik do identyfikatora programowego, takiego jak "Excel.Document.5", obiektu automatyzacji, dla którego ma zostać utworzony obiekt wysyłki.

### <a name="return-value"></a>Wartość zwracana

Nonzero na sukces; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#4](../../mfc/codesnippet/cpp/coledispatchdriver-class_2.cpp)]

## <a name="coledispatchdriverdetachdispatch"></a><a name="detachdispatch"></a>COleDispatchDriver::DetachDispatch

Odłącza bieżące `IDispatch` połączenie od tego obiektu.

```
LPDISPATCH DetachDispatch();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do wcześniej dołączonego `IDispatch` obiektu OLE.

### <a name="remarks"></a>Uwagi

Nie `IDispatch` jest zwolniony.

Aby uzyskać więcej informacji na temat typu LPDISPATCH, zobacz [Implementowanie interfejsu IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) w usłudze Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#5](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]

## <a name="coledispatchdrivergetproperty"></a><a name="getproperty"></a>COleDispatchDriver::GetProperty

Pobiera właściwość obiektu określoną przez *dwDispID*.

```cpp
void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Identyfikuje właściwość do pobrania.

*vtProp (vtProp)*<br/>
Określa właściwość, która ma zostać pobrana. Aby uzyskać możliwe wartości, zobacz sekcję Uwagi dla [COleDispatchDriver::InvokeHelper](#invokehelper).

*pvProp*<br/>
Adres zmiennej, która otrzyma wartość właściwości. Musi być zgodny z typem określonym przez *vtProp*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#6](../../mfc/codesnippet/cpp/coledispatchdriver-class_4.cpp)]

## <a name="coledispatchdriverinvokehelper"></a><a name="invokehelper"></a>COleDispatchDriver::InvokeHelper

Wywołuje metodę obiektu lub właściwość określoną przez *dwDispID*, w kontekście określonym przez *wFlags*.

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
Flagi opisujące kontekst wywołania `IDispatch::Invoke`. . Aby uzyskać listę możliwych wartości, zobacz parametr *wFlags* w [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) w zestawie Windows SDK.

*vtRet ( vtret )*<br/>
Określa typ zwracanej wartości. Aby uzyskać możliwe wartości, zobacz uwagi sekcji.

*pvRet*<br/>
Adres zmiennej, która otrzyma wartość właściwości lub wartość zwracaną. Musi być zgodny z typem określonym przez *vtRet*.

*pbParamInfo*<br/>
Wskaźnik do ciągu bajtów zakończonych z wartością null określających typy parametrów następujących po *pbParamInfo*.

*...*<br/>
Lista zmiennych parametrów, typów określonych w *pbParamInfo*.

### <a name="remarks"></a>Uwagi

Parametr *pbParamInfo* określa typy parametrów przekazanych do metody lub właściwości. Lista argumentów zmiennych jest reprezentowana przez **...** w deklaracji składni.

Możliwe wartości dla *vtRet* argument są pobierane z wyliczenia VARENUM. Dopuszczalne są następujące wartości:

|Symbol|Typ zwracany|
|------------|-----------------|
|Vt_empty|**void**|
|VT_I2|**short**|
|VT_I4|**długi**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|**CY**|
|VT_DATE|**Data**|
|Vt_bstr|Bstr|
|VT_DISPATCH|LPDISPATCH ( LPDISPATCH )|
|VT_ERROR|SCODE|
|VT_BOOL|**Bool**|
|VT_VARIANT|**VARIANT**|
|VT_UNKNOWN|LPUNKNOWN|

Argument *pbParamInfo* jest oddzieloną spacją **listą VTS_** stałych. Jedna lub więcej z tych wartości, oddzielonych spacjami (nie przecinkami), określa listę parametrów funkcji. Możliwe wartości są wyświetlane z [EVENT_CUSTOM](event-maps.md#event_custom) makrą.

Ta funkcja konwertuje parametry na wartości VARIANTARG, a następnie wywołuje [metodę IDispatch::Invoke.](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) Jeśli wywołanie `Invoke` nie powiedzie się, ta funkcja zda wyjątek. Jeśli SCODE (kod stanu) `IDispatch::Invoke` zwrócony przez jest DISP_E_EXCEPTION, ta funkcja zgłasza [COleException](../../mfc/reference/coleexception-class.md) obiektu; w przeciwnym razie rzuca [COleDispatchException](../../mfc/reference/coledispatchexception-class.md).

Aby uzyskać więcej informacji, zobacz [VARIANTARG](/windows/win32/api/oaidl/ns-oaidl-variant), [Implementowanie interfejsu IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface), [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)i [struktury kodów błędów COM](/windows/win32/com/structure-of-com-error-codes) w usłudze Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [COleDispatchDriver::CreateDispatch](#createdispatch).

## <a name="coledispatchdriverm_bautorelease"></a><a name="m_bautorelease"></a>COleDispatchDriver::m_bAutoRelease

Jeśli TRUE, obiekt COM, do który m_lpDispatch uzyskuje dostęp [m_lpDispatch,](#m_lpdispatch) zostanie automatycznie zwolniony `COleDispatchDriver` po [wywołaniu ReleaseDispatch](#releasedispatch) lub po zniszczeniu tego obiektu.

```
BOOL m_bAutoRelease;
```

### <a name="remarks"></a>Uwagi

Domyślnie `m_bAutoRelease` jest ustawiona na WARTOŚĆ PRAWDA w konstruktorze.

Aby uzyskać więcej informacji na temat zwalniania obiektów COM, zobacz [Implementowanie zliczania odwołań](/windows/win32/com/implementing-reference-counting) i [IUnknown::Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#9](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]

## <a name="coledispatchdriverm_lpdispatch"></a><a name="m_lpdispatch"></a>COleDispatchDriver::m_lpDispatch

Wskaźnik do `IDispatch` interfejsu dołączonego `COleDispatchDriver`do tego .

```
LPDISPATCH m_lpDispatch;
```

### <a name="remarks"></a>Uwagi

Element `m_lpDispatch` członkowski danych jest zmienną publiczną typu LPDISPATCH.

Aby uzyskać więcej informacji, zobacz [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) w usłudze Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [COleDispatchDriver::AttachDispatch](#attachdispatch).

## <a name="coledispatchdriveroperator-"></a><a name="operator_eq"></a>COleDispatchDriver::operator =

Kopiuje wartość źródłową `COleDispatchDriver` do obiektu.

```
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>Parametry

*wysyłkaSrc*<br/>
Wskaźnik do istniejącego `COleDispatchDriver` obiektu.

## <a name="coledispatchdriveroperator-lpdispatch"></a><a name="operator_lpdispatch"></a>COleDispatchDriver::operator LPDISPATCH

Uzyskuje dostęp `IDispatch` do wskaźnika bazowego `COleDispatchDriver` obiektu.

```
operator LPDISPATCH();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#8](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]

## <a name="coledispatchdriverreleasedispatch"></a><a name="releasedispatch"></a>COleDispatchDriver::ReleaseDispatch

Zwalnia `IDispatch` połączenie. Aby uzyskać więcej informacji, zobacz [Implementowanie interfejsu IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)

```cpp
void ReleaseDispatch();
```

### <a name="remarks"></a>Uwagi

Jeśli dla tego połączenia ustawiono automatyczne `IDispatch::Release` zwolnienie, ta funkcja wywołuje przed zwolnieniem interfejsu.

### <a name="example"></a>Przykład

  Zobacz przykład [COleDispatchDriver::AttachDispatch](#attachdispatch).

## <a name="coledispatchdriversetproperty"></a><a name="setproperty"></a>COleDispatchDriver::SetProperty

Ustawia właściwość obiektu OLE określoną przez *dwDispID*.

```cpp
void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>Parametry

*dwDispID*<br/>
Identyfikuje właściwość, która ma zostać ustawiona.

*vtProp (vtProp)*<br/>
Określa typ właściwości, która ma zostać ustawiona. Aby uzyskać możliwe wartości, zobacz sekcję Uwagi dla [COleDispatchDriver::InvokeHelper](#invokehelper).

*...*<br/>
Pojedynczy parametr typu określonego przez *vtProp*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#7](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]

## <a name="see-also"></a>Zobacz też

[Próbka MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[Próbka MFC ACDUAL](../../overview/visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)
