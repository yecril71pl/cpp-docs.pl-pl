---
title: _mktemp, _wmktemp
ms.date: 4/2/2020
api_name:
- _wmktemp
- _mktemp
- _o__mktemp
- _o__wmktemp
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tmktemp
- wmktemp
- tmktemp
- _wmktemp
- _mktemp
helpviewer_keywords:
- _wmktemp function
- _mktemp function
- files [C++], temporary
- tmktemp function
- _tmktemp function
- wmktemp function
- mktemp function
- temporary files [C++]
ms.assetid: 055eb539-a8c2-4a7d-be54-f5b6d1eb5c85
ms.openlocfilehash: 536a63841c6e29fa003eb8b99c896f6d1cf5519f
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919100"
---
# <a name="_mktemp-_wmktemp"></a>_mktemp, _wmktemp

Tworzy unikatową nazwę pliku. Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [_mktemp_s, _wmktemp_s](mktemp-s-wmktemp-s.md).

## <a name="syntax"></a>Składnia

```C
char *_mktemp(
   char *nameTemplate
);
wchar_t *_wmktemp(
   wchar_t *nameTemplate
);
template <size_t size>
char *_mktemp(
   char (&nameTemplate)[size]
); // C++ only
template <size_t size>
wchar_t *_wmktemp(
   wchar_t (&nameTemplate)[size]
); // C++ only
```

### <a name="parameters"></a>Parametry

*nameTemplate*<br/>
Wzorzec nazwy pliku.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do zmodyfikowanego nameTemplate. Funkcja zwraca **wartość null** , jeśli *nameTemplate* jest źle sformułowane lub nie można utworzyć więcej unikatowych nazw z danego nameTemplate.

## <a name="remarks"></a>Uwagi

Funkcja **_mktemp** tworzy unikatową nazwę pliku, modyfikując argument *nameTemplate* . **_mktemp** automatycznie obsługuje argumenty ciągu znaków wielobajtowych, aby rozpoznawać sekwencje znaków wielobajtowych zgodnie ze stroną kodową wielobajtowego aktualnie używaną przez system czasu wykonywania. **_wmktemp** to dwubajtowa wersja **_mktemp**; argument i zwracana wartość **_wmktemp** są ciągami znaków dwubajtowych. **_wmktemp** i **_mktemp** zachowują się identycznie, z tą różnicą, że **_wmktemp** nie obsługują ciągów znaków wielobajtowych.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp**|**_mktemp**|**_mktemp**|**_wmktemp**|

Argument *nameTemplate* ma postać *Base*XXXXXX, gdzie *Base* jest częścią nowej nazwy pliku, którą dostarczasz, a każdy X jest symbolem zastępczym znaku dostarczonego przez **_mktemp**. Każdy znak zastępczy w *nameTemplate* musi być wielką literą x. **_mktemp** zachowuje *podstawową* i zastępuje pierwszy znak x symbolem alfabetycznym. **_mktemp** zastępuje następujące znaki końcowe X wartością z pięciu cyfr; Ta wartość jest unikatowym numerem identyfikującym proces wywołujący lub w programach wielowątkowych, wątek wywołujący.

Każde pomyślne wywołanie do **_mktemp** modyfikuje *nameTemplate*. W każdym kolejnym wywołaniu z tego samego procesu lub wątku z tym samym *nameTemplate* argumentem nameTemplate **_mktemp** sprawdza nazwy plików, które są zgodne z nazwami zwracanymi przez **_mktemp** w poprzednich wywołaniach. Jeśli plik nie istnieje dla danej nazwy, **_mktemp** zwraca tę nazwę. Jeśli istnieją pliki dla wszystkich poprzednio zwróconych nazw, **_mktemp** tworzy nową nazwę przez zastąpienie znaku alfabetycznego, który został użyty w wcześniej zwróconej nazwie z następną dostępną małą literą, w kolejności od "a" do "z". Na przykład jeśli *podstawowa* :

> **Fn**

i pięć cyfr dostarczonych przez **_mktemp** to 12345, pierwsza zwrócona nazwa:

> **fna12345**

Jeśli ta nazwa jest używana do tworzenia pliku FNA12345, a ten plik nadal istnieje, następna nazwa zwrócona przez wywołanie z tego samego procesu lub wątku z tą samą *podstawą* dla *nameTemplate* jest:

> **fnb12345**

Jeśli FNA12345 nie istnieje, zwracana jest kolejna Nazwa:

> **fna12345**

**_mktemp** może utworzyć maksymalnie 26 unikatowych nazw plików dla każdej kombinacji wartości *podstawowych* i *nameTemplate* . W związku z tym FNZ12345 jest ostatnią unikatową nazwą pliku **_mktemp** można utworzyć dla wartości *podstawowych* i *nameTemplate* używanych w tym przykładzie.

W przypadku niepowodzenia ustawiono **errno** . Jeśli *nameTemplate* ma nieprawidłowy format (na przykład mniej niż 6 X), **errno** jest ustawiona na **EINVAL**. Jeśli **_mktemp** nie może utworzyć unikatowej nazwy, ponieważ wszystkie 26 możliwych nazw plików już istnieją, **_mktemp** ustawia nameTemplate do pustego ciągu i zwraca **EEXIST**.

W języku C++ te funkcje mają przeciążenia szablonu, które wywołują nowsze, bezpieczne odpowiedniki tych funkcji. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mktemp**|\<IO. h>|
|**_wmktemp**|\<IO. h> lub \<WCHAR. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_mktemp.c
// compile with: /W3
/* The program uses _mktemp to create
* unique filenames. It opens each filename
* to ensure that the next name is unique.
*/

#include <io.h>
#include <string.h>
#include <stdio.h>
#include <errno.h>

char *template = "fnXXXXXX";
char *result;
char names[27][9];

int main( void )
{
   int i;
   FILE *fp;

   for( i = 0; i < 27; i++ )
   {
      strcpy_s( names[i], sizeof( names[i] ), template );
      /* Attempt to find a unique filename: */
      result = _mktemp( names[i] );  // C4996
      // Note: _mktemp is deprecated; consider using _mktemp_s instead
      if( result == NULL )
      {
         printf( "Problem creating the template\n" );
         if (errno == EINVAL)
         {
             printf( "Bad parameter\n");
         }
         else if (errno == EEXIST)
         {
             printf( "Out of unique filenames\n");
         }
      }
      else
      {
         fopen_s( &fp, result, "w" );
         if( fp != NULL )
            printf( "Unique filename is %s\n", result );
         else
            printf( "Cannot open %s\n", result );
         fclose( fp );
      }
   }
}
```

```Output
Unique filename is fna03912
Unique filename is fnb03912
Unique filename is fnc03912
Unique filename is fnd03912
Unique filename is fne03912
Unique filename is fnf03912
Unique filename is fng03912
Unique filename is fnh03912
Unique filename is fni03912
Unique filename is fnj03912
Unique filename is fnk03912
Unique filename is fnl03912
Unique filename is fnm03912
Unique filename is fnn03912
Unique filename is fno03912
Unique filename is fnp03912
Unique filename is fnq03912
Unique filename is fnr03912
Unique filename is fns03912
Unique filename is fnt03912
Unique filename is fnu03912
Unique filename is fnv03912
Unique filename is fnw03912
Unique filename is fnx03912
Unique filename is fny03912
Unique filename is fnz03912
Problem creating the template.
Out of unique filenames.
```

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_getpid](getpid.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[tmpfile](tmpfile.md)<br/>
