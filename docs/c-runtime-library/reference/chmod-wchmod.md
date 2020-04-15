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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: faceb49c921162da042f863abbebbe2ef0a52153
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350093"
---
# <a name="_chmod-_wchmod"></a>_chmod, _wchmod

Zmienia ustawienia uprawnień do plików.

## <a name="syntax"></a>Składnia

```C
int _chmod( const char *filename, int pmode );
int _wchmod( const wchar_t *filename, int pmode );
```

### <a name="parameters"></a>Parametry

*Pod nazwą*<br/>
Nazwa istniejącego pliku.

*pmode*<br/>
Ustawienie uprawnień dla pliku.

## <a name="return-value"></a>Wartość zwracana

Te funkcje zwracają 0, jeśli ustawienie uprawnień zostanie pomyślnie zmienione. Zwracana wartość -1 oznacza błąd. Jeśli nie można odnaleźć określonego pliku, **errno** jest ustawiony na **ENOENT;** jeśli parametr jest nieprawidłowy, **errno** jest ustawiony na **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja **_chmod** zmienia ustawienie uprawnień pliku określonego przez *nazwę pliku*. Ustawienie uprawnień steruje dostępem do odczytu i zapisu do pliku. *Pmode* wyrażenia liczby całkowitej zawiera jedną lub obie z następujących stałych manifestu, zdefiniowane w SYS\Stat.h.

| *pmode* | Znaczenie |
|-|-|
| **\_S\_IREAD (S IREAD)** | Dozwolone tylko czytanie. |
| **\_S\_IWRITE** | Pisanie dozwolone. (W efekcie pozwala na czytanie i pisanie). |
| **\_S\_IREAD** &#124; ** \_S\_IWRITE** | Czytanie i pisanie dozwolone. |

Po podaniu obu stałych są one połączone z operatorem bitowy lub operatorem (**\|**). Jeśli uprawnienie do zapisu nie jest podane, plik jest tylko do odczytu. Należy pamiętać, że wszystkie pliki są zawsze czytelne; nie można udzielić uprawnień tylko do zapisu. W związku z tym tryby **_S_IWRITE** i **_S_IWRITE** \| **_S_IREAD** są równoważne.

**_wchmod** jest szerokoznakową wersją **_chmod**; *argumentnazyt,* który **ma _wchmod** jest ciągiem znaków o szerokim charakterze. **_wchmod** i **_chmod** zachowują się identycznie w przeciwnym razie.

Ta funkcja sprawdza poprawność jego parametrów. Jeśli *pmode* nie jest kombinacją jednej ze stałych manifestu lub zawiera alternatywny zestaw stałych, funkcja po prostu ignoruje te. Jeśli *nazwa pliku* ma wartość **NULL**, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w polu Sprawdzanie [poprawności parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, **errno** jest ustawiona na **Wartość EINVAL** i funkcja zwraca -1.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tchmod**|**_chmod**|**_chmod**|**_wchmod**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_chmod**|\<> io.h|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|
|**_wchmod**|\<io.h> lub \<wchar.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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
