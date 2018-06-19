---
title: strtok —, _strtok_l —, wcstok —, _wcstok_l —, _mbstok —, _mbstok_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbstok_l
- _mbstok
- wcstok
- _mbstok
- strtok
- _wcstok_l
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
- _mbstok
- strtok
- _tcstok
- wcstok
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 45e2155f830a302f316aa96ce41b65a71709bc0d
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451800"
---
# <a name="strtok-strtokl-wcstok-wcstokl-mbstok-mbstokl"></a>strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l

Znajduje następny token w ciągu, używając bieżących ustawień regionalnych lub określone ustawienia regionalne, który jest przekazywany w. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [strtok_s —, _strtok_s_l —, wcstok_s —, _wcstok_s_l —, _mbstok_s —, _mbstok_s_l —](strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md).

> [!IMPORTANT]
> **_mbstok —** i **_mbstok_l —** nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
char *strtok(
   char *strToken,
   const char *strDelimit
);
wchar_t *wcstok(
   wchar_t *strToken,
   const wchar_t *strDelimit
);
unsigned char *_mbstok(
   unsigned char*strToken,
   const unsigned char *strDelimit
);
unsigned char *_mbstok(
   unsigned char*strToken,
   const unsigned char *strDelimit,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*strToken*<br/>
Ciąg zawierający token lub tokeny.

*strDelimit*<br/>
Zestaw znaków ogranicznika.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do następnego tokenu w *strToken*. Zwracają **NULL** gdy znajdują się żadnych kolejnych tokenów. Każde wywołanie modyfikuje *strToken* podstawiając znak null dla pierwszego ogranicznika występujący po zwrócony tokenu.

## <a name="remarks"></a>Uwagi

**Strtok —** funkcja znajduje następny token w *strToken*. Zestaw znaków *strDelimit* określa możliwe ograniczniki tokenu, który ma zostać odnaleziona w *strToken* w bieżącym wywołaniu. **wcstok —** i **_mbstok —** znaków dwubajtowych i znaków wielobajtowych wersji **strtok —**. Argumenty i zwracana wartość **wcstok —** są znaków dwubajtowych ciągi; tych **_mbstok —** są ciągami znaków wielobajtowych. Te trzy funkcje działają tak samo w przeciwnym razie wartość.

> [!IMPORTANT]
> Te funkcje pociągnąć za sobą potencjalne zagrożenie wynikające z problem przepełnienie buforu. Przepełnienie buforu problemy używanej metody ataku systemu, co powoduje nieuzasadnione podniesienie uprawnień. Aby uzyskać więcej informacji, zobacz [unikanie Overruns buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795).

W pierwszym wywołaniu **strtok —**, funkcja pomija ograniczniki początkowych i zwraca wskaźnik do pierwszym tokenie w *strToken*, przerywanie token znakiem null. Więcej tokenów mogą być podzielone poza pozostałej części *strToken* serii wywołań **strtok —**. Każde wywołanie **strtok —** modyfikuje *strToken* wstawiając znak null po **tokenu** zwracanych przez tego wywołania. Można odczytać następnego tokenu z *strToken*, wywołaj **strtok —** z **NULL** wartość *strToken* argumentu. **NULL** *strToken* powoduje, że argument **strtok —** aby wyszukać następny token w modyfikacji *strToken*. *StrDelimit* argument może zająć dowolną wartość z jednego wywołania do następnego tak, aby zestaw ograniczników może się różnić.

Wartość wyjściowa jest zagrożony ustawienie **lc_ctype —** ustawienie kategorii ustawień regionalnych; zobacz [setlocale](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji bez **_l** Użyj sufiksu bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych; wersje z **_l** sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych Przekazano zamiast tego. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

> [!NOTE]
> Każdej funkcji używa statycznego zmiennej lokalnej wątku do analizowania ciągu na tokeny. W związku z tym wiele wątków jednocześnie można wywoływać te funkcje bez niepożądane skutki. Jednak w jednym wątku naprzemiennego wykonywania wywołań do jednej z tych funkcji jest wysoce może powodować uszkodzenie danych i wyniki niedokładne. Podczas analizowania różne ciągi, Zakończ analizowania ciągu przed rozpoczęciem następnego przeanalizować. Ponadto należy pamiętać o potencjalnych zagrożeń podczas wywoływania jednej z tych funkcji w pętli, gdzie jest wywoływany inną funkcję. Innych funkcji kończy się przy użyciu jednej z tych funkcji, przeplotem sekwencję wywołań spowoduje, wyzwalania uszkodzenie danych.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstok —**|**strtok**|**_mbstok**|**wcstok**|
|**_tcstok —**|**_strtok_l**|**_mbstok_l**|**_wcstok_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtok**|\<string.h>|
|**wcstok**|\<String.h > lub \<wchar.h >|
|**_mbstok —**, **_mbstok_l —**|\<mbstring.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
