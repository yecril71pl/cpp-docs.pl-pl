---
title: strncat —, _strncat_l, wcsncat —, _wcsncat_l, _mbsncat —, _mbsncat_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- strncat
- _strncat_l
- _mbsncat
- _mbsncat_l
- wcsncat
- wcsncat_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tcsncat_l
- _wcsncat_l
- _tcsnccat_l
- _mbsncat
- _strncat_l
- strncat
- _tcsnccat
- _mbsncat_l
- _ftcsncat
- wcsncat
- _tcsncat
dev_langs:
- C++
helpviewer_keywords:
- concatenating strings
- ftcsncat function
- tcsncat_l function
- _tcsnccat_l function
- _tcsncat function
- strncat function
- _ftcsncat function
- mbsncat function
- mbsncat_l function
- strings [C++], appending
- wcsncat function
- tcsnccat function
- tcsnccat_l function
- _tcsnccat function
- string concatenation [C++]
- appending strings
- characters [C++], appending to strings
- _mbsncat function
- _tcsncat_l function
- _mbsncat_l function
- tcsncat function
ms.assetid: de67363b-68c6-4ca5-91e3-478610ad8159
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3d80ca39f4bb12fa28190c499d93ad4152831b4e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417590"
---
# <a name="strncat-strncatl-wcsncat-wcsncatl-mbsncat-mbsncatl"></a>strncat —, _strncat_l, wcsncat —, _wcsncat_l _mbsncat —, _mbsncat_l —

Dołącza znaków ciągu. Dostępne są bardziej bezpieczne wersje tych funkcji, zobacz [strncat_s —, _strncat_s_l, wcsncat_s —, _wcsncat_s_l, _mbsncat_s —, _mbsncat_s_l —](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md) .

> [!IMPORTANT]
> **_mbsncat —** i **_mbsncat_l —** nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
char *strncat(
   char *strDest,
   const char *strSource,
   size_t count
);
wchar_t *wcsncat(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count
);
unsigned char *_mbsncat(
   unsigned char *strDest,
   const unsigned char *strSource,
   size_t count
);
unsigned char *_mbsncat_l(
   unsigned char *strDest,
   const unsigned char *strSource,
   size_t count,
   _locale_t locale
);
template <size_t size>
char *strncat(
   char (&strDest)[size],
   const char *strSource,
   size_t count
); // C++ only
template <size_t size>
wchar_t *wcsncat(
   wchar_t (&strDest)[size],
   const wchar_t *strSource,
   size_t count
); // C++ only
template <size_t size>
unsigned char *_mbsncat(
   unsigned char (&strDest)[size],
   const unsigned char *strSource,
   size_t count
); // C++ only
template <size_t size>
unsigned char *_mbsncat_l(
   unsigned char (&strDest)[size],
   const unsigned char *strSource,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*strDest*<br/>
Ciąg docelowego zerem.

*strSource*<br/>
Ciąg źródłowy zerem.

*Liczba*<br/>
Liczba znaków do dołączenia.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do ciągu docelowego. Brak wartości zwracanej jest zarezerwowana wystąpił błąd.

## <a name="remarks"></a>Uwagi

**Strncat —** funkcja dołącza co najwyżej pierwszy *liczba* znaków *strSource* do *strDest*. Litery *strSource* zastępuje znak końcowy null z *strDest*. Jeśli w pojawi się znak null *strSource* przed *liczba* znaki są dołączane, **strncat —** dołącza wszystkie znaki od *strSource*, maksymalnie znakiem pustym. Jeśli *liczba* jest większa niż długość *strSource*, długość *strSource* jest używany zamiast *liczba*. Wszystkich przypadkach, wynikowy ciąg zostanie zakończony znakiem null. Jeśli kopiowanie odbywa się między ciągów, które nakładają się na, zachowanie jest niezdefiniowany.

> [!IMPORTANT]
> **strncat —** nie sprawdza wystarczającą ilość miejsca w *strDest*; w związku z tym jest przyczyną przepełnienia buforu. Należy pamiętać, że *liczba* ogranicza liczbę znaków dołączany; nie jest limit rozmiaru *strDest*. Zobacz poniższy przykład. Aby uzyskać więcej informacji, zobacz [unikanie Overruns buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795).

**wcsncat —** i **_mbsncat —** znaków dwubajtowych i znaków wielobajtowych wersji **strncat —**. Argumenty typu string i zwracana wartość **wcsncat —** są znaków dwubajtowych ciągi; tych **_mbsncat —** są ciągami znaków wielobajtowych. Te trzy funkcje działają tak samo w przeciwnym razie wartość.

Wartość wyjściowa jest zagrożony ustawienie **lc_ctype —** ustawienie kategorii ustawień regionalnych; zobacz [setlocale](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji bez **_l** Użyj sufiksu bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych; wersje z **_l** sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych Przekazano zamiast tego. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

W języku C++ te funkcje mają przeciążenia szablonu. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsncat —**|**strncat**|**_mbsnbcat**|**wcsncat —**|
|**_tcsncat_l —**|**_strncat_l**|**_mbsnbcat_l**|**_wcsncat_l**|

> [!NOTE]
> **_strncat_l** i **_wcsncat_l** nie zależność od ustawień regionalnych, a nie są przeznaczone do bezpośredniego wywoływania. Są one udostępniane do użytku wewnętrznego przez **_tcsncat_l —**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strncat**|\<string.h>|
|**wcsncat —**|\<String.h > lub \<wchar.h >|
|**_mbsncat —**|\<mbstring.h>|
|**_mbsncat_l**|\<mbstring.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_strncat.c
// Use strcat and strncat to append to a string.
#include <stdlib.h>

#define MAXSTRINGLEN 39

char string[MAXSTRINGLEN+1];
// or char *string = malloc(MAXSTRINGLEN+1);

void BadAppend( char suffix[], int n )
{
   strncat( string, suffix, n );
}

void GoodAppend( char suffix[], size_t n )
{
   strncat( string, suffix, __min( n, MAXSTRINGLEN-strlen(string)) );
}

int main( void )
{
   string[0] = '\0';
   printf( "string can hold up to %d characters\n", MAXSTRINGLEN );

   strcpy( string, "This is the initial string!" );
   // concatenate up to 20 characters...
   BadAppend( "Extra text to add to the string...", 20 );
   printf( "After BadAppend :  %s (%d chars)\n", string, strlen(string) );

   strcpy( string, "This is the initial string!" );
   // concatenate up to 20 characters...
   GoodAppend( "Extra text to add to the string...", 20 );
   printf( "After GoodAppend:  %s (%d chars)\n", string, strlen(string) );
}
```

### <a name="output"></a>Dane wyjściowe

```Output
string can hold up to 39 characters
After BadAppend :  This is the initial string!Extra text to add to (47 chars)
After GoodAppend:  This is the initial string!Extra text t (39 chars)
```

Należy pamiętać, że **BadAppend** spowodowała przepełnienie buforu.

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
