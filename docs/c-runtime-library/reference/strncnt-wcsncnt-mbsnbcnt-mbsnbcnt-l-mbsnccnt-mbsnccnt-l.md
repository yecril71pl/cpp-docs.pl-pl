---
title: _strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l
ms.date: 4/2/2020
api_name:
- _mbsnbcnt_l
- _mbsnccnt
- _wcsncnt
- _strncnt
- _mbsnccnt_l
- _mbsnbcnt
- _o__mbsnbcnt
- _o__mbsnbcnt_l
- _o__mbsnccnt
- _o__mbsnccnt_l
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: bfd339a38dd5df30ece72059525860603ee10748
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364182"
---
# <a name="_strncnt-_wcsncnt-_mbsnbcnt-_mbsnbcnt_l-_mbsnccnt-_mbsnccnt_l"></a>_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l

Zwraca liczbę znaków lub bajtów w określonej liczbie.

> [!IMPORTANT]
> **_mbsnbcnt**, **_mbsnbcnt_l**, **_mbsnccnt**i **_mbsnccnt_l** nie mogą być używane w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Str*<br/>
Ciąg do zbadania.

*Liczba*<br/>
Liczba znaków lub bajtów do zbadania w *ul*.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_mbsnbcnt** i **_mbsnbcnt_l** zwracają liczbę bajtów znalezionych w pierwszej *liczbie* znaków wielobajtowych *str*. **_mbsnccnt** i **_mbsnccnt_l** zwracają liczbę znaków znalezionych w pierwszej *liczbie* bajtów *str*. Jeśli znak null zostanie napotkany przed zakończeniem badania *str,* zwracają one liczbę bajtów lub znaków znalezionych przed znakiem null. Jeśli *str* składa się z mniej niż *liczba* znaków lub bajtów, zwracają liczbę znaków lub bajtów w ciągu. Jeśli *liczba* jest mniejsza niż zero, zwracają 0. W poprzednich wersjach te funkcje miały wartość zwracaną typu **int,** a nie **size_t**.

**_strncnt** zwraca liczbę znaków w pierwszych *bajtach licznika* jednobajtowego ciągu *str*. **_wcsncnt** zwraca liczbę znaków w pierwszej *liczbie* znaków szerokich znaków szerokiego znaku *str*.

## <a name="remarks"></a>Uwagi

**_mbsnbcnt** i **_mbsnbcnt_l** policzyć liczbę bajtów znalezionych w pierwszej *liczbie* znaków wielobajtowych *str*. **_mbsnbcnt** i **_mbsnbcnt_l** zastąpić **mtob** i powinny być stosowane zamiast **mtob**.

**_mbsnccnt** i **_mbsnccnt_l** policzyć liczbę znaków znalezionych w pierwszej *liczbie* bajtów *str*. Jeśli **_mbsnccnt** i **_mbsnccnt_l** napotkania znaku null w drugim bajcie znaku dwu bajtowego, pierwszy bajt jest również uważany za null i nie jest uwzględniony w zwracanej wartości liczby. **_mbsnccnt** i **_mbsnccnt_l** zastąpić **btom** i powinny być stosowane zamiast **btom**.

Jeśli *str* jest wskaźnikiem **NULL** lub jest *liczbą* 0, te funkcje wywołują nieprawidłowy program obsługi parametrów zgodnie z opisem w [zatwierdzeniu parametru](../../c-runtime-library/parameter-validation.md), **errno** jest ustawiona na **Wartość EINVAL**, a funkcja zwraca wartość 0.

Na wartość wyjściową ma wpływ ustawienie **LC_CTYPE** kategorii ustawień regionalnych; zobacz [setlocale,](setlocale-wsetlocale.md) aby uzyskać więcej informacji. Wersje tych funkcji bez sufiksu **_l** używają bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych; wersje z sufiksem **_l** są identyczne, z tą różnicą, że zamiast tego używają parametru ustawień regionalnych przekazanych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|-------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnbcnt**|**_strncnt**|**_mbsnbcnt**|**_wcsncnt**|
|**_tcsnccnt**|**_strncnt**|**_mbsnbcnt**|Nie dotyczy|
|**_wcsncnt**|Nie dotyczy|Nie dotyczy|**_mbsnbcnt**|
|**_wcsncnt**|Nie dotyczy|Nie dotyczy|**_mbsnccnt**|
|Nie dotyczy|Nie dotyczy|**_mbsnbcnt_l**|**_mbsnccnt_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbsnbcnt**|\<mbstring.h>|
|**_mbsnbcnt_l**|\<mbstring.h>|
|**_mbsnccnt**|\<mbstring.h>|
|**_mbsnccnt_l**|\<mbstring.h>|
|**_strncnt**|\<tchar.h>|
|**_wcsncnt**|\<tchar.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
