---
title: strstr, wcsstr, _mbsstr, _mbsstr_l
ms.date: 11/04/2016
apiname:
- _mbsstr
- wcsstr
- _mbsstr_l
- strstr
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _fstrstr
- _ftcsstr
- strstr
- wcsstr
- _mbsstr
- _tcsstr
helpviewer_keywords:
- strings [C++], searching
- mbsstr function
- _ftcsstr function
- ftcsstr function
- fstrstr function
- _tcsstr function
- substrings, finding
- mbsstr_l function
- tcsstr function
- _mbsstr function
- wcsstr function
- _fstrstr function
- _mbsstr_l function
- strstr function
ms.assetid: 03d70c3f-2473-45cb-a5f8-b35beeb2748a
ms.openlocfilehash: 42e02473e062c3af9524ed432aa163b7574342de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541066"
---
# <a name="strstr-wcsstr-mbsstr-mbsstrl"></a>strstr, wcsstr, _mbsstr, _mbsstr_l

Zwraca wskaźnik do pierwszego wystąpienia wyszukiwanego ciągu w ciągu.

> [!IMPORTANT]
> `_mbsstr` i `_mbsstr_l` nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
char *strstr(
   const char *str,
   const char *strSearch
); // C only
char *strstr(
   char *str,
   const char *strSearch
); // C++ only
const char *strstr(
   const char *str,
   const char *strSearch
); // C++ only
wchar_t *wcsstr(
   const wchar_t *str,
   const wchar_t *strSearch
); // C only
wchar_t *wcsstr(
   wchar_t *str,
   const wchar_t *strSearch
); // C++ only
const wchar_t *wcsstr(
   const wchar_t *str,
   const wchar_t *strSearch
); // C++ only
unsigned char *_mbsstr(
   const unsigned char *str,
   const unsigned char *strSearch
); // C only
unsigned char *_mbsstr(
   unsigned char *str,
   const unsigned char *strSearch
); // C++ only
const unsigned char *_mbsstr(
   const unsigned char *str,
   const unsigned char *strSearch
); // C++ only
unsigned char *_mbsstr_l(
   const unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C only
unsigned char *_mbsstr_l(
   unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C++ only
const unsigned char *_mbsstr_l(
   const unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*str*<br/>
Ciąg zakończony wartością null do wyszukania.

*strSearch*<br/>
Ciąg zakończony wartością null do wyszukania.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do pierwszego wystąpienia *strSearch* w *str*, lub wartość NULL, jeśli *strSearch* nie jest widoczna w *str*. Jeśli *strSearch* wskazuje ciąg o zerowej długości, funkcja zwraca *str*.

## <a name="remarks"></a>Uwagi

`strstr` Funkcja zwraca wskaźnik do pierwszego wystąpienia *strSearch* w *str*. Wyszukiwanie nie obejmuje kończących się pustych znaków. `wcsstr` jest wersją znaków dwubajtowych `strstr` i `_mbsstr` jest wersją znaków wielobajtowych. Argumenty i wartość zwracana przez `wcsstr` są znakami dwubajtowymi ciągów; te z `_mbsstr` są ciągami znaków wielobajtowych. `_mbsstr` sprawdza poprawność parametrów. Jeśli *str* lub *strSearch* ma wartość NULL, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, `_mbsstr` ustawia `errno` EINVAL i zwraca wartość 0. `strstr` i `wcsstr` nie sprawdzają poprawność swoich parametrów. Te trzy funkcje zachowują się identycznie.

> [!IMPORTANT]
> Te funkcje mogą zostać naliczone zagrożenie z problemem przepełnienia buforu. Problemy z przepełnieniem buforu może służyć do ataków systemu, ponieważ umożliwiają one wykonywanie dowolnego kodu, co może spowodować nieuzasadnione podniesienie poziomu uprawnień. Aby uzyskać więcej informacji, zobacz [unikanie przepełnień bufora](/windows/desktop/SecBP/avoiding-buffer-overruns).

W języku C, te funkcje biorą **const** wskaźnik dla pierwszego argumentu. W języku C++ dostępne są dwa przeciążenia. Przeciążenia, które przyjmuje wskaźnik do **const** zwraca wskaźnik do **const**; wersja, która przyjmuje wskaźnik do non -**const** zwraca wskaźnik do non - **Const**. _CRT_CONST_CORRECT_OVERLOADS — makro jest zdefiniowany, jeśli oba **const** i innych niż-**const** wersje tych funkcji są dostępne. Jeśli potrzebujesz non -**const** zachowanie dla obu przeciążeń C++, określ symbol _CONST_RETURN.

Wartość wyjściowa jest zależna od ustawienia kategorii ustawień regionalnych LC_CTYPE; Aby uzyskać więcej informacji, zobacz [setlocale, _wsetlocale](setlocale-wsetlocale.md). Wersje tych funkcji, które nie mają **_l** sufiks używają bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych; wersje, które mają **_l** sufiksem są identyczne, z tą różnicą, że używają w zamian parametru ustawień regionalnych, które zostały przekazane. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcsstr`|`strstr`|`_mbsstr`|`wcsstr`|
|**n/d**|**n/d**|`_mbsstr_l`|**n/d**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`strstr`|\<string.h>|
|`wcsstr`|\<Włącz String.h > lub \<wchar.h >|
|`_mbsstr`, `_mbsstr_l`|\<mbstring.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_strstr.c

#include <string.h>
#include <stdio.h>

char str[] =    "lazy";
char string[] = "The quick brown dog jumps over the lazy fox";
char fmt1[] =   "         1         2         3         4         5";
char fmt2[] =   "12345678901234567890123456789012345678901234567890";

int main( void )
{
   char *pdest;
   int  result;
   printf( "String to be searched:\n   %s\n", string );
   printf( "   %s\n   %s\n\n", fmt1, fmt2 );
   pdest = strstr( string, str );
   result = (int)(pdest - string + 1);
   if ( pdest != NULL )
      printf( "%s found at position %d\n", str, result );
   else
      printf( "%s not found\n", str );
}
```

```Output
String to be searched:
   The quick brown dog jumps over the lazy fox
            1         2         3         4         5
   12345678901234567890123456789012345678901234567890

lazy found at position 36
```

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[basic_string::find](../../standard-library/basic-string-class.md#find)<br/>
