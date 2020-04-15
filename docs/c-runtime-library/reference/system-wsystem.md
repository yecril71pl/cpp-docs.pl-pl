---
title: system, _wsystem
ms.date: 4/2/2020
api_name:
- system
- _wsystem
- _o__wsystem
- _o_system
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tsystem
- _wsystem
helpviewer_keywords:
- _wsystem function
- wsystem function
- tsystem function
- _tsystem function
- system function
- commands, executing
- command interpreter
ms.assetid: 7d3df2b6-f742-49ce-bf52-012b0aee3df5
ms.openlocfilehash: 21ce04d30da80a40a1162dce06ff378150008766
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362788"
---
# <a name="system-_wsystem"></a>system, _wsystem

Wykonuje polecenie.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int system(
   const char *command
);
int _wsystem(
   const wchar_t *command
);
```

### <a name="parameters"></a>Parametry

*Polecenia*<br/>
Polecenie do wykonania.

## <a name="return-value"></a>Wartość zwracana

Jeśli *polecenie* ma wartość **NULL** i zostanie znaleziony interpreter poleceń, zwraca wartość niezerową. Jeśli interpreter poleceń nie zostanie znaleziony, zwraca wartość 0 i ustawia **errno** na **ENOENT**. Jeśli *polecenie* nie ma **wartości NULL,** **system** zwraca wartość zwracaną przez interpreter polecenia. Zwraca wartość 0 tylko wtedy, gdy interpreter polecenia zwraca wartość 0. Zwracana wartość - 1 wskazuje błąd, a **errno** jest ustawiona na jedną z następujących wartości:

|||
|-|-|
| **E2BIG ( E2BIG )** | Lista argumentów (która jest zależna od systemu) jest zbyt duża. |
| **Enoent** | Nie można odnaleźć interpretera poleceń. |
| **ENOEXEC ( ENOEXEC )** | Nie można wykonać pliku tłumacza poleceń, ponieważ format jest nieprawidłowy. |
| **ENOMEM ( ENOMEM )** | Za mało pamięci jest dostępna do wykonania polecenia; lub dostępna pamięć została uszkodzona; lub istnieje nieprawidłowy blok, co oznacza, że proces, który sprawia, że wywołanie nie zostało przydzielone poprawnie. |

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr,](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) aby uzyskać więcej informacji na temat tych kodów zwrotnych.

## <a name="remarks"></a>Uwagi

Funkcja **systemowa** przekazuje *polecenie* do interpretera poleceń, który wykonuje ciąg jako polecenie systemu operacyjnego. **system** używa zmiennych środowiskowych **COMSPEC** i **PATH** do zlokalizowania pliku CMD.exe. Jeśli *polecenie* ma wartość **NULL**, funkcja sprawdza tylko, czy interpreter polecenia istnieje.

Przed wywołaniem **systemu**należy wyraźnie opróżnić, używając [fflush](fflush.md) lub [_flushall](flushall.md)lub zamknąć dowolny strumień.

**_wsystem** jest szerokoznakową wersją **systemu;** argumentem *polecenia* **do _wsystem** jest ciągiem znaków o szerokim charakterze. Te funkcje zachowują się identycznie w przeciwnym razie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsystem**|**system**|**system**|**_wsystem**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**system**|\<> lub \<>|
|**_wsystem**|\<> lub \<> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

W tym przykładzie użyto **systemu** do wpisywać plik tekstowy.

```C
// crt_system.c

#include <process.h>

int main( void )
{
   system( "type crt_system.txt" );
}
```

### <a name="input-crt_systemtxt"></a>Dane wejściowe: crt_system.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Dane wyjściowe

```Output
Line one.
Line two.
```

## <a name="see-also"></a>Zobacz też

[Kontrola procesu i środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, funkcje _wexec](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
