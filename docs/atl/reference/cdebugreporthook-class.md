---
title: Klasa CDebugReportHook
ms.date: 11/04/2016
f1_keywords:
- CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHookProc
- ATLUTIL/ATL::CDebugReportHook::RemoveHook
- ATLUTIL/ATL::CDebugReportHook::SetHook
- ATLUTIL/ATL::CDebugReportHook::SetPipeName
- ATLUTIL/ATL::CDebugReportHook::SetTimeout
helpviewer_keywords:
- CDebugReportHook class
ms.assetid: 798076c3-6e63-4286-83b8-aa1bbcd0c20c
ms.openlocfilehash: 7187448b2ba2c9d3ab0399aa3e75ce8d757bfec1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496772"
---
# <a name="cdebugreporthook-class"></a>Klasa CDebugReportHook

Użyj tej klasy, aby wysyłać raporty debugowania do nazwanego potoku.

## <a name="syntax"></a>Składnia

```
class CDebugReportHook
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHook](#cdebugreporthook)|Wywołuje [](#setpipename)metody setpipename, setTimeout i [sethook](#sethook). [](#settimeout)|
|[CDebugReportHook:: ~ CDebugReportHook](#dtor)|Wywołuje [CDebugReportHook:: RemoveHook](#removehook).|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHookProc](#cdebugreporthookproc)|Ruchom Funkcja raportowania niestandardowego, która jest dołączana do procesu raportowania debugowania w czasie wykonywania C.|
|[CDebugReportHook::RemoveHook](#removehook)|Wywołaj tę metodę, aby zatrzymać wysyłanie raportów debugowania do nazwanego potoku i przywrócić poprzedni punkt zaczepienia raportu.|
|[CDebugReportHook::SetHook](#sethook)|Wywołaj tę metodę, aby rozpocząć wysyłanie raportów debugowania do nazwanego potoku.|
|[CDebugReportHook:: setpipename](#setpipename)|Wywołaj tę metodę, aby ustawić maszynę i nazwę potoku, do którego będą wysyłane raporty debugowania.|
|[CDebugReportHook::SetTimeout](#settimeout)|Wywołaj tę metodę, aby ustawić czas w milisekundach, przez jaki ta klasa będzie oczekiwać na udostępnienie nazwanego potoku.|

## <a name="remarks"></a>Uwagi

Utwórz wystąpienie tej klasy w debugowanych kompilacjach usług lub aplikacji do wysyłania raportów debugowania do nazwanego potoku. Raporty debugowania są generowane przez wywołanie [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) lub użycie otoki dla tej funkcji, takiej jak makra [ATLTRACE](debugging-and-error-reporting-macros.md#atltrace) i [ATLASSERT](debugging-and-error-reporting-macros.md#atlassert) .

Użycie tej klasy pozwala interaktywnie debugować składniki działające w nieinteraktywnych [stacjach okna](/windows/win32/winstation/window-stations).

Należy pamiętać, że raporty debugowania są wysyłane przy użyciu podstawowego kontekstu zabezpieczeń wątku. Personifikacja jest tymczasowo wyłączona, aby raporty debugowania mogły być wyświetlane w sytuacjach, w których odbywa się personifikacja użytkowników z niskimi uprawnieniami, takich jak aplikacje sieci Web.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil. h

##  <a name="cdebugreporthook"></a>CDebugReportHook::CDebugReportHook

Wywołuje [](#setpipename)metody setpipename, setTimeout i [sethook](#sethook). [](#settimeout)

```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```

### <a name="parameters"></a>Parametry

*szMachineName*<br/>
Nazwa komputera, do którego powinny zostać wysłane dane wyjściowe debugowania. Domyślnie jest to komputer lokalny.

*szPipeName*<br/>
Nazwa potoku, do którego powinny zostać wysłane dane wyjściowe debugowania.

*dwTimeout*<br/>
Czas (w milisekundach), jaki ta klasa będzie oczekiwać na udostępnienie nazwanego potoku.

##  <a name="dtor"></a>CDebugReportHook:: ~ CDebugReportHook

Wywołuje [CDebugReportHook:: RemoveHook](#removehook).

```
~CDebugReportHook() throw();
```

##  <a name="cdebugreporthookproc"></a>CDebugReportHook::CDebugReportHookProc

Funkcja raportowania niestandardowego, która jest dołączana do procesu raportowania debugowania w czasie wykonywania C.

```
static int __cdecl CDebugReportHookProc(
    int reportType,
    char* message,
    int* returnValue) throw();
