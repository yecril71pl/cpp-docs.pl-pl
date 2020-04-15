---
title: _mbsnbset, _mbsnbset_l
ms.date: 4/2/2020
api_name:
- _mbsnbset
- _mbsnbset_l
- _o__mbsnbset
- _o__mbsnbset_l
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
- mbsnbset
- mbsnbset_l
- _mbsnbset
- _mbsnbset_l
helpviewer_keywords:
- tcsnset function
- _tcsnset_l function
- _mbsnbset function
- _tcsnset function
- _mbsnbset_l function
- mbsnbset_l function
- tcsnset_l function
- mbsnbset function
ms.assetid: 8e46ef75-9a56-42d2-a522-a08450c67c19
ms.openlocfilehash: 57c6d1a81c9aac817b0028e8eccad38d03b0eef7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340545"
---
# <a name="_mbsnbset-_mbsnbset_l"></a>_mbsnbset, _mbsnbset_l

Ustawia pierwszy **n** bajtów ciągu wielobajtowego znaku na określony znak. Dostępne są bezpieczniejsze wersje tych funkcji; patrz [_mbsnbset_s, _mbsnbset_s_l](mbsnbset-s-mbsnbset-s-l.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
unsigned char *_mbsnbset(
   unsigned char *str,
   unsigned int c,
   size_t count
);
unsigned char *_mbsnbset_l(
   unsigned char *str,
   unsigned int c,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Ciąg do zmiany.

*C*<br/>
Ustawienie jednobajtowe lub wielobajtowe.

*Liczba*<br/>
Liczba bajtów do ustawionego.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_mbsnbset** zwraca wskaźnik do zmienionego ciągu.

## <a name="remarks"></a>Uwagi

Funkcje **_mbsnbset** i **_mbsnbset_l** ustawiają co najwyżej pierwsze bajty *zliczania* *od str* do *c*. Jeśli *liczba* jest większa niż długość *str*, długość *str* jest używany zamiast *liczyć*. Jeśli *c* jest znakiem wielobajtowym i nie można go całkowicie ustawić w ostatnim bajcie określonym przez *liczbę,* ostatni bajt jest wyściełany pustym znakiem. **_mbsnbset** i **_mbsnbset_l** nie umieszcza kończącej się wartości null na końcu *ul.*

**_mbsnbset** i **_mbsnbset_l** jest podobny do **_mbsnset**, z tą różnicą, że ustawia *liczbę* bajtów, a nie *zlicza* znaki *c*.

Jeśli *str* ma **wartość NULL** lub *liczba* wynosi zero, ta funkcja generuje nieprawidłowy wyjątek parametru opisany w [zatwierdzeniu parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, **errno** jest ustawiona na **Wartość EINVAL,** a funkcja zwraca **wartość NULL**. Ponadto jeśli *c* nie jest prawidłowym znakiem wielobajtowym, **errno** jest ustawiona na **wartość EINVAL** i zamiast niej jest używana spacja.

Na wartość wyjściową ma wpływ ustawienie **LC_CTYPE** kategorii ustawień regionalnych; zobacz [setlocale,](setlocale-wsetlocale.md) aby uzyskać więcej informacji. **Wersja _mbsnbset** tej funkcji używa bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych; _mbsnbset_l **_mbsnbset_l** wersja jest identyczna, z tą różnicą, że zamiast tego używa parametru ustawień regionalnych przekazanych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

**Uwaga dotycząca zabezpieczeń** Ten interfejs API powoduje potencjalne zagrożenie spowodowane przez problem przepełnienia buforu. Problemy z przepełnieniem buforu są częstą metodą ataku systemu, co powoduje nieuzasadnione podniesienie uprawnień. Aby uzyskać więcej informacji, zobacz [Unikanie przekroczenia buforu](/windows/win32/SecBP/avoiding-buffer-overruns).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnset**|**_strnset**|**_mbsnbset**|**_wcsnset**|
|**_tcsnset_l**|**_strnset_l**|**_mbsnbset_l**|**_wcsnset_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbsnbset**|\<mbstring.h>|
|**_mbsnbset_l**|\<mbstring.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_mbsnbset.c
// compile with: /W3
#include <mbstring.h>
#include <stdio.h>

int main( void )
{
   char string[15] = "This is a test";
   /* Set not more than 4 bytes of string to be *'s */
   printf( "Before: %s\n", string );
   _mbsnbset( string, '*', 4 ); // C4996
   // Note; _mbsnbset is deprecated; consider _mbsnbset_s
   printf( "After:  %s\n", string );
}
```

### <a name="output"></a>Dane wyjściowe

```Output
Before: This is a test
After:  **** is a test
```

## <a name="see-also"></a>Zobacz też

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
