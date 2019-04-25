---
title: strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l
ms.date: 03/25/2019
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
ms.openlocfilehash: 22dd01a0b2558c83ca1e25875a2ace7dd4ee15c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62176190"
---
# <a name="strtok-strtokl-wcstok-wcstokl-mbstok-mbstokl"></a>strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l

Znajduje następny token w ciągu, przy użyciu bieżących ustawień regionalnych lub określonych ustawień regionalnych, które zostały przekazane. Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [strtok_s —, _strtok_s_l —, wcstok_s —, _wcstok_s_l —, _mbstok_s —, _mbstok_s_l —](strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md).

> [!IMPORTANT]
> **_mbstok —** i **_mbstok_l —** nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Zestaw znaków ogranicznika.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do następnego tokenu w *strToken*. Te funkcje zwracają **NULL** gdy znajdują się żadnych kolejnych tokenów. Każde wywołanie modyfikuje *strToken* , zastępując znak null w poszukiwaniu ogranicznika pierwszy, która występuje po zwrócony token.

## <a name="remarks"></a>Uwagi

**Strtok —** funkcja znajduje następny token w *strToken*. Zestaw znaków *strDelimit* określa ograniczniki możliwe tokenu, który ma zostać odnaleziona w *strToken* w bieżącym wywołaniu. **wcstok —** i **_mbstok —** są wersjami znaków dwubajtowych i znaków wielobajtowych **strtok —**. Argumenty i wartość zwracana przez **wcstok —** są znakami dwubajtowymi ciągów; te z **_mbstok —** są ciągami znaków wielobajtowych. Te trzy funkcje zachowują się identycznie.

> [!IMPORTANT]
> Te funkcje pociągnąć za sobą potencjalnym zagrożeniem spowodowanym ulepszonym problem przepełnienia buforu. Problemy z przepełnieniem buforu są częstą metodą ataku systemu, co nieuzasadnione podniesienie poziomu uprawnień. Aby uzyskać więcej informacji, zobacz [unikanie przepełnień bufora](/windows/desktop/SecBP/avoiding-buffer-overruns).

W pierwszym wywołaniu **strtok —**, funkcja pomija wiodących ograniczniki i zwraca wskaźnik do pierwszego token w *strToken*, przerywa token znakiem null. Kolejnych tokenów można zaburzyć poza pozostałą część *strToken* przez szereg wywołań do **strtok —**. Każde wywołanie **strtok —** modyfikuje *strToken* przez wstawienie znaku null po **tokenu** zwrócony przez to wywołanie. Można odczytać następnego tokenu z *strToken*, wywołaj **strtok —** z **o wartości NULL** wartość *strToken* argumentu. **NULL** *strToken* powoduje, że argument **strtok —** aby wyszukać następny token w zmodyfikowanego *strToken*. *StrDelimit* argument może przyjąć dowolną wartość z jednego wywołania do następnego tak, aby zestaw ograniczników mogą się różnić.

Wartość wyjściowa jest zależna od ustawienia **LC_CTYPE** ustawienia kategorii ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [setlocale](setlocale-wsetlocale.md).

Wersje tych funkcji, bez **_l** sufiksa używa bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych. Wersje **_l** sufiksem są identyczne, z tą różnicą, że używają parametru ustawień regionalnych przekazanych w zamian. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

> [!NOTE]
> Każda funkcja używa statycznej zmiennej lokalnej wątku do analizowania parametrów na tokeny. W związku z tym wiele wątków jednocześnie może wywołać te funkcje, bez niepożądane skutki. Jednak w ramach pojedynczego wątku z przeplotem wywołania do jednej z tych funkcji jest wysoce może powodować uszkodzenie danych i nieprecyzyjne wyniki. Podczas analizy różnych ciągów, Zakończ analizowania jednego ciągu przed przystąpieniem do następnego przeanalizować. Ponadto należy pamiętać o możliwym zagrożenia podczas wywoływania jednej z tych funkcji z w ramach pętli, gdzie jest wywoływana innej funkcji. Inne funkcje kończy się przy użyciu jednej z tych funkcji, przeplotem sekwencję wywołań spowoduje, wyzwalając uszkodzenie danych.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstok**|**strtok**|**_mbstok**|**wcstok**|
|**_tcstok**|**_strtok_l**|**_mbstok_l**|**_wcstok_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtok**|\<string.h>|
|**wcstok**|\<Włącz String.h > lub \<wchar.h >|
|**_mbstok**, **_mbstok_l**|\<mbstring.h>|

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