```

### <a name="parameters"></a>Parametry

*reportType*<br/>
Typ raportu (_CRT_WARN, _CRT_ERROR lub _CRT_ASSERT).

*komunikat*<br/>
Ciąg komunikatu.

*returnValue*<br/>
Wartość, która powinna zostać zwrócona przez [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość FALSE, jeśli punkt zaczepienia obsługuje komunikat w całości, dzięki czemu nie jest wymagane dalsze raportowanie. Zwraca wartość true `_CrtDbgReport` , jeśli komunikat powinien być raportowany w normalny sposób.

### <a name="remarks"></a>Uwagi

Funkcja raportowania próbuje otworzyć nazwany potok i komunikować się z procesem na drugim końcu. Jeśli potok jest zajęty, funkcja raportowania będzie czekać, aż potok zostanie zwolniony, lub limit czasu wygaśnie. Limit czasu może być ustawiony przez konstruktora lub wywołanie [CDebugReportHook:: setTimeout](#settimeout).

Kod w tej funkcji jest wykonywany w podstawowym kontekście zabezpieczeń wątku wywołującego, czyli Personifikacja jest wyłączona przez czas trwania tej funkcji.

##  <a name="removehook"></a>CDebugReportHook::RemoveHook

Wywołaj tę metodę, aby zatrzymać wysyłanie raportów debugowania do nazwanego potoku i przywrócić poprzedni punkt zaczepienia raportu.

```
void RemoveHook() throw();
```

### <a name="remarks"></a>Uwagi

Wywołuje [_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) , aby przywrócić poprzedni hak raportu.

##  <a name="sethook"></a>CDebugReportHook:: sethook

Wywołaj tę metodę, aby rozpocząć wysyłanie raportów debugowania do nazwanego potoku.

```
void SetHook() throw();
```

### <a name="remarks"></a>Uwagi

Wywołuje [_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) , aby raporty debugowania były kierowane przez [CDebugReportHookProc](#cdebugreporthookproc) do nazwanego potoku. Ta klasa śledzi poprzedni punkt zaczepienia raportu, aby można go było przywrócić po wywołaniu [RemoveHook](#removehook) .

##  <a name="setpipename"></a>CDebugReportHook:: setpipename

Wywołaj tę metodę, aby ustawić maszynę i nazwę potoku, do którego będą wysyłane raporty debugowania.

```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```

### <a name="parameters"></a>Parametry

*szMachineName*<br/>
Nazwa komputera, do którego powinny zostać wysłane dane wyjściowe debugowania.

*szPipeName*<br/>
Nazwa potoku, do którego powinny zostać wysłane dane wyjściowe debugowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

##  <a name="settimeout"></a>CDebugReportHook:: setTimeout

Wywołaj tę metodę, aby ustawić czas w milisekundach, przez jaki ta klasa będzie oczekiwać na udostępnienie nazwanego potoku.

```
void SetTimeout(DWORD dwTimeout);
```

### <a name="parameters"></a>Parametry

*dwTimeout*<br/>
Czas (w milisekundach), jaki ta klasa będzie oczekiwać na udostępnienie nazwanego potoku.

## <a name="see-also"></a>Zobacz także

[Klasy](../../atl/reference/atl-classes.md)
