---
title: _chmod, _wchmod
ms.date: 4/2/2020
api_name:
- _chmod
- _wchmod
- _o__chmod
- _o__wchmod
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: b1bc89ce51fff44a847111d68cac8e8b3f58a635
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917006"
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
| **\_S\_IREAD** &#124; ** \_s\_IWRITE** | Dozwolone odczytywanie i zapisywanie. |

Po otrzymaniu obu stałych są one przyłączone do operatora bitowego or (**\|**). Jeśli nie podano uprawnienia do zapisu, plik jest tylko do odczytu. Należy pamiętać, że wszystkie pliki są zawsze do odczytu; nie można udzielić uprawnienia tylko do zapisu. W tym celu tryby **_S_IWRITE** i **_S_IREAD** \| **_S_IWRITE** są równoważne.

**_wchmod** to dwubajtowa wersja **_chmod**; argument *filename* **_wchmod** jest ciągiem znaków dwubajtowych. **_wchmod** i **_chmod** zachowują się identycznie w inny sposób.

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *PMODE* nie jest kombinacją jednej z stałych manifestu ani nie zawiera alternatywnego zestawu stałych, funkcja po prostu ignoruje te elementy. Jeśli *Nazwa pliku* ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL** , a funkcja zwraca wartość-1.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tchmod**|**_chmod**|**_chmod**|**_wchmod**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_chmod**|\<IO. h>|\<sys/Types. h>, \<sys/stat. h>, \<errno. h>|
|**_wchmod**|\<IO. h> lub \<WCHAR. h>|\<sys/Types. h>, \<sys/stat. h>, \<errno. h>|

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

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_stat, funkcje _wstat](stat-functions.md)<br/>
