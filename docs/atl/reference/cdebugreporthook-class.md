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
ms.openlocfilehash: 8380556bbe007326156bf0ec0eefc23052e8e056
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747718"
---
# <a name="cdebugreporthook-class"></a>Klasa CDebugReportHook

Ta klasa służy do wysyłania raportów debugowania do nazwanego potoku.

## <a name="syntax"></a>Składnia

```
class CDebugReportHook
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHook](#cdebugreporthook)|Wywołuje [SetPipeName](#setpipename), [SetTimeout](#settimeout)i [SetHook](#sethook).|
|[CDebugReportHook::~CDebugReportHook](#dtor)|Wywołuje [CDebugReportHook::RemoveHook](#removehook).|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHookProc](#cdebugreporthookproc)|(Statyczne) Funkcja raportowania niestandardowego, która jest podłączona do procesu raportowania debugowania w czasie wykonywania języka C.|
|[CDebugReportHook::Usuń Element](#removehook)|Wywołanie tej metody, aby zatrzymać wysyłanie raportów debugowania do nazwanego potoku i przywrócić poprzedni hak raportu.|
|[CDebugReportHook::SetHook](#sethook)|Wywołanie tej metody, aby rozpocząć wysyłanie raportów debugowania do nazwanego potoku.|
|[CDebugReportHook::SetPipeName](#setpipename)|Wywołanie tej metody, aby ustawić maszynę i nazwę potoku, do którego będą wysyłane raporty debugowania.|
|[CDebugReportHook::SetTimeout](#settimeout)|Wywołanie tej metody, aby ustawić czas w milisekundach, że ta klasa będzie czekać na nazwany potok staną się dostępne.|

## <a name="remarks"></a>Uwagi

Utwórz wystąpienie tej klasy w kompilacjach debugowania usług lub aplikacji do wysyłania raportów debugowania do nazwanego potoku. Raporty debugowania są generowane przez wywołanie [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) lub przy użyciu otoki dla tej funkcji, takiej jak makra [ATLTRACE](debugging-and-error-reporting-macros.md#atltrace) i [ATLASSERT.](debugging-and-error-reporting-macros.md#atlassert)

Użycie tej klasy umożliwia interaktywne debugowanie składników działających w nieinterakcyjnych [stacjach okiennych](/windows/win32/winstation/window-stations).

Należy zauważyć, że raporty debugowania są wysyłane przy użyciu kontekstu zabezpieczeń podstawowych wątku. Personifikacja jest tymczasowo wyłączona, dzięki czemu raporty debugowania mogą być wyświetlane w sytuacjach, w których ma miejsce personifikacja użytkowników o niskich uprawnieniach, na przykład w aplikacjach sieci web.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil.h

## <a name="cdebugreporthookcdebugreporthook"></a><a name="cdebugreporthook"></a>CDebugReportHook::CDebugReportHook

Wywołuje [SetPipeName](#setpipename), [SetTimeout](#settimeout)i [SetHook](#sethook).

```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```

### <a name="parameters"></a>Parametry

*szMachineName (Nazwa)*<br/>
Nazwa komputera, do którego należy wysłać dane wyjściowe debugowania. Domyślnie komputer lokalny.

*szPipeName (Nazwa)*<br/>
Nazwa nazwanego potoku, do którego należy wysłać dane wyjściowe debugowania.

*dwTimeout*<br/>
Czas w milisekundach, że ta klasa będzie czekać na nazwany potok, aby stać się dostępne.

## <a name="cdebugreporthookcdebugreporthook"></a><a name="dtor"></a>CDebugReportHook::~CDebugReportHook

Wywołuje [CDebugReportHook::RemoveHook](#removehook).

```
~CDebugReportHook() throw();
```

## <a name="cdebugreporthookcdebugreporthookproc"></a><a name="cdebugreporthookproc"></a>CDebugReportHook::CDebugReportHookProc

Funkcja raportowania niestandardowego, która jest podłączona do procesu raportowania debugowania w czasie wykonywania języka C.

```
static int __cdecl CDebugReportHookProc(
    int reportType,
    char* message,
    int* returnValue) throw();
```

### <a name="parameters"></a>Parametry

*Typ raportu*<br/>
Typ raportu (_CRT_WARN, _CRT_ERROR lub _CRT_ASSERT).

*Komunikat*<br/>
Ciąg wiadomości.

*Returnvalue*<br/>
Wartość, która powinna zostać zwrócona przez [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość FAŁSZ, jeśli hak obsługuje daną wiadomość całkowicie, dzięki czemu nie jest wymagane dalsze raportowanie. Zwraca wartość `_CrtDbgReport` PRAWDA, jeśli wiadomość powinna być zgłaszana w normalny sposób.

### <a name="remarks"></a>Uwagi

Funkcja raportowania próbuje otworzyć nazwany potok i komunikować się z procesem na drugim końcu. Jeśli potok jest zajęty, funkcja raportowania będzie czekać, aż potok jest wolny lub upłynie limit czasu. Limit czasu można ustawić przez konstruktora lub wywołanie [CDebugReportHook::SetTimeout](#settimeout).

Kod w tej funkcji jest wykonywany w podstawowym kontekście zabezpieczeń wątku wywołującego, czyli personifikacja jest wyłączona na czas trwania tej funkcji.

## <a name="cdebugreporthookremovehook"></a><a name="removehook"></a>CDebugReportHook::Usuń Element

Wywołanie tej metody, aby zatrzymać wysyłanie raportów debugowania do nazwanego potoku i przywrócić poprzedni hak raportu.

```cpp
void RemoveHook() throw();
```

### <a name="remarks"></a>Uwagi

Wywołuje [_CrtSetReportHook2,](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) aby przywrócić poprzedni hak raportu.

## <a name="cdebugreporthooksethook"></a><a name="sethook"></a>CDebugReportHook::SetHook

Wywołanie tej metody, aby rozpocząć wysyłanie raportów debugowania do nazwanego potoku.

```cpp
void SetHook() throw();
```

### <a name="remarks"></a>Uwagi

Wywołuje [_CrtSetReportHook2,](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) aby raporty debugowania kierowane za pośrednictwem [CDebugReportHookProc](#cdebugreporthookproc) do nazwanego potoku. Ta klasa śledzi poprzedni hak raportu, dzięki czemu można go przywrócić, gdy [removehook](#removehook) jest wywoływana.

## <a name="cdebugreporthooksetpipename"></a><a name="setpipename"></a>CDebugReportHook::SetPipeName

Wywołanie tej metody, aby ustawić maszynę i nazwę potoku, do którego będą wysyłane raporty debugowania.

```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```

### <a name="parameters"></a>Parametry

*szMachineName (Nazwa)*<br/>
Nazwa komputera, do którego należy wysłać dane wyjściowe debugowania.

*szPipeName (Nazwa)*<br/>
Nazwa nazwanego potoku, do którego należy wysłać dane wyjściowe debugowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

## <a name="cdebugreporthooksettimeout"></a><a name="settimeout"></a>CDebugReportHook::SetTimeout

Wywołanie tej metody, aby ustawić czas w milisekundach, że ta klasa będzie czekać na nazwany potok staną się dostępne.

```cpp
void SetTimeout(DWORD dwTimeout);
```

### <a name="parameters"></a>Parametry

*dwTimeout*<br/>
Czas w milisekundach, że ta klasa będzie czekać na nazwany potok, aby stać się dostępne.

## <a name="see-also"></a>Zobacz też

[Klasy](../../atl/reference/atl-classes.md)
