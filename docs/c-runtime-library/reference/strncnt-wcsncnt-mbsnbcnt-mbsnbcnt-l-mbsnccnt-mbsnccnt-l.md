---
title: _strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l
ms.date: 11/04/2016
apiname:
- _mbsnbcnt_l
- _mbsnccnt
- _wcsncnt
- _strncnt
- _mbsnccnt_l
- _mbsnbcnt
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
apitype: DLLExport
f1_keywords:
- _mbsnbcnt
- wcsncnt
- _tcsnbcnt
- _mbsnccnt
- _ftcsnbcnt
- mbsnbcnt
- strncnt
- mbsnbcnt_l
- mbsnccnt_l
- mbsnccnt
- _strncnt
- _wcsncnt
helpviewer_keywords:
- _strncnt function
- _mbsnbcnt function
- _mbsnbcnt_l function
- _mbsnccnt_l function
- mbsnbcnt_l function
- mbsnbcnt function
- tcsnbcnt function
- mbsnccnt_l function
- strncnt function
- _tcsnbcnt function
- mbsnccnt function
- wcsncnt function
- _mbsnccnt function
- _wcsncnt function
ms.assetid: 2a022e9e-a307-4acb-a66b-e56e5357f848
ms.openlocfilehash: 456a11ae98fe8fb40c2ef1d6f4e6d86583f4b7b3
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51520217"
---
# <a name="strncnt-wcsncnt-mbsnbcnt-mbsnbcntl-mbsnccnt-mbsnccntl"></a>_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l

Zwraca liczbę znaków lub liczbę bajtów w ciągu określonej liczby.

> [!IMPORTANT]
> **_mbsnbcnt**, **_mbsnbcnt_l**, **_mbsnccnt**, i **_mbsnccnt_l** nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
size_t _strncnt(
   const char *str,
   size_t count
);
size_t _wcsncnt(
   const wchar_t *str,
   size_t count
);
size_t _mbsnbcnt(
   const unsigned char *str,
   size_t count
);
size_t _mbsnbcnt_l(
   const unsigned char *str,
   size_t count,
   _locale_t locale
);
size_t _mbsnccnt(
   const unsigned char *str,
   size_t count
);
size_t _mbsnccnt_l(
   const unsigned char *str,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Ciąg do badania.

*Liczba*<br/>
Liczba znaków lub liczbę bajtów do badania w *str*.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_mbsnbcnt** i **_mbsnbcnt_l** zwracają liczbę bajtów znalezionych w pierwszym *liczba* znaków wielobajtowych *str*. **_mbsnccnt** i **_mbsnccnt_l** zwracają liczbę znaków znalezionych w pierwszym *liczba* bajtów *str*. Jeśli znak null zostanie osiągnięty zanim badanie *str* jest zakończone, zwracają one liczbę bajtów lub znaków znalezionych przed znakiem null. Jeśli *str* składa się z mniej niż *liczba* znaków lub liczbę bajtów, zwracają one liczbę znaków lub liczbę bajtów w ciągu. Jeśli *liczba* jest mniejsza od zera, zwracają 0. W poprzednich wersjach te funkcje miały wartość zwrotu typu **int** zamiast **size_t**.

**_strncnt** zwraca liczbę znaków w pierwszym *liczba* bajtów ciąg znaków jednobajtowych *str*. **_wcsncnt** zwraca liczbę znaków w pierwszym *liczba* znaków dwubajtowych w ciągu znaków dwubajtowych *str*.

## <a name="remarks"></a>Uwagi

**_mbsnbcnt** i **_mbsnbcnt_l** liczbę bajtów znalezionych w pierwszym *liczba* znaków wielobajtowych *str*. **_mbsnbcnt** i **_mbsnbcnt_l** Zastąp **mtob** i powinna być używana zamiast **mtob**.

**_mbsnccnt** i **_mbsnccnt_l** liczbę znaków znalezionych w pierwszym *liczba* bajtów *str*. Jeśli **_mbsnccnt** i **_mbsnccnt_l** wystąpić znak null w drugim bajcie znaków dwubajtowych, pierwszy bajt jest również uważany za wartość null i nie są objęte wartości liczby zwracanej. **_mbsnccnt** i **_mbsnccnt_l** Zastąp **btom** i powinna być używana zamiast **btom**.

Jeśli *str* jest **NULL** wskaźnika lub *liczba* wynosi 0, funkcje te wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md), **errno** ustawiono **EINVAL**, a funkcja zwraca 0.

Wartość wyjściowa jest zależna od ustawienia **LC_CTYPE** ustawienia kategorii ustawień regionalnych; zobacz [setlocale](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji, bez **_l** sufiks używają bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych; wersje **_l** sufiksem są identyczne, z tą różnicą, że używają parametru ustawień regionalnych w zamian przekazanych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|-------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnbcnt**|**_strncnt**|**_mbsnbcnt**|**_wcsncnt**|
|**_tcsnccnt**|**_strncnt**|**_mbsnbcnt**|n/d|
|**_wcsncnt**|n/d|n/d|**_mbsnbcnt**|
|**_wcsncnt**|n/d|n/d|**_mbsnccnt**|
|n/d|n/d|**_mbsnbcnt_l**|**_mbsnccnt_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbsnbcnt**|\<mbstring.h>|
|**_mbsnbcnt_l**|\<mbstring.h>|
|**_mbsnccnt**|\<mbstring.h>|
|**_mbsnccnt_l**|\<mbstring.h>|
|**_strncnt**|\<tchar.h >|
|**_wcsncnt**|\<tchar.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_mbsnbcnt.c

#include  <mbstring.h>
#include  <stdio.h>

int main( void )
{
   unsigned char str[] = "This is a multibyte-character string.";
   unsigned int char_count, byte_count;
   char_count = _mbsnccnt( str, 10 );
   byte_count = _mbsnbcnt( str, 10 );
   if ( byte_count - char_count )
      printf( "The first 10 characters contain %d multibyte characters\n", char_count );
   else
      printf( "The first 10 characters are single-byte.\n");
}
```

### <a name="output"></a>Dane wyjściowe

```Output
The first 10 characters are single-byte.
```

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
