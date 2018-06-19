---
title: _mbsnbset —, _mbsnbset_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 316580b0c5f1f46ffa9f4a49ef759b347032fc09
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404652"
---
# <a name="mbsnbset-mbsnbsetl"></a>_mbsnbset, _mbsnbset_l

Ustawia pierwszy **n** bajtów ciąg znaków wielobajtowych określony znak. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [_mbsnbset_s —, _mbsnbset_s_l —](mbsnbset-s-mbsnbset-s-l.md).

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Ciąg, który ma zostać zmienione.

*c*<br/>
Ustawienie jednobajtowe lub znaków wielobajtowych.

*Liczba*<br/>
Liczba bajtów do ustawienia.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_mbsnbset —** zwraca wskaźnik do ciągu zmieniony.

## <a name="remarks"></a>Uwagi

**_Mbsnbset —** i **_mbsnbset_l —** funkcje ustawiać co najwyżej pierwszy *liczba* bajtów *str* do *c*. Jeśli *liczba* jest większa niż długość *str*, długość *str* jest używany zamiast *liczba*. Jeśli *c* jest znaków wielobajtowych i nie można ustawić wyłącznie do ostatniego bajtu określony przez *liczby*, ostatniego bajtu jest uzupełniana znakiem puste. **_mbsnbset —** i **_mbsnbset_l —** nie umieścić kończącym wartości null na końcu *str*.

**_mbsnbset —** i **_mbsnbset_l —** jest podobny do **_mbsnset —**, z wyjątkiem tego, że ustawia *liczba* bajtów zamiast *liczba* znaki *c*.

Jeśli *str* jest **NULL** lub *liczba* wynosi zero, ta funkcja generuje wyjątek nieprawidłowy parametr zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **errno** ustawiono **einval —** i funkcja zwraca **NULL**. Ponadto jeśli *c* nie jest prawidłową znaków wielobajtowych **errno** ustawiono **einval —** i spacji zamiast niego jest używana.

Wartość wyjściowa jest zagrożony ustawienie **lc_ctype —** ustawienie kategorii ustawień regionalnych; zobacz [setlocale](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. **_Mbsnbset —** wersja tej funkcji używa bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych; **_mbsnbset_l —** wersji jest identyczny z tą różnicą, że on używać zamiast niej przekazany parametr ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

**Uwaga dotycząca zabezpieczeń** ten interfejs API ponosi potencjalne zagrożenie wynikające z problem przepełnienie buforu. Przepełnienie buforu problemy używanej metody ataku systemu, co powoduje nieuzasadnione podniesienie uprawnień. Aby uzyskać więcej informacji, zobacz [unikanie Overruns buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnset —**|**_strnset**|**_mbsnbset —**|**_wcsnset**|
|**_tcsnset_l —**|**_strnset_l**|**_mbsnbset_l**|**_wcsnset_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbsnbset —**|\<mbstring.h>|
|**_mbsnbset_l**|\<mbstring.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
