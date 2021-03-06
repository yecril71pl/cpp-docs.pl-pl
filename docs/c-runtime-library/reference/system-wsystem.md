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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 15e4637d709fdf4600ecb4c66c7d4a75c4fa07eb
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844980"
---
# <a name="system-_wsystem"></a>system, _wsystem

Wykonuje polecenie.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*dotyczące*<br/>
Polecenie, które ma zostać wykonane.

## <a name="return-value"></a>Wartość zwracana

Jeśli *polecenie* ma wartość **null** i zostanie znaleziony interpreter poleceń, funkcja zwraca wartość różną od zera. Jeśli interpreter poleceń nie zostanie znaleziony, zwraca wartość 0 i ustawia **errno** na **ENOENT**. Jeśli *polecenie* nie ma **wartości null**, **system** zwraca wartość, która jest zwracana przez interpreter poleceń. Zwraca wartość 0 tylko wtedy, gdy interpreter poleceń zwróci wartość 0. Zwracana wartość-1 wskazuje błąd, a **errno** jest ustawiona na jedną z następujących wartości:

| Wartość | Opis |
|-|-|
| **E2BIG** | Lista argumentów (która jest zależna od systemu) jest zbyt duża. |
| **ENOENT** | Nie można znaleźć interpretera poleceń. |
| **ENOEXEC** | Nie można wykonać pliku interpretera poleceń, ponieważ format jest nieprawidłowy. |
| **ENOMEM** | Za mało dostępnej pamięci do wykonania polecenia; lub dostępna pamięć została uszkodzona; lub istnieje nieprawidłowy blok, który wskazuje, że proces wywołujący wywołanie nie został poprawnie przydzielony. |

Aby uzyskać więcej informacji na temat kodów powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Uwagi

Funkcja **system** przekazuje *polecenie* do interpretera poleceń, który wykonuje ciąg jako polecenie systemu operacyjnego. **system** używa zmiennych środowiskowych **wywołana** i **Path** do lokalizowania pliku interpretera poleceń CMD.exe. Jeśli *polecenie* ma **wartość null**, funkcja po prostu sprawdza, czy istnieje interpreter poleceń.

Należy jawnie opróżniać przy użyciu [fflush](fflush.md) lub [_flushall](flushall.md)lub zamknąć wszystkie strumienie przed wywołaniem **system**.

**_wsystem** to dwubajtowa wersja **systemu**; argument *polecenia* do **_wsystem** jest ciągiem znaków dwubajtowych. Funkcje te zachowują się identycznie w inny sposób.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsystem**|**system**|**system**|**_wsystem**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**system**|\<process.h> lub \<stdlib.h>|
|**_wsystem**|\<process.h> lub \<stdlib.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten przykład używa **systemu** do wpisania pliku tekstowego.

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

[Proces i kontrola środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, funkcje _wexec](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_spawn, funkcje _wspawn](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
