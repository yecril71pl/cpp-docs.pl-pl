---
title: System, _wsystem — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- system
- _wsystem
apilocation:
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
apitype: DLLExport
f1_keywords:
- _tsystem
- _wsystem
dev_langs:
- C++
helpviewer_keywords:
- _wsystem function
- wsystem function
- tsystem function
- _tsystem function
- system function
- commands, executing
- command interpreter
ms.assetid: 7d3df2b6-f742-49ce-bf52-012b0aee3df5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca44648ed378d4484b8e4c32a38a6780b3eddd53
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32414705"
---
# <a name="system-wsystem"></a>system, _wsystem

Wykonuje polecenia.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*polecenie*<br/>
Polecenie do wykonania.

## <a name="return-value"></a>Wartość zwracana

Jeśli *polecenia* jest **NULL** i interpreter poleceń zostanie znaleziony, zwraca wartość różną od zera. Jeśli interpreter poleceń nie zostanie znaleziony, zwraca wartość 0 i ustawia **errno** do **enoent —**. Jeśli *polecenia* nie jest **NULL**, **systemu** zwraca wartość zwracaną przez interpreter poleceń. Zwraca wartość 0, tylko wtedy, gdy interpreter poleceń zwraca wartość 0. Zwracana wartość - 1 wskazuje błąd i **errno** ustawiono na jedną z następujących wartości:

|||
|-|-|
**E2BIG —**|Lista argumentów (który jest zależny od systemu) jest za duży.
**ENOENT —**|Nie można odnaleźć interpreter poleceń.
**ENOEXEC —**|Nie można wykonać pliku interpreter poleceń, ponieważ format jest nieprawidłowy.
**ENOMEM —**|Za mało pamięci jest dostępna do wykonania polecenia; lub ilość dostępnej pamięci jest uszkodzona; lub istnieje bloku nie jest ważna, co oznacza, że proces, który jest wywołania nie został poprawnie przydzielony.

Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) uzyskać więcej informacji o tych kody powrotne.

## <a name="remarks"></a>Uwagi

**Systemu** funkcji przekazuje *polecenia* interpreter poleceń, które wykonuje ciąg jako polecenie systemu operacyjnego. **System** używa **COMSPEC** i **ścieżki** zmiennych środowiskowych, aby zlokalizować interpreter poleceń plik CMD.exe. Jeśli *polecenia* jest **NULL**, funkcja właśnie sprawdza, czy istnieje interpreter poleceń.

Użytkownik musi jawnie opróżnić, za pomocą [fflush —](fflush.md) lub [_flushall —](flushall.md), lub zamknij strumieniem przed wywołaniem **systemu**.

**_wsystem —** jest wersja znaków dwubajtowych **systemu**; *polecenia* argument **_wsystem —** jest ciągiem znaków dwubajtowych. Funkcje te działają tak samo w przeciwnym razie wartość.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsystem —**|**system**|**system**|**_wsystem**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**system**|\<process.h > lub \<stdlib.h >|
|**_wsystem**|\<process.h > lub \<stdlib.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

W tym przykładzie użyto **systemu** na typ pliku tekstowego.

```C
// crt_system.c

#include <process.h>

int main( void )
{
   system( "type crt_system.txt" );
}
```

### <a name="input-crtsystemtxt"></a>Dane wejściowe: crt_system.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Dane wyjściowe

```Output
Line one.
Line two.
```

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec, funkcje](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
