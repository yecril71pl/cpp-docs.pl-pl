---
title: _mbsnbset, _mbsnbset_l
ms.date: 11/04/2016
apiname:
- _mbsnbset
- _mbsnbset_l
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
ms.openlocfilehash: 4c0f053cde32d71e4864c442b761606bb56c8829
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331288"
---
# <a name="mbsnbset-mbsnbsetl"></a>_mbsnbset, _mbsnbset_l

Ustawia pierwszy **n** bajtów ciąg znaków wielobajtowych do określonego znaku. Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [_mbsnbset_s —, _mbsnbset_s_l —](mbsnbset-s-mbsnbset-s-l.md).

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*str*<br/>
Ciąg, który ma zostać zmodyfikowana.

*c*<br/>
Ustawienie jednobajtowych lub znaków wielobajtowych.

*Liczba*<br/>
Liczba bajtów do ustawienia.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_mbsnbset —** zwraca wskaźnik do zmienionego ciągu.

## <a name="remarks"></a>Uwagi

**_Mbsnbset —** i **_mbsnbset_l —** funkcje ustawiają, co najwyżej, pierwsze *liczba* bajtów *str* do *c*. Jeśli *liczba* jest większa niż długość *str*, długość *str* jest używana zamiast *liczba*. Jeśli *c* jest znakiem wielobajtowym i nie może być wyłącznie ustawiony jako ostatni bajt określony przez *liczba*, ostatni bajt jest uzupełniany pustym znakiem. **_mbsnbset —** i **_mbsnbset_l —** nie umieszczają kończącego znaku null na końcu *str*.

**_mbsnbset —** i **_mbsnbset_l —** przypomina **_mbsnset —**, z tą różnicą, że ustawia *liczba* bajtów zamiast *liczba* znaki *c*.

Jeśli *str* jest **NULL** lub *liczba* wynosi zero, funkcja ta wytwarza wyjątek nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** a funkcja zwraca **NULL**. Ponadto jeśli *c* nie jest prawidłowym znakiem wielobajtowym **errno** ustawiono **EINVAL** i spacja jest używana w zamian.

Wartość wyjściowa jest zależna od ustawienia **LC_CTYPE** ustawienia kategorii ustawień regionalnych; zobacz [setlocale](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. **_Mbsnbset —** wersja tej funkcji używa bieżących ustawień regionalnych dla wszelkich zachowań; **_mbsnbset_l —** wersja jest identyczna, z tą różnicą, że korzysta z parametru ustawień regionalnych przekazanych w zamian. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

**Uwaga dotycząca zabezpieczeń** ten interfejs API wiąże potencjalnym zagrożeniem spowodowanym ulepszonym problem przepełnienia buforu. Problemy z przepełnieniem buforu są częstą metodą ataku systemu, co nieuzasadnione podniesienie poziomu uprawnień. Aby uzyskać więcej informacji, zobacz [unikanie przepełnień bufora](/windows/desktop/SecBP/avoiding-buffer-overruns).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnset —**|**_strnset**|**_mbsnbset**|**_wcsnset**|
|**_tcsnset_l**|**_strnset_l**|**_mbsnbset_l**|**_wcsnset_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbsnbset**|\<mbstring.h>|
|**_mbsnbset_l**|\<mbstring.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
