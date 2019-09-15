---
title: _chmod, _wchmod
ms.date: 11/04/2016
api_name:
- _chmod
- _wchmod
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
- api-ms-win-crt-filesystem-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: b224133212f19627a8f975dbbe8c80176e29f112
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939207"
---
# <a name="_chmod-_wchmod"></a>_chmod, _wchmod

Zmienia ustawienia uprawnienia do pliku.

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

Te funkcje zwracają wartość 0, jeśli ustawienie uprawnienia zostało pomyślnie zmienione. Zwracana wartość-1 oznacza niepowodzenie. Jeśli określony plik nie został znaleziony, **errno** jest ustawiony na **ENOENT**; Jeśli parametr jest nieprawidłowy, **errno** jest ustawiony na **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja **_chmod** zmienia ustawienie uprawnień pliku określonego przez *filename*. Ustawienie uprawnienia kontroluje dostęp do odczytu i zapisu do pliku. Wyrażenie Integer *PMODE* zawiera jedną lub obie następujące stałe manifestu zdefiniowane w SYS\Stat.h.

| *pmode* | Znaczenie |
|-|-|
| **\_IREAD\_S** | Dozwolony jest tylko odczyt. |
| **\_IWRITE\_S** | Dozwolone jest zapisanie. (W efekcie zezwala na odczyt i zapis). |
| **\_S\_IREAD** &#124; **SIWRITE\_ \_** | Dozwolone odczytywanie i zapisywanie. |

Po otrzymaniu obu stałych są one przyłączone do operatora bitowego or ( **\|** ). Jeśli nie podano uprawnienia do zapisu, plik jest tylko do odczytu. Należy pamiętać, że wszystkie pliki są zawsze do odczytu; nie można udzielić uprawnienia tylko do zapisu. W ten sposób tryby **_S_IWRITE** i **_S_IREAD** \| **_S_IWRITE** są równoważne.

**_wchmod** to dwubajtowa wersja **_chmod**; argumentem *filename* **_wchmod** jest ciąg znaków dwubajtowych. **_wchmod** i **_chmod** zachowują się identycznie w inny sposób.

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *PMODE* nie jest kombinacją jednej z stałych manifestu ani nie zawiera alternatywnego zestawu stałych, funkcja po prostu ignoruje te elementy. Jeśli *Nazwa pliku* ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL** , a funkcja zwraca wartość-1.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tchmod**|**_chmod**|**_chmod**|**_wchmod**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_chmod**|\<io.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|
|**_wchmod**|\<IO. h > lub \<WCHAR. h >|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
[_stat, _wstat Functions](stat-functions.md)<br/>
