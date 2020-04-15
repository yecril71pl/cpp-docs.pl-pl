---
title: strcspn, wcscspn, _mbscspn, _mbscspn_l
ms.date: 4/2/2020
api_name:
- _mbscspn_l
- wcscspn
- _mbscspn
- strcspn
- _o__mbscspn
- _o__mbscspn_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strcspn
- _mbscspn
- wcscspn
- _ftcscspn
- _tcscspn
helpviewer_keywords:
- strings [C++], searching
- ftcscspn function
- strcspn function
- _mbscspn function
- mbscspn_l function
- wcscspn function
- tcscspn function
- _ftcscspn function
- _mbscspn_l function
- mbscspn function
- _tcscspn function
ms.assetid: f73f51dd-b533-4e46-ba29-d05c553708a6
ms.openlocfilehash: 2ba3c2941736d185ad93c7c6e44cb83c82ebb478
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358878"
---
# <a name="strcspn-wcscspn-_mbscspn-_mbscspn_l"></a>strcspn, wcscspn, _mbscspn, _mbscspn_l

Zwraca indeks pierwszego wystąpienia w ciągu znaku, który należy do zestawu znaków.

> [!IMPORTANT]
> **_mbschr** i **_mbschr_l** nie mogą być używane w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
size_t strcspn(
   const char *str,
   const char *strCharSet
);
size_t wcscspn(
   const wchar_t *str,
   const wchar_t *strCharSet
);
size_t _mbscspn(
   const unsigned char *str,
   const unsigned char *strCharSet
);
size_t _mbscspn_l(
   const unsigned char *str,
   const unsigned char *strCharSet,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Przeszukiwany ciąg zakończony zerem.

*strCharSet (Zestaw strCharset)*<br/>
Zestaw znaków zakończony z wartością null.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Te funkcje zwracają indeks pierwszego znaku w *str,* który znajduje się w *strCharSet*. Jeśli żaden ze znaków w *str* jest w *strCharSet*, to wartość zwracana jest długość *str*.

Żadna wartość zwracana nie jest zarezerwowana, aby wskazać błąd.

## <a name="remarks"></a>Uwagi

**wcscspn** i **_mbscspn** są szerokoznakowymi i wielobajtowymi znakami **strcspn**. Argumenty **wcscspn** są ciągi znaków o szerokich znakach; **_mbscspn** są ciągami znaków wielobajtowych.

**_mbscspn** sprawdza poprawność jego parametrów. Jeśli *str* lub *strCharSet* jest wskaźnikiem null, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [programie Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, funkcja zwraca 0 i ustawia **errno** na **EINVAL**. **strcspn** i **wcscspn** nie weryfikują swoich parametrów. Te trzy funkcje zachowują się identycznie inaczej.

Na wartość wyjściową ma wpływ ustawienie **LC_CTYPE** kategorii ustawień regionalnych; zobacz [setlocale,](setlocale-wsetlocale.md) aby uzyskać więcej informacji. Wersje tych funkcji bez sufiksu **_l** używają bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych; wersje z sufiksem **_l** są identyczne, z tą różnicą, że zamiast tego używają parametru ustawień regionalnych przekazanych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscspn**|**strcspn (strcspn)**|**_mbscspn**|**wcscspn**|
|Nie dotyczy|Nie dotyczy|**_mbscspn_l**|Nie dotyczy|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strcspn (strcspn)**|\<string.h>|
|**wcscspn**|\<string.h> lub \<wchar.h>|
|**_mbscspn** **, _mbscspn_l**|\<mbstring.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_strcspn.c

#include <string.h>
#include <stdio.h>

void test( const char * str, const char * strCharSet )
{
   int pos = strcspn( str, strCharSet );
   printf( "strcspn( \"%s\", \"%s\" ) = %d\n", str, strCharSet, pos );
}

int main( void )
{
   test( "xyzbxz", "abc" );
   test( "xyzbxz", "xyz" );
   test( "xyzbxz", "no match" );
   test( "xyzbxz", "" );
   test( "", "abc" );
   test( "", "" );
}
```

```Output
strcspn( "xyzbxz", "abc" ) = 3
strcspn( "xyzbxz", "xyz" ) = 0
strcspn( "xyzbxz", "no match" ) = 6
strcspn( "xyzbxz", "" ) = 6
strcspn( "", "abc" ) = 0
strcspn( "", "" ) = 0
```

## <a name="see-also"></a>Zobacz też

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
