---
title: strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l
ms.date: 4/2/2020
api_name:
- _mbstok_l
- _mbstok
- wcstok
- _mbstok
- strtok
- _wcstok_l
- _o__mbstok
- _o__mbstok_l
- _o_strtok
- _o_wcstok
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
- _mbstok
- strtok
- _tcstok
- wcstok
helpviewer_keywords:
- mbstok_l function
- strings [C++], searching
- tcstok function
- _tcstok function
- _strtok_l function
- strtok function
- mbstok function
- wcstok_l function
- _mbstok function
- tcstok_l function
- tokens, finding in strings
- _mbstok_l function
- wcstok function
- _wcstok_l function
- _tcstok_l function
- strtok_l function
ms.assetid: 904cb734-f0d7-4d77-ba81-4791ddf461ae
ms.openlocfilehash: d228d9824c534a21e4a22797e4b070e6d8d0b179
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365197"
---
# <a name="strtok-_strtok_l-wcstok-_wcstok_l-_mbstok-_mbstok_l"></a>strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l

Znajduje następny token w ciągu, przy użyciu bieżących ustawień regionalnych lub określonych ustawień regionalnych, które są przekazywane w. Dostępne są bezpieczniejsze wersje tych funkcji; [zobacz strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l](strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md).

> [!IMPORTANT]
> **_mbstok** i **_mbstok_l** nie mogą być używane w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
char *strtok(
   char *strToken,
   const char *strDelimit
);
char *strtok_l(
   char *strToken,
   const char *strDelimit,
   _locale_t locale
);
wchar_t *wcstok(
   wchar_t *strToken,
   const wchar_t *strDelimit
);
wchar_t *wcstok_l(
   wchar_t *strToken,
   const wchar_t *strDelimit,
   _locale_t locale
);
unsigned char *_mbstok(
   unsigned char *strToken,
   const unsigned char *strDelimit
);
unsigned char *_mbstok_l(
   unsigned char *strToken,
   const unsigned char *strDelimit,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*strToken ( strToken )*<br/>
Ciąg zawierający token lub tokeny.

*strDelimit*<br/>
Zestaw znaków ogranicznika.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do następnego tokenu znalezionego w *strToken*. Funkcje zwracają **null,** gdy nie znaleziono więcej tokenów. Każde wywołanie modyfikuje *strToken* zastępując znak null dla pierwszego ogranicznika, który występuje po zwrócony token.

## <a name="remarks"></a>Uwagi

Funkcja **strtok** znajduje następny token w *strToken*. Zestaw znaków w *strDelimit* określa możliwe ograniczniki tokenu można znaleźć w *strToken* w bieżącym wywołaniu. **wcstok** i **_mbstok** są szerokoznakowymi i wielobajtowymi znakami **strtok**. Argumenty i zwracana wartość **wcstok** są ciągami znaków o szerokich znakach; **_mbstok** są ciągami znaków wielobajtowych. Te trzy funkcje zachowują się identycznie inaczej.

> [!IMPORTANT]
> Te funkcje ponoszą potencjalne zagrożenie spowodowane problemem przepełnienia buforu. Problemy z przepełnieniem buforu są częstą metodą ataku systemu, co powoduje nieuzasadnione podniesienie uprawnień. Aby uzyskać więcej informacji, zobacz [Unikanie przekroczenia buforu](/windows/win32/SecBP/avoiding-buffer-overruns).

Przy pierwszym wywołaniu **strtok**funkcja pomija wiodące ograniczniki i zwraca wskaźnik do pierwszego tokenu w *strToken*, kończąc token znakiem zerowym. Więcej tokenów można podzielić z pozostałej części *strToken* przez serię wywołań **strtok**. Każde wywołanie **strtok** modyfikuje *strToken* przez wstawienie znaku null po **token** zwracany przez to wywołanie. Aby odczytać następny token z *strToken*, wywołać **strtok** z wartością **NULL** dla argumentu *strToken.* Argument **NULL** *strToken* powoduje, że **strtok** wyszukuje następny token w zmodyfikowanym *strToken*. *StrDelimit* argument może mieć dowolną wartość z jednego wywołania do następnego, tak aby zestaw ograniczników może się różnić.

Na wartość danych wyjściowych ma wpływ ustawienie **LC_CTYPE** kategorii ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [setlocale](setlocale-wsetlocale.md).

Wersje tych funkcji bez sufiksu **_l** używają bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych. Wersje z sufiksem **_l** są identyczne, z tą różnicą, że zamiast tego używają parametru ustawień regionalnych przekazanych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

> [!NOTE]
> Każda funkcja używa zmiennej statycznej lokalnego wątku do analizowania ciągu na tokeny. W związku z tym wiele wątków można jednocześnie wywołać te funkcje bez działań niepożądanych. Jednak w ciągu jednego wątku przeplatanie wywołań do jednej z tych funkcji jest wysoce prawdopodobne, aby spowodować uszkodzenie danych i niedokładne wyniki. Podczas analizowania różnych ciągów, należy zakończyć analizowanie jednego ciągu przed rozpoczęciem analizowania następnego. Ponadto należy pamiętać o potencjalnych niebezpieczeństwa podczas wywoływania jednej z tych funkcji z wewnątrz pętli, gdzie inna funkcja jest wywoływana. Jeśli druga funkcja kończy się przy użyciu jednej z tych funkcji, interleaved sekwencji wywołań spowoduje, wyzwalając uszkodzenie danych.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstok**|**strtok (strtok)**|**_mbstok**|**wcstok**|
|**_tcstok**|**_strtok_l**|**_mbstok_l**|**_wcstok_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtok (strtok)**|\<string.h>|
|**wcstok**|\<string.h> lub \<wchar.h>|
|**_mbstok** **, _mbstok_l**|\<mbstring.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_strtok.c
// compile with: /W3
// In this program, a loop uses strtok
// to print all the tokens (separated by commas
// or blanks) in the string named "string".
//
#include <string.h>
#include <stdio.h>

char string[] = "A string\tof ,,tokens\nand some  more tokens";
char seps[]   = " ,\t\n";
char *token;

int main( void )
{
   printf( "Tokens:\n" );

   // Establish string and get the first token:
   token = strtok( string, seps ); // C4996
   // Note: strtok is deprecated; consider using strtok_s instead
   while( token != NULL )
   {
      // While there are tokens in "string"
      printf( " %s\n", token );

      // Get next token:
      token = strtok( NULL, seps ); // C4996
   }
}
```

```Output
Tokens:
A
string
of
tokens
and
some
more
tokens
```

## <a name="see-also"></a>Zobacz też

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
