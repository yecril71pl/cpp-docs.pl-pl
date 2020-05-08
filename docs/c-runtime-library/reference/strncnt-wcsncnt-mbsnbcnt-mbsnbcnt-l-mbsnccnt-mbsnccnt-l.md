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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 020b844d884182ae7553fec9e9db746987189910
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914211"
---
# <a name="_strncnt-_wcsncnt-_mbsnbcnt-_mbsnbcnt_l-_mbsnccnt-_mbsnccnt_l"></a>_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l

Zwraca liczbę znaków lub bajtów w określonej liczbie.

> [!IMPORTANT]
> **_mbsnbcnt**, **_mbsnbcnt_l**, **_mbsnccnt**i **_mbsnccnt_l** nie mogą być używane w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Ciąg, który ma zostać zbadany.

*liczbą*<br/>
Liczba znaków lub bajtów do zbadania w *str*.

*locale*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_mbsnbcnt** i **_mbsnbcnt_l** zwracają liczbę bajtów znalezionych w pierwszej *liczbie* znaków wielobajtowych *str*. **_mbsnccnt** i **_mbsnccnt_l** zwracają liczbę znaków znalezionych w pierwszej *liczbie* bajtów *str*. Jeśli znak null zostanie napotkany przed zakończeniem badania *str* , zwraca liczbę bajtów lub znaków znalezionych przed znakiem null. Jeśli *str* zawiera mniej niż *Count* znaków lub bajtów, zwraca liczbę znaków lub bajtów w ciągu. Jeśli *Liczba* jest mniejsza od zera, zwracają 0. W poprzednich wersjach te funkcje miały wartość zwracaną typu **int** , a nie **size_t**.

**_strncnt** zwraca liczbę znaków w pierwszej liczbie bajtów *jednobajtowego* ciągu *str*. **_wcsncnt** zwraca liczbę znaków w pierwszej liczbie znaków dwubajtowych *w ciągu* *znaków szerokich* .

## <a name="remarks"></a>Uwagi

**_mbsnbcnt** i **_mbsnbcnt_l** Policz liczbę bajtów znalezionych w pierwszej *liczbie* znaków wielobajtowych *str*. **_mbsnbcnt** i **_mbsnbcnt_l** Zastąp **mtob** i powinny być używane zamiast **mtob**.

**_mbsnccnt** i **_mbsnccnt_l** Policz liczbę znaków znalezionych w pierwszej *liczbie* bajtów *str*. Jeśli **_mbsnccnt** i **_mbsnccnt_l** napotkają znak null w drugim bajcie znaku dwubajtowego, pierwszy bajt jest również uznawany za wartość null i nie jest uwzględniony w zwracanej wartości Count. **_mbsnccnt** i **_mbsnccnt_l** Zastąp **btom** i powinny być używane zamiast **btom**.

Jeśli *str* jest wskaźnikiem o **wartości null** lub *licznik* ma wartość 0, te funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametrów](../../c-runtime-library/parameter-validation.md), **errno** jest ustawiona na **EINVAL**, a funkcja zwraca wartość 0.

Wartość wyjściowa jest zależna od ustawienia ustawienia kategorii **LC_CTYPE** ustawień regionalnych; Aby uzyskać więcej informacji, zobacz [setlocals](setlocale-wsetlocale.md) . Wersje tych funkcji bez sufiksu **_l** używają bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych. wersje z sufiksem **_l** są identyczne, z tą różnicą, że korzystają z przekazaną w zamian parametru ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

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
|**_mbsnbcnt**|\<mbstring. h>|
|**_mbsnbcnt_l**|\<mbstring. h>|
|**_mbsnccnt**|\<mbstring. h>|
|**_mbsnccnt_l**|\<mbstring. h>|
|**_strncnt**|\<Używanie TCHAR. h>|
|**_wcsncnt**|\<Używanie TCHAR. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
[Ustawienie](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
