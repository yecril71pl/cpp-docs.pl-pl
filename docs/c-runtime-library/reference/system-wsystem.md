---
title: system, _wsystem
ms.date: 11/04/2016
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
helpviewer_keywords:
- _wsystem function
- wsystem function
- tsystem function
- _tsystem function
- system function
- commands, executing
- command interpreter
ms.assetid: 7d3df2b6-f742-49ce-bf52-012b0aee3df5
ms.openlocfilehash: 46c4949fcc8cfbe4a3477e66b57d8fc6fc97ed73
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259095"
---
# <a name="system-wsystem"></a>system, _wsystem

Wykonuje polecenie.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Polecenie*<br/>
Polecenie do wykonania.

## <a name="return-value"></a>Wartość zwracana

Jeśli *polecenia* jest **NULL** i interpretera poleceń zostanie znaleziona, zwraca wartość różną od zera. Jeśli interpreter poleceń nie zostanie znaleziona, zwraca wartość 0 i ustawia **errno** do **ENOENT**. Jeśli *polecenia* nie **NULL**, **systemu** zwraca wartość, która jest zwracana przez interpretera poleceń. Zwraca wartość 0, tylko wtedy, gdy interpreter poleceń zwraca wartość 0. Zwracana wartość-1 wskazuje błąd, i **errno** jest ustawiony na jedną z następujących wartości:

|||
|-|-|
| **E2BIG** | Lista argumentów (która jest zależna od systemu) jest zbyt duży. |
| **ENOENT** | Nie można odnaleźć interpreter poleceń. |
| **ENOEXEC** | Nie można wykonać pliku interpreter poleceń, ponieważ format jest nieprawidłowy. |
| **ENOMEM** | Jest dostępna, można wykonać polecenia; nie ma wystarczającej ilości pamięci lub ilość dostępnej pamięci jest uszkodzony; lub istnieje nieprawidłowy blok, co oznacza, że proces, który wykonuje wywołanie nie został poprawnie przydzielony. |

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) uzyskać więcej informacji o tych kody powrotne.

## <a name="remarks"></a>Uwagi

**Systemu** funkcji przebiegów *polecenia* do interpretera poleceń, które wykonuje ciągu jako polecenie systemu operacyjnego. **System** używa **COMSPEC** i **ścieżki** zmiennych środowiskowych w celu zlokalizowania interpreter poleceń plik CMD.exe. Jeśli *polecenia* jest **NULL**, funkcja sprawdza jedynie, czy istnieje interpreter poleceń.

Użytkownik musi jawnie opróżnienia, za pomocą [fflush —](fflush.md) lub [_flushall —](flushall.md), lub zamknij strumienie przed wywołaniem **systemu**.

**_wsystem —** to wersja znaku dwubajtowego **systemu**; *polecenia* argument **_wsystem —** jest ciągiem znaku dwubajtowego. Funkcje te zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsystem**|**system**|**system**|**_wsystem**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**system**|\<process.h > lub \<stdlib.h >|
|**_wsystem**|\<process.h > lub \<stdlib.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

W tym przykładzie użyto **systemu** do typu pliku tekstowego.

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
