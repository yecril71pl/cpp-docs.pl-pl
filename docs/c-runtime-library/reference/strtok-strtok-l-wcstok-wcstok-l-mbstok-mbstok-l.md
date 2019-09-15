---
title: strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l
ms.date: 03/25/2019
api_name:
- _mbstok_l
- _mbstok
- wcstok
- _mbstok
- strtok
- _wcstok_l
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
ms.openlocfilehash: 62ed9edc6ec5a7ee60223f1c5e908aa14f421a25
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957653"
---
# <a name="strtok-_strtok_l-wcstok-_wcstok_l-_mbstok-_mbstok_l"></a>strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l

Znajduje następny token w ciągu, przy użyciu bieżących ustawień regionalnych lub określonych ustawień regionalnych, które są przesyłane. Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l](strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md).

> [!IMPORTANT]
> **_mbstok** i **_mbstok_l** nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*strToken*<br/>
Ciąg zawierający token lub tokeny.

*strDelimit*<br/>
Zbiór znaków ogranicznika.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do następnego tokenu znalezionego w *strToken*. Funkcje zwracają **wartość null** , jeśli nie znaleziono więcej tokenów. Każde wywołanie modyfikuje *strToken* przez podstawianie znaku null dla pierwszego ogranicznika, który występuje po zwróconym tokenie.

## <a name="remarks"></a>Uwagi

Funkcja **strtok** znajduje następny token w *strToken*. Zestaw znaków w *strDelimit* określa możliwe ograniczniki tokenu, który ma być znaleziony w *strToken* dla bieżącego wywołania. **wcstok** i **_mbstok** są wersjami znaków dwubajtowych i znakami wieloznacznymi **strtok**. Argumenty i wartość zwracana przez **wcstok** są ciągami znaków dwubajtowych; te z **_mbstok** są ciągami znaków wielobajtowych. Te trzy funkcje zachowują się identycznie w inny sposób.

> [!IMPORTANT]
> Te funkcje powodują potencjalne zagrożenie spowodowane przez problem z przepełnieniem buforu. Problemy związane z przepełnieniem buforu są częstą metodą ataku systemu, powodując nieuzasadnione podniesienie uprawnień. Aby uzyskać więcej informacji, zobacz [unikanie przekroczeń buforu](/windows/win32/SecBP/avoiding-buffer-overruns).

Przy pierwszym wywołaniu funkcji **strtok**funkcja pomija wiodące ograniczniki i zwraca wskaźnik do pierwszego tokenu w *strToken*, kończąc token ze znakiem null. Więcej tokenów można rozbić z pozostałej części *strToken* przez serię wywołań do **strtok**. Każde wywołanie **strtok** modyfikuje *strToken* , wstawiając znak null po **tokenie** zwróconym przez to wywołanie. Aby odczytać następny token z *strToken*, wywołaj **strtok** z wartością **null** dla argumentu *strToken* . Argument **null** *strToken* powoduje, że **strtok** szuka następnego tokenu w zmodyfikowanym *strToken*. Argument *strDelimit* może przyjmować dowolną wartość z jednego wywołania do następnego, aby zestaw ograniczników mógł się różnić.

Wartość wyjściowa jest zależna od ustawienia ustawienia kategorii **LC_CTYPE** ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [setlocale](setlocale-wsetlocale.md).

Wersje tych funkcji bez sufiksu **_l** używają bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych. Wersje z sufiksem **_l** są identyczne, z tą różnicą, że w zamian korzystają z przekazaną parametrem ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

> [!NOTE]
> Każda funkcja używa statycznej zmiennej lokalnej do analizowania ciągu w tokenach. W związku z tym wiele wątków może jednocześnie wywoływać te funkcje bez niepożądanych efektów. Jednak w pojedynczym wątku, przechodzące wywołania jednej z tych funkcji bardzo prawdopodobnie spowodują uszkodzenie danych i niedokładne wyniki. Podczas analizowania różnych ciągów Zakończ analizowanie jednego ciągu przed rozpoczęciem analizy następnego. Należy również pamiętać o potencjalnym zagrożeniu podczas wywoływania jednej z tych funkcji z wewnątrz pętli, w której wywoływana jest inna funkcja. Jeśli druga funkcja zostanie zakończona przy użyciu jednej z tych funkcji, zostanie wykryta sekwencja wywołań, która spowoduje wyzwolenie uszkodzenia danych.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstok**|**strtok**|**_mbstok**|**wcstok**|
|**_tcstok**|**_strtok_l**|**_mbstok_l**|**_wcstok_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtok**|\<string.h>|
|**wcstok**|\<ciąg. h > lub \<WCHAR. h >|
|**_mbstok**, **_mbstok_l**|\<mbstring.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
