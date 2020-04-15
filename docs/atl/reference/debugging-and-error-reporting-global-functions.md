---
title: Debugowanie i raportowanie błędów funkcje globalne
ms.date: 11/04/2016
f1_keywords:
- atlcomcli/ATL::AtlHresultFromLastError
- atlcom/ATL::AtlReportError
- atldef/ATL::AtlThrow
helpviewer_keywords:
- functions [ATL], error reporting
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
ms.openlocfilehash: f7636b1f4e13340b223edd8c63c39bbeb21c8bd0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330205"
---
# <a name="debugging-and-error-reporting-global-functions"></a>Debugowanie i raportowanie błędów funkcje globalne

Te funkcje zapewniają przydatne debugowania i śledzenia obiektów.

|||
|-|-|
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|Zwraca `GetLastError` kod błędu w postaci HRESULT.|
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|Konwertuje kod błędu Win32 na HRESULT.|
|[AtlReportError ( AtlReportError )](debugging-and-error-reporting-global-functions.md#atlreporterror)|Konfiguruje, `IErrorInfo` aby podać szczegóły błędu do klienta.|
|[AtlThrow ( AtlThrow )](debugging-and-error-reporting-global-functions.md#atlthrow)|Rzuca . `CAtlException`|
|[AtlThrowLastWin32 (AtlThrowLastWin32)](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|Wywołanie tej funkcji, aby zasygnalizować `GetLastError`błąd na podstawie wyniku funkcji systemu Windows .|

## <a name="atlhresultfromlasterror"></a><a name="atlhresultfromlasterror"></a>AtlHresultFromLastError

Zwraca wartość kodu ostatniego błędu wywołującego wątku w formie HRESULT.

```
HRESULT AtlHresultFromLastError();
```

### <a name="remarks"></a>Uwagi

`AtlHresultFromLastError`wywołania, `GetLastError` aby uzyskać ostatni błąd i zwraca błąd po przekonwertowaniu go na HRESULT przy użyciu makra HRESULT_FROM_WIN32.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlcomcli.h

## <a name="atlhresultfromwin32"></a><a name="atlhresultfromwin32"></a>AtlHresultFromWin32

Konwertuje kod błędu Win32 na HRESULT.

```
AtlHresultFromWin32(DWORD error);
```

### <a name="parameters"></a>Parametry

*error*<br/>
Wartość błędu do konwersji.

### <a name="remarks"></a>Uwagi

Konwertuje kod błędu Win32 na HRESULT, używając HRESULT_FROM_WIN32 makra.

> [!NOTE]
> Zamiast używać `HRESULT_FROM_WIN32(GetLastError())`funkcji [AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlcomcli.h

## <a name="atlreporterror"></a><a name="atlreporterror"></a>AtlReportError ( AtlReportError )

Konfiguruje `IErrorInfo` interfejs, aby dostarczać informacje o błędzie klientom obiektu.

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

*Clsid*<br/>
[w] Identyfikator CLSID obiektu raportowania błędu.

*lpszDesc*<br/>
[w] Ciąg opisujący błąd. Wersje Unicode określają, że *lpszDesc* jest typu LPCOLESTR; wersja ANSI określa typ LPCSTR.

*Iid*<br/>
[w] Identyfikator interfejsu definiującego błąd lub GUID_NULL, jeśli błąd jest zdefiniowany przez system operacyjny.

*Hres*<br/>
[w] HRESULT, który ma powrócić do wywołującego.

*Nid*<br/>
[w] Identyfikator zasobu, w którym jest przechowywany ciąg opisu błędu. Wartość ta powinna należeć do 0x0200 i 0xFFFF, włącznie. W kompilacjach debugowania **assert** spowoduje, jeśli *nID* nie indeksuje prawidłowego ciągu. W kompilacjach wersji ciąg opisu błędu zostanie ustawiony na "Nieznany błąd".

*dwHelpID (Pomoc EKwi.*<br/>
[w] Identyfikator kontekstu pomocy dla błędu.

*lpszHelpFile*<br/>
[w] Ścieżka i nazwa pliku pomocy opisującego błąd.

*hInst (WZT)*<br/>
[w] Dojście do zasobu. Domyślnie ten parametr `__AtlBaseModuleModule::GetResourceInstance`jest `__AtlBaseModuleModule` , gdzie jest globalne [wystąpienie CAtlBaseModule](../../atl/reference/catlbasemodule-class.md) lub klasy pochodne od niego.

### <a name="return-value"></a>Wartość zwracana

Jeśli parametr *hRes* nie ma wartościzerowej, zwraca wartość *hRes*. Jeśli *hRes* wynosi zero, pierwsze `AtlReportError` cztery wersje zwracane DISP_E_EXCEPTION. Dwie ostatnie wersje zwracają wynik **MAKE_HRESULT makra( 1,** `nID` **FACILITY_ITF)**.

### <a name="remarks"></a>Uwagi

Ciąg *lpszDesc* jest używany jako opis tekstowy błędu. Gdy klient odbiera *hRes,* `AtlReportError`z którego zwracasz, klient może uzyskać dostęp do struktury, `IErrorInfo` aby uzyskać szczegółowe informacje o błędzie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]

> [!CAUTION]
> Nie należy `AtlReportError` używać w programie obsługi catch języka C++. Niektóre zastąpienia tych funkcji używają makr konwersji ciągu ATL wewnętrznie, `_alloca` które z kolei używają tej funkcji wewnętrznie. Za `AtlReportError` pomocą programu obsługi catch języka C++ może powodować wyjątki w programie obsługi catch języka C++.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="atlthrow"></a><a name="atlthrow"></a>AtlThrow ( AtlThrow )

Wywołanie tej funkcji, aby zasygnalizować błąd na podstawie kodu stanu HRESULT.

```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```

### <a name="parameters"></a>Parametry

*Hr*<br/>
Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ta funkcja jest używana przez kod ATL i MFC w przypadku wystąpienia błędu. Można go również wywołać z własnego kodu. Domyślna implementacja tej funkcji zależy od definicji symbolu _ATL_NO_EXCEPTIONS i od typu projektu, MFC lub ATL.

We wszystkich przypadkach ta funkcja śledzi HRESULT do debugera.

W programie Visual Studio 2015 Update 3 i nowsze, ta funkcja jest przypisywana __declspec(noreturn), aby uniknąć fałszywych ostrzeżeń SAL.

Jeśli _ATL_NO_EXCEPTIONS nie jest zdefiniowany w projekcie MFC, ta funkcja zgłasza [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md) na podstawie wartości HRESULT.

Jeśli _ATL_NO_EXCEPTIONS nie jest zdefiniowany w projekcie ATL, funkcja rzuca [CAtlException](../../atl/reference/catlexception-class.md).

Jeśli _ATL_NO_EXCEPTIONS jest zdefiniowany, funkcja powoduje błąd potwierdzenia zamiast zgłaszania wyjątku.

W przypadku projektów ATL można zapewnić własną implementację tej funkcji, która ma być używana przez ATL w przypadku awarii. Aby to zrobić, zdefiniuj `AtlThrow` własną funkcję z `AtlThrow` tym samym podpisem, a #define być nazwą funkcji. Należy to zrobić przed włączeniem atlexcept.h (co oznacza, że należy to zrobić przed włączeniem jakichkolwiek nagłówków ATL, ponieważ atlbase.h zawiera atlexcept.h). Przypisz swoją `__declspec(noreturn)` funkcję, aby uniknąć fałszywych ostrzeżeń SAL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldef.h

## <a name="atlthrowlastwin32"></a><a name="atlthrowlastwin32"></a>AtlThrowLastWin32 (AtlThrowLastWin32)

Wywołanie tej funkcji, aby zasygnalizować `GetLastError`błąd na podstawie wyniku funkcji systemu Windows .

```
inline void AtlThrowLastWin32();
```

### <a name="remarks"></a>Uwagi

Ta funkcja śledzi wynik `GetLastError` do debugera.

Jeśli _ATL_NO_EXCEPTIONS nie jest zdefiniowany w projekcie MFC, ta funkcja zgłasza [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md) na podstawie wartości zwróconej przez `GetLastError`.

Jeśli _ATL_NO_EXCEPTIONS nie jest zdefiniowany w projekcie ATL, funkcja rzuca [CAtlException](../../atl/reference/catlexception-class.md).

Jeśli _ATL_NO_EXCEPTIONS jest zdefiniowany, funkcja powoduje błąd potwierdzenia zamiast zgłaszania wyjątku.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldef.h

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)<br/>
[Debugowanie i raportowanie błędów makra](../../atl/reference/debugging-and-error-reporting-macros.md)
