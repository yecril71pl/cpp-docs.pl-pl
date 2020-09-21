---
title: Funkcje globalne debugowania i raportowania błędów
ms.date: 11/04/2016
f1_keywords:
- atlcomcli/ATL::AtlHresultFromLastError
- atlcom/ATL::AtlReportError
- atldef/ATL::AtlThrow
helpviewer_keywords:
- functions [ATL], error reporting
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
ms.openlocfilehash: 10aca6862f6989c126981a9f6437c61f1c07bdae
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742791"
---
# <a name="debugging-and-error-reporting-global-functions"></a>Funkcje globalne debugowania i raportowania błędów

Funkcje te umożliwiają przydatną funkcję debugowania i śledzenia.

|Nazwa|Opis|
|-|-|
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|Zwraca `GetLastError` Kod błędu w postaci HRESULT.|
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|Konwertuje kod błędu Win32 na HRESULT.|
|[AtlReportError](debugging-and-error-reporting-global-functions.md#atlreporterror)|Konfiguruje `IErrorInfo` , aby zapewnić klientom szczegółowe informacje o błędach.|
|[Funkcji AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|Zgłasza `CAtlException` .|
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|Wywołaj tę funkcję, aby sygnalizować błąd na podstawie wyniku funkcji systemu Windows `GetLastError` .|

## <a name="atlhresultfromlasterror"></a><a name="atlhresultfromlasterror"></a> AtlHresultFromLastError

Zwraca wartość kodu ostatniego błędu wywołującego wątku w formie HRESULT.

```
HRESULT AtlHresultFromLastError();
```

### <a name="remarks"></a>Uwagi

`AtlHresultFromLastError` wywołania `GetLastError` w celu uzyskania ostatniego błędu i zwracają błąd po konwersji na wynik HRESULT przy użyciu makra HRESULT_FROM_WIN32.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlcomcli. h

## <a name="atlhresultfromwin32"></a><a name="atlhresultfromwin32"></a> AtlHresultFromWin32

Konwertuje kod błędu Win32 na HRESULT.

```
AtlHresultFromWin32(DWORD error);
```

### <a name="parameters"></a>Parametry

*Porn*<br/>
Wartość błędu do przekonwertowania.

### <a name="remarks"></a>Uwagi

Konwertuje kod błędu Win32 na HRESULT przy użyciu makra HRESULT_FROM_WIN32.

> [!NOTE]
> Zamiast korzystać z programu `HRESULT_FROM_WIN32(GetLastError())` , należy użyć funkcji [AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlcomcli. h

## <a name="atlreporterror"></a><a name="atlreporterror"></a> AtlReportError

Konfiguruje `IErrorInfo` interfejs, aby dostarczyć informacje o błędzie do klientów obiektu.

```
HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCOLESTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCOLESTR lpszDesc,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCSTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCSTR lpszDesc,
    DWORD dwHelpID,
    LPCSTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    UINT nID,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    UINT nID,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
podczas Identyfikator CLSID obiektu zgłaszającego błąd.

*lpszDesc*<br/>
podczas Ciąg opisujący błąd. Wersje Unicode określają, że *lpszDesc* jest typu LPCOLESTR; Wersja ANSI określa typ LPCSTR.

*IID*<br/>
podczas Identyfikator IID interfejsu definiujący błąd lub GUID_NULL, jeśli błąd jest zdefiniowany przez system operacyjny.

*hRes*<br/>
podczas Wartość HRESULT, która ma zostać zwrócona do obiektu wywołującego.

*nID*<br/>
podczas Identyfikator zasobu, w którym jest przechowywany ciąg opisu błędu. Ta wartość powinna należeć do przedziału od 0x0200 do 0xFFFF włącznie. W kompilacjach debugowania wynikiem **będzie wynik** , jeśli *NID* nie indeksuje poprawnego ciągu. W kompilacjach wydania ciąg opisu błędu zostanie ustawiony na "nieznany błąd".

*dwHelpID*<br/>
podczas Identyfikator kontekstu pomocy dla błędu.

*lpszHelpFile*<br/>
podczas Ścieżka i nazwa pliku pomocy opisującego błąd.

*hInst*<br/>
podczas Dojście do zasobu. Domyślnie ten parametr to `__AtlBaseModuleModule::GetResourceInstance` , gdzie `__AtlBaseModuleModule` jest globalnym wystąpieniem [CAtlBaseModule](../../atl/reference/catlbasemodule-class.md) lub klasy pochodnej.

### <a name="return-value"></a>Wartość zwracana

Jeśli parametr *hRes* jest różny od zera, zwraca wartość *hRes*. Jeśli *hRes* ma wartość zero, wówczas pierwsze cztery wersje `AtlReportError` zwracanych DISP_E_EXCEPTION. Ostatnie dwie wersje zwracają wynik **MAKE_HRESULT makro (1, FACILITY_ITF,** `nID` **)**.

### <a name="remarks"></a>Uwagi

Ciąg *lpszDesc* jest używany jako opis tekstowy błędu. Gdy klient odbierze *hRes* z `AtlReportError` , klient może uzyskać dostęp do `IErrorInfo` struktury w celu uzyskania szczegółowych informacji o błędzie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]

> [!CAUTION]
> Nie należy używać `AtlReportError` w obsłudze catch języka C++. W przypadku niektórych zastąpień tych funkcji są używane wewnętrznie makra konwersji ciągów ATL, które z kolei używają `_alloca` funkcji wewnętrznie. Korzystanie `AtlReportError` z programu w obsłudze catch języka c++ może spowodować wyjątki w obsłudze catch języka c++.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

## <a name="atlthrow"></a><a name="atlthrow"></a> Funkcji AtlThrow

Wywołaj tę funkcję, aby sygnalizować błąd na podstawie kodu stanu HRESULT.

```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```

### <a name="parameters"></a>Parametry

*godz.*<br/>
Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ta funkcja jest używana przez kod ATL i MFC w przypadku warunku błędu. Może być również wywoływana z własnego kodu. Domyślna implementacja tej funkcji zależy od definicji symbolu _ATL_NO_EXCEPTIONS i typu projektu, MFC lub ATL.

We wszystkich przypadkach ta funkcja śledzi wynik HRESULT do debugera.

W programie Visual Studio 2015 Update 3 i nowszych funkcja ta ma atrybut __declspec (noreturn), aby uniknąć ostrzeżeń fałszywe SAL.

Jeśli _ATL_NO_EXCEPTIONS nie jest zdefiniowana w projekcie MFC, ta funkcja zgłasza [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md) na podstawie wartości HRESULT.

Jeśli _ATL_NO_EXCEPTIONS nie jest zdefiniowana w projekcie ATL, funkcja zgłasza [CAtlException](../../atl/reference/catlexception-class.md).

Jeśli _ATL_NO_EXCEPTIONS jest zdefiniowany, funkcja powoduje błąd potwierdzenia, zamiast zgłaszać wyjątek.

W przypadku projektów ATL istnieje możliwość zapewnienia własnej implementacji tej funkcji, która ma być używana przez ATL w przypadku awarii. W tym celu należy zdefiniować własną funkcję o tej samej sygnaturze, co `AtlThrow` i #define jako `AtlThrow` nazwę funkcji. Należy to zrobić przed włączeniem atlexcept. h (co oznacza, że należy je wykonać przed dołączeniem wszelkich nagłówków ATL od atlbase. h obejmuje atlexcept. h). Poatrybucie funkcję `__declspec(noreturn)` , aby uniknąć fałszyweych ostrzeżeń sal.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** atldef. h

## <a name="atlthrowlastwin32"></a><a name="atlthrowlastwin32"></a> AtlThrowLastWin32

Wywołaj tę funkcję, aby sygnalizować błąd na podstawie wyniku funkcji systemu Windows `GetLastError` .

```
inline void AtlThrowLastWin32();
```

### <a name="remarks"></a>Uwagi

Ta funkcja śledzi wynik `GetLastError` debugera.

Jeśli _ATL_NO_EXCEPTIONS nie jest zdefiniowana w projekcie MFC, ta funkcja zgłasza [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md) na podstawie wartości zwracanej przez `GetLastError` .

Jeśli _ATL_NO_EXCEPTIONS nie jest zdefiniowana w projekcie ATL, funkcja zgłasza [CAtlException](../../atl/reference/catlexception-class.md).

Jeśli _ATL_NO_EXCEPTIONS jest zdefiniowany, funkcja powoduje błąd potwierdzenia, zamiast zgłaszać wyjątek.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atldef. h

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)<br/>
[Makra debugowania i raportowania błędów](../../atl/reference/debugging-and-error-reporting-macros.md)
