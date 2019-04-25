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
ms.openlocfilehash: a7c5993d1b96daaa73e7fc9509c93e66daed77f3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245930"
---
# <a name="cdebugreporthook-class"></a>Klasa CDebugReportHook

Klasa jest używana do wysyłania raportów debugowania z nazwanym potokiem.

## <a name="syntax"></a>Składnia

```
class CDebugReportHook
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHook](#cdebugreporthook)|Wywołania [SetPipeName](#setpipename), [SetTimeout](#settimeout), i [SetHook](#sethook).|
|[CDebugReportHook::~CDebugReportHook](#dtor)|Wywołania [CDebugReportHook::RemoveHook](#removehook).|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHookProc](#cdebugreporthookproc)|(Statyczny) Funkcja raportowania niestandardowa jest podłączone do środowiska wykonawczego języka C debugować proces raportowania.|
|[CDebugReportHook::RemoveHook](#removehook)|Wywołanie tej metody, aby zatrzymać wysyłanie raportów debugowania do nazwanego potoku i przywrócić poprzednich punktów zaczepienia raportu.|
|[CDebugReportHook::SetHook](#sethook)|Wywołaj tę metodę, aby rozpocząć wysyłanie raportów debugowania do nazwanego potoku.|
|[CDebugReportHook::SetPipeName](#setpipename)|Wywołaj tę metodę, aby ustawić komputera i Nazwa potoku, do którego będą wysyłane raporty debugowania.|
|[CDebugReportHook::SetTimeout](#settimeout)|Wywołaj tę metodę, aby ustawić czas w milisekundach, że ta klasa będzie czekać nazwany potok staną się dostępne.|

## <a name="remarks"></a>Uwagi

Utwórz wystąpienie tej klasy w kompilacjach debugowania, usługi lub aplikacji na wysyłanie raportów debugowania do nazwanego potoku. Debugowanie raporty są generowane przez wywołanie metody [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) lub użyć otokę dla tej funkcji, takich jak [ATLTRACE](debugging-and-error-reporting-macros.md#atltrace) i [ATLASSERT](debugging-and-error-reporting-macros.md#atlassert) makra.

Użyj tej klasy umożliwia interakcyjnie debugować składników działających w trybie nieinteraktywnym [stacji okna](/windows/desktop/winstation/window-stations).

Należy zwrócić uwagę na to, czy raporty debugowania są wysyłane przy użyciu podstawowych kontekstu zabezpieczeń w wątku. Personifikacja jest tymczasowo wyłączona, aby raporty debugowania mogą być wyświetlane w sytuacjach, w którym z obniżonymi uprawnieniami użytkowników jest personifikacja, takie jak w aplikacjach sieci web.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil.h

##  <a name="cdebugreporthook"></a>  CDebugReportHook::CDebugReportHook

Wywołania [SetPipeName](#setpipename), [SetTimeout](#settimeout), i [SetHook](#sethook).

```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```

### <a name="parameters"></a>Parametry

*szMachineName*<br/>
Nazwa maszyny, do którego mają być wysyłane dane wyjściowe debugowania. Wartość domyślna to komputer lokalny.

*szPipeName*<br/>
Nazwa nazwanego potoku, do którego mają być wysyłane dane wyjściowe debugowania.

*dwTimeout*<br/>
Czas w milisekundach, że ta klasa będzie czekać nazwany potok staną się dostępne.

##  <a name="dtor"></a>  CDebugReportHook:: ~ CDebugReportHook

Wywołania [CDebugReportHook::RemoveHook](#removehook).

```
~CDebugReportHook() throw();
```

##  <a name="cdebugreporthookproc"></a>  CDebugReportHook::CDebugReportHookProc

Funkcja raportowania niestandardowa jest podłączone do środowiska wykonawczego języka C debugować proces raportowania.

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
Wartość, która ma zostać zwrócony przez [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość FALSE, jeśli punkt zaczepienia obsługi wiadomości w danym całkowicie dzięki czemu nie dalsze raportowania są wymagane. Zwraca wartość PRAWDA, jeśli `_CrtDbgReport` należy zgłaszać komunikat w normalny sposób.

### <a name="remarks"></a>Uwagi

Funkcja raportowania próbuje otworzyć nazwanego potoku i komunikacji z procesem na drugim końcu. Jeśli potok jest zajęty, funkcja raportowania będzie czekał potoku jest bezpłatna lub upłynie limit czasu. Można ustawić limitu czasu przez konstruktora lub wywołanie [CDebugReportHook::SetTimeout](#settimeout).

Kod w tej funkcji jest wykonywany w kontekście zabezpieczeń podstawowy wątek wywołujący, oznacza to, personifikacja jest wyłączone na czas trwania tej funkcji.

##  <a name="removehook"></a>  CDebugReportHook::RemoveHook

Wywołanie tej metody, aby zatrzymać wysyłanie raportów debugowania do nazwanego potoku i przywrócić poprzednich punktów zaczepienia raportu.

```
void RemoveHook() throw();
```

### <a name="remarks"></a>Uwagi

Wywołania [_crtsetreporthook2 —](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) można przywrócić poprzedniego punktu zaczepienia raportu.

##  <a name="sethook"></a>  CDebugReportHook::SetHook

Wywołaj tę metodę, aby rozpocząć wysyłanie raportów debugowania do nazwanego potoku.

```
void SetHook() throw();
```

### <a name="remarks"></a>Uwagi

Wywołania [_crtsetreporthook2 —](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) do raportów debugowania kierowane za pośrednictwem [CDebugReportHookProc](#cdebugreporthookproc) do nazwanego potoku. Ta klasa śledzi informacje o poprzednich punktów zaczepienia raportu tak, aby można go przywrócić, kiedy [RemoveHook](#removehook) jest wywoływana.

##  <a name="setpipename"></a>  CDebugReportHook::SetPipeName

Wywołaj tę metodę, aby ustawić komputera i Nazwa potoku, do którego będą wysyłane raporty debugowania.

```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```

### <a name="parameters"></a>Parametry

*szMachineName*<br/>
Nazwa maszyny, do którego mają być wysyłane dane wyjściowe debugowania.

*szPipeName*<br/>
Nazwa nazwanego potoku, do którego mają być wysyłane dane wyjściowe debugowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

##  <a name="settimeout"></a>  CDebugReportHook::SetTimeout

Wywołaj tę metodę, aby ustawić czas w milisekundach, że ta klasa będzie czekać nazwany potok staną się dostępne.

```
void SetTimeout(DWORD dwTimeout);
```

### <a name="parameters"></a>Parametry

*dwTimeout*<br/>
Czas w milisekundach, że ta klasa będzie czekać nazwany potok staną się dostępne.

## <a name="see-also"></a>Zobacz także

[Klasy](../../atl/reference/atl-classes.md)
