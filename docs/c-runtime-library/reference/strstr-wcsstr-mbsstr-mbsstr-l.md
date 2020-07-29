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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 3ac4df470e40b35257495d51c5d2d0efdb9310af
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233993"
---
# <a name="strstr-wcsstr-_mbsstr-_mbsstr_l"></a>strstr, wcsstr, _mbsstr, _mbsstr_l

Zwraca wskaźnik do pierwszego wystąpienia ciągu wyszukiwania w ciągu.

> [!IMPORTANT]
> `_mbsstr`i `_mbsstr_l` nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Ciąg zakończony znakiem null do wyszukania.

*strSearch*<br/>
Ciąg zakończony znakiem null do wyszukania.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do pierwszego wystąpienia *strSearch* w *str*lub null, jeśli *strSearch* nie pojawia się w *str*. Jeśli *strSearch* wskazuje ciąg o zerowej długości, funkcja zwraca *str*.

## <a name="remarks"></a>Uwagi

`strstr`Funkcja zwraca wskaźnik do pierwszego wystąpienia *strSearch* w *str*. Wyszukiwanie nie obejmuje kończących się pustych znaków. `wcsstr`jest wersją znaków `strstr` `_mbsstr` dwubajtowych i jest wersją znaku wieloznakówowego. Argumenty i wartość zwracana przez `wcsstr` są ciągami znaków `_mbsstr` dwubajtowych; te z są ciągami znaków wieloznacznych. `_mbsstr`sprawdza poprawność swoich parametrów. Jeśli *str* lub *strSearch* ma wartość null, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, `_mbsstr` ustawia `errno` na EINVAL i zwraca 0. `strstr`i `wcsstr` nie weryfikują ich parametrów. Te trzy funkcje zachowują się identycznie w inny sposób.

> [!IMPORTANT]
> Te funkcje mogą spowodować zagrożenie z powodu problemu z przepełnieniem buforu. Problemy z przepełnieniem buforu mogą służyć do ataku systemu, ponieważ mogą one umożliwić wykonanie dowolnego kodu, co może spowodować nieuzasadnione podniesienie uprawnień. Aby uzyskać więcej informacji, zobacz [unikanie przekroczeń buforu](/windows/win32/SecBP/avoiding-buffer-overruns).

W języku C te funkcje przyjmują **`const`** wskaźnik dla pierwszego argumentu. W języku C++ dostępne są dwa przeciążenia. Przeciążenie, które przyjmuje wskaźnik do **`const`** zwraca wskaźnik do **`const`** ; wersja, która przyjmuje wskaźnik do nie **`const`** zwraca wskaźnika do elementu niebędącego elementem **`const`** . Makro _CRT_CONST_CORRECT_OVERLOADS jest zdefiniowane, jeśli **`const`** są dostępne zarówno i nie **`const`** wersje tych funkcji. Jeśli wymagane jest **`const`** zachowanie niezachowania dla obu przeciążeń C++, zdefiniuj symbol _CONST_RETURN.

Wartość wyjściowa jest zależna od ustawienia kategorii ustawień regionalnych LC_CTYPE; Aby uzyskać więcej informacji, zobacz [setlocals, _wsetlocale](setlocale-wsetlocale.md). Wersje tych funkcji, które nie mają sufiksu **_l** używają bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych; wersje, które mają sufiks **_l** są identyczne, z tą różnicą, że zamiast tego używają parametru ustawień regionalnych, który jest przesyłany. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcsstr`|`strstr`|`_mbsstr`|`wcsstr`|
|**nie dotyczy**|**nie dotyczy**|`_mbsstr_l`|**nie dotyczy**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`strstr`|\<string.h>|
|`wcsstr`|\<string.h> lub \<wchar.h>|
|`_mbsstr`, `_mbsstr_l`|\<mbstring.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
[Regionalne](../../c-runtime-library/locale.md)<br/>
[Interpretacja sekwencji znaków wielobajtowych](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[basic_string:: find](../../standard-library/basic-string-class.md#find)<br/>
