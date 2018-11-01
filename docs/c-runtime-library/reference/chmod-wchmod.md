---
title: _chmod, _wchmod
ms.date: 11/04/2016
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
helpviewer_keywords:
- _chmod function
- wchmod function
- file permissions [C++]
- chmod function
- files [C++], changing permissions
- _wchmod function
ms.assetid: 92f7cb86-b3b0-4232-a599-b8c04a2f2c19
ms.openlocfilehash: 7f3133aac1548be5cb497fe32ae4f9f1c0e238d9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595133"
---
# <a name="chmod-wchmod"></a>_chmod, _wchmod

Zmienia ustawienia uprawnień do pliku.

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

Te funkcje zwracają 0, jeśli ustawienie uprawnienia zostało pomyślnie zmienione. Zwracana wartość-1 wskazuje błąd. Jeśli nie można odnaleźć określonego pliku, **errno** ustawiono **ENOENT**; Jeśli parametr jest nieprawidłowy, **errno** ustawiono **EINVAL**.

## <a name="remarks"></a>Uwagi

**_Chmod —** funkcji zmienia ustawienie uprawnienia w pliku określonym przez *filename*. Ustawienie uprawnienia steruje odczytu i zapisu do pliku. Wyrażenia typu całkowitego *pmode* zawiera jeden lub oba z następujących stałych manifestu, określonych w SYS\Stat.h.

|*pmode*|Znaczenie|
|-|-|
**_S_IREAD**|Dozwolone tylko odczyt.
**_S_IWRITE**|Zapisywanie jest dozwolone. (W praktyce pozwala na odczyt i zapis.)
**_S_IREAD** &AMP;#124; **_S_IWRITE**|Odczyt i zapis dozwolone.

Gdy oba stałe są podane, są połączone przy użyciu bitowego operatora or — operator (**|**). Jeśli uprawnienia do zapisu nie zostanie określony, plik jest tylko do odczytu. Należy pamiętać, że wszystkie pliki są zawsze czytelny; nie jest możliwe przyznać uprawnienia tylko do zapisu. W efekcie tryby **_S_IWRITE** i **_S_IREAD** | **_S_IWRITE** są równoważne.

**_wchmod —** to wersja znaku dwubajtowego **_chmod —**; *filename* argument **_wchmod —** jest ciągiem znaku dwubajtowego. **_wchmod —** i **_chmod —** zachowują się identycznie.

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *pmode* nie jest kombinacją jednej ze stałych manifestu lub inny zestaw zawiera stałych, funkcja po prostu ignoruje te. Jeśli *filename* jest **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** a funkcja zwraca wartość -1.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tchmod**|**_chmod —**|**_chmod —**|**_wchmod —**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_chmod —**|\<io.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|
|**_wchmod —**|\<IO.h > lub \<wchar.h >|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
