---
title: _chmod —, _wchmod — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _chmod
- _wchmod
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _chmod
- _wchmod
- wchmod
dev_langs:
- C++
helpviewer_keywords:
- _chmod function
- wchmod function
- file permissions [C++]
- chmod function
- files [C++], changing permissions
- _wchmod function
ms.assetid: 92f7cb86-b3b0-4232-a599-b8c04a2f2c19
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b8194e6bdaf93c4bc2cbbc8c2ff2fdf23df438a5
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="chmod-wchmod"></a>_chmod, _wchmod

Zmienia ustawienia pliku uprawnień.

## <a name="syntax"></a>Składnia

```C
int _chmod( const char *filename, int pmode );
int _wchmod( const wchar_t *filename, int pmode );
```

### <a name="parameters"></a>Parametry

*Nazwa pliku*<br/>
Nazwa istniejącego pliku.

*pmode*<br/>
Ustawienie uprawnień dla pliku.

## <a name="return-value"></a>Wartość zwracana

Funkcje zwracają 0, jeśli ustawienie uprawnienia zostanie pomyślnie zmienione. Zwracana wartość -1 oznacza błąd. Jeśli nie można odnaleźć określonego pliku, **errno** ustawiono **enoent —**; Jeśli parametr jest nieprawidłowy, **errno** ustawiono **einval —**.

## <a name="remarks"></a>Uwagi

**_Chmod —** funkcji zmienia ustawienia uprawnień pliku określonego przez *filename*. Ustawienie uprawnień steruje odczytu i zapisu do pliku. Wyrażenie całkowite *pmode* zawiera co najmniej jednej z następujących stałych manifestu, zdefiniowane w SYS\Stat.h.

|*pmode*|Znaczenie|
|-|-|
**_S_IREAD —**|Dozwolone tylko odczyt.
**_S_IWRITE —**|Zapisywanie dozwolone. (W praktyce umożliwia odczytywanie i zapisywanie.)
**_S_IREAD —** &AMP;#124; **_S_IWRITE —**|Odczytywanie i zapisywanie dozwolone.

Gdy zarówno stałe są podane, są połączone z bitowego or — operator (**|**). Jeśli uprawnienia do zapisu nie zostanie podany, plik jest tylko do odczytu. Należy pamiętać, że wszystkie pliki są zawsze do odczytu; nie jest możliwe nadaj uprawnienia tylko do zapisu. W związku z tym tryby **_s_iwrite —** i **_s_iread —** | **_s_iwrite —** są równoważne.

**_wchmod —** jest wersja znaków dwubajtowych **_chmod —**; *filename* argument **_wchmod —** jest ciągiem znaków dwubajtowych. **_wchmod —** i **_chmod —** zachowują się tak samo w przeciwnym razie wartość.

Ta funkcja weryfikuje jego parametrów. Jeśli *pmode* nie jest kombinacją jednego z manifestu stałe lub zawiera inny zestaw stałych, funkcja po prostu ignoruje te. Jeśli *filename* jest **NULL**, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **errno** ustawiono **einval —** i funkcja zwraca wartość -1.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tchmod**|**_chmod —**|**_chmod —**|**_wchmod —**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_chmod —**|\<io.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|
|**_wchmod —**|\<IO.h > lub \<wchar.h >|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_chmod.c
// This program uses _chmod to
// change the mode of a file to read-only.
// It then attempts to modify the file.
//

#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

// Change the mode and report error or success
void set_mode_and_report(char * filename, int mask)
{
   // Check for failure
   if( _chmod( filename, mask ) == -1 )
   {
      // Determine cause of failure and report.
      switch (errno)
      {
         case EINVAL:
            fprintf( stderr, "Invalid parameter to chmod.\n");
            break;
         case ENOENT:
            fprintf( stderr, "File %s not found\n", filename );
            break;
         default:
            // Should never be reached
            fprintf( stderr, "Unexpected error in chmod.\n" );
       }
   }
   else
   {
      if (mask == _S_IREAD)
        printf( "Mode set to read-only\n" );
      else if (mask & _S_IWRITE)
        printf( "Mode set to read/write\n" );
   }
   fflush(stderr);
}

int main( void )
{

   // Create or append to a file.
   system( "echo /* End of file */ >> crt_chmod.c_input" );

   // Set file mode to read-only:
   set_mode_and_report("crt_chmod.c_input ", _S_IREAD );

   system( "echo /* End of file */ >> crt_chmod.c_input " );

   // Change back to read/write:
   set_mode_and_report("crt_chmod.c_input ", _S_IWRITE );

   system( "echo /* End of file */ >> crt_chmod.c_input " );
}
```

```Output

A line of text.

```

```Output

      A line of text.Mode set to read-only
Access is denied.
Mode set to read/write
```

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_stat, _wstat — funkcje](stat-functions.md)<br/>
