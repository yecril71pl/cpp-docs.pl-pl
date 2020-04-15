---
title: strstr, wcsstr, _mbsstr, _mbsstr_l
ms.date: 4/2/2020
api_name:
- _mbsstr
- wcsstr
- _mbsstr_l
- strstr
- _o__mbsstr
- _o__mbsstr_l
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 06fb79ac050f4e1c357a76a782730cd72cbdadec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316947"
---
# <a name="strstr-wcsstr-_mbsstr-_mbsstr_l"></a>strstr, wcsstr, _mbsstr, _mbsstr_l

Zwraca wskaźnik do pierwszego wystąpienia ciągu wyszukiwania w ciągu.

> [!IMPORTANT]
> `_mbsstr`i `_mbsstr_l` nie może być używany w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Str*<br/>
Ciąg zakończony wartością null do wyszukiwania.

*strSzukaj*<br/>
Ciąg zakończony wartością null do wyszukania.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do pierwszego wystąpienia *strSearch* w *str*lub NULL, jeśli *strSearch* nie pojawia się w *str*. Jeśli *strSearch* wskazuje na ciąg zerowej długości, funkcja zwraca *str*.

## <a name="remarks"></a>Uwagi

Funkcja `strstr` zwraca wskaźnik do pierwszego wystąpienia *strSearch* w *str*. Wyszukiwanie nie obejmuje zakończenia znaków null. `wcsstr`jest wersją szerokoznakową `strstr` i `_mbsstr` jest wersją wieloznakową. Argumenty i zwracana `wcsstr` wartość są ciągami znaków o szerokich znakach; są `_mbsstr` ciągami znaków wielobajtowych. `_mbsstr`sprawdza jego parametry. Jeśli *str* lub *strSearch* ma wartość NULL, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [zatwierdzeniu parametru.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, `_mbsstr` `errno` ustawia wartość EINVAL i zwraca 0. `strstr`i `wcsstr` nie weryfikują ich parametrów. Te trzy funkcje zachowują się identycznie inaczej.

> [!IMPORTANT]
> Te funkcje mogą spowodować zagrożenie z powodu problemu przepełnienia buforu. Problemy z przepełnieniem buforu mogą służyć do ataku na system, ponieważ mogą one umożliwić wykonanie dowolnego kodu, co może spowodować nieuzasadnione podniesienie uprawnień. Aby uzyskać więcej informacji, zobacz [Unikanie przekroczenia buforu](/windows/win32/SecBP/avoiding-buffer-overruns).

W języku C te funkcje przyjmują **wskaźnik const** dla pierwszego argumentu. W języku C++ dostępne są dwa przeciążenia. Przeciążenie, które ma wskaźnik **const** zwraca wskaźnik **const**; wersja, która ma wskaźnik do**non-const** zwraca wskaźnik do**non-const**. Makro _CRT_CONST_CORRECT_OVERLOADS jest zdefiniowany, jeśli dostępne są zarówno **wersje const,** jak i inne niż**const** tych funkcji. Jeśli wymagane jest zachowanie**non-const** dla obu przeciążeń C++, zdefiniuj symbol _CONST_RETURN.

Na wartość danych wyjściowych ma wpływ ustawienie kategorii ustawień regionalnych LC_CTYPE; aby uzyskać więcej informacji, zobacz [setlocale, _wsetlocale](setlocale-wsetlocale.md). Wersje tych funkcji, które nie mają sufiksu **_l,** używają bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych; wersje, które mają sufiks **_l** są identyczne, z tą różnicą, że zamiast tego używają parametru ustawień regionalnych, który jest przekazywany. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcsstr`|`strstr`|`_mbsstr`|`wcsstr`|
|**N/a**|**N/a**|`_mbsstr_l`|**N/a**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`strstr`|\<string.h>|
|`wcsstr`|\<string.h> lub \<wchar.h>|
|`_mbsstr`, `_mbsstr_l`|\<mbstring.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[basic_string::znajdź](../../standard-library/basic-string-class.md#find)<br/>
