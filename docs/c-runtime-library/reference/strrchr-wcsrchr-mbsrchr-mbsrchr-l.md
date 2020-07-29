---
title: strrchr, wcsrchr, _mbsrchr, _mbsrchr_l
ms.date: 4/2/2020
api_name:
- strrchr
- wcsrchr
- _mbsrchr
- _mbsrchr_l
- _o__mbsrchr
- _o__mbsrchr_l
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
- _tcsrchr
- _ftcsrchr
- strrchr
- wcsrchr
- _mbsrchr
helpviewer_keywords:
- _mbsrchr function
- tcsrchr function
- mbsrchr_l function
- characters [C++], scanning for
- ftcsrchr function
- _tcsrchr function
- strings [C++], scanning
- mbsrchr function
- strrchr function
- scanning strings
- wcsrchr function
- _ftcsrchr function
- _mbsrchr_l function
ms.assetid: 75cf2664-758e-49bb-bf6b-8a139cd474d2
ms.openlocfilehash: d1350cf14df0c87d57a87ad3aced35e3887b6676
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231302"
---
# <a name="strrchr-wcsrchr-_mbsrchr-_mbsrchr_l"></a>strrchr, wcsrchr, _mbsrchr, _mbsrchr_l

Skanuje ciąg dla ostatniego wystąpienia znaku.

> [!IMPORTANT]
> `_mbsrchr`i `_mbsrchr_l` nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
char *strrchr(
   const char *str,
   int c
); // C only
char *strrchr(
   char *str,
   int c
); // C++ only
const char *strrchr(
   const char *str,
   int c
); // C++ only
wchar_t *wcsrchr(
   const wchar_t *str,
   wchar_t c
); // C only
wchar_t *wcsrchr(
   wchar_t *str,
   wchar_t c
); // C++ only
const wchar_t *wcsrchr(
   const wchar_t *str,
   wchar_t c
); // C++ only
unsigned char *_mbsrchr(
   const unsigned char *str,
   unsigned int c
); // C only
unsigned char *_mbsrchr(
   unsigned char *str,
   unsigned int c
); // C++ only
const unsigned char *_mbsrchr(
   const unsigned char *str,
   unsigned int c
); // C++ only
unsigned char *_mbsrchr_l(
   const unsigned char *str,
   unsigned int c,
   _locale_t locale
); // C only
unsigned char *_mbsrchr_l(
   unsigned char *str,
   unsigned int c,
   _locale_t locale
); // C++ only
const unsigned char *_mbsrchr_l(
   const unsigned char *str,
   unsigned int c,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*str*<br/>
Ciąg zakończony znakiem null do wyszukania.

*s*<br/>
Znak, który ma zostać zlokalizowany.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do ostatniego wystąpienia *c* w *str*lub wartość null, jeśli nie można odnaleźć języka *c* .

## <a name="remarks"></a>Uwagi

`strrchr`Funkcja znajduje ostatnie wystąpienie *c* (konwertowane do **`char`** ) w *str*. Wyszukiwanie zawiera kończący znak null.

`wcsrchr`i `_mbsrchr` są wersjami znaków dwubajtowych i znakami wieloznacznymi `strrchr` . Argumenty i wartość zwracana przez `wcsrchr` są ciągami znaków `_mbsrchr` dwubajtowych; te z są ciągami znaków wieloznacznych.

W języku C te funkcje przyjmują **`const`** wskaźnik dla pierwszego argumentu. W języku C++ dostępne są dwa przeciążenia. Przeciążenie pobierające wskaźnik do **`const`** zwraca wskaźnik do **`const`** ; wersja, która przyjmuje wskaźnik do **`const`** niezwracanego wskaźnika do niebędącego elementem **`const`** . Makro _CRT_CONST_CORRECT_OVERLOADS jest zdefiniowane, jeśli **`const`** są dostępne zarówno i nie **`const`** wersje tych funkcji. Jeśli wymagane jest **`const`** zachowanie niezachowania dla obu przeciążeń C++, zdefiniuj symbol _CONST_RETURN.

`_mbsrchr`sprawdza poprawność swoich parametrów. Jeśli *str* ma wartość null, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, `errno` jest ustawione na EINVAL i `_mbsrchr` zwraca 0. `strrchr`i `wcsrchr` nie weryfikują ich parametrów. Te trzy funkcje zachowują się identycznie w inny sposób.

Wartość wyjściowa jest zależna od ustawienia ustawienia kategorii LC_CTYPE ustawień regionalnych; Aby uzyskać więcej informacji, zobacz [setlocale](setlocale-wsetlocale.md). Wersje tych funkcji bez sufiksu **_l** używają bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych. wersje z sufiksem **_l** są identyczne, z tą różnicą, że korzystają z przekazaną w zamian parametru ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcsrchr`|`strrchr`|`_mbsrchr`|`wcsrchr`|
|**nie dotyczy**|**nie dotyczy**|`_mbsrchr_l`|**nie dotyczy**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`strrchr`|\<string.h>|
|`wcsrchr`|\<string.h> lub \<wchar.h>|
|`_mbsrchr`, `_mbsrchr_l`|\<mbstring.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Aby zapoznać się z przykładem użycia `strrchr` , zobacz [strchr](strchr-wcschr-mbschr-mbschr-l.md).

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Regionalne](../../c-runtime-library/locale.md)<br/>
[Interpretacja sekwencji znaków wielobajtowych](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strchr, wcschr, _mbschr, _mbschr_l](strchr-wcschr-mbschr-mbschr-l.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
