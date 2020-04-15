---
title: strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l
ms.date: 4/2/2020
api_name:
- _mbslen
- _mbslen_l
- _mbstrlen
- wcslen
- _mbstrlen_l
- strlen
- _o__mbslen
- _o__mbslen_l
- _o__mbstrlen
- _o__mbstrlen_l
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbstrlen
- wcslen
- _tcslen
- _ftcslen
- strlen
- _mbslen
helpviewer_keywords:
- wcslen function
- string length, getting
- ftcslen function
- lengths, strings
- mbstrlen_l function
- _mbslen_l function
- _tcslen function
- mbslen_l function
- mbslen function
- _mbstrlen function
- strings [C++], getting length
- mbstrlen function
- _mbstrlen_l function
- _ftcslen function
- tcslen function
- strlen function
- _mbslen function
ms.assetid: 16462f2a-1e0f-4eb3-be55-bf1c83f374c2
ms.openlocfilehash: 0aa7c4f666936bae9602d6b2ab95a2731d9c0413
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355248"
---
# <a name="strlen-wcslen-_mbslen-_mbslen_l-_mbstrlen-_mbstrlen_l"></a>strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l

Pobiera długość ciągu, przy użyciu bieżących ustawień regionalnych lub określonych ustawień regionalnych. Dostępne są bezpieczniejsze wersje tych funkcji; [strnlen, strnlen_s, wcsnlen, wcsnlen_s, _mbsnlen, _mbsnlen_l, _mbstrnlen, _mbstrnlen_l](strnlen-strnlen-s.md)

> [!IMPORTANT]
> **_mbslen** **, _mbslen_l** **, _mbstrlen**i **_mbstrlen_l** nie mogą być używane w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
size_t strlen(
   const char *str
);
size_t wcslen(
   const wchar_t *str
);
size_t _mbslen(
   const unsigned char *str
);
size_t _mbslen_l(
   const unsigned char *str,
   _locale_t locale
);
size_t _mbstrlen(
   const char *str
);
size_t _mbstrlen_l(
   const char *str,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Ciąg zakończony zerem.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca liczbę znaków w *str*, z wyłączeniem wartości null terminala. Żadna wartość zwracana nie jest zarezerwowana w celu wskazania `((size_t)(-1))` błędu, z wyjątkiem **_mbstrlen** i **_mbstrlen_l**, które zwracają, jeśli ciąg zawiera nieprawidłowy znak wielobajtowy.

## <a name="remarks"></a>Uwagi

**strlen** interpretuje ciąg jako ciąg znaków jednobajtowych, więc jego zwracana wartość jest zawsze równa liczbie bajtów, nawet jeśli ciąg zawiera znaki wielobajtowe. **wcslen** jest szerokoznakową wersją **strlen;** argument **wcslen** jest ciągiem znaków o szerokim charakterze, a liczba znaków jest w postaci szerokiej (dwu bajtowej). **wcslen** i **strlen** zachowują się identycznie inaczej.

**Uwaga dotycząca zabezpieczeń** Te funkcje ponoszą potencjalne zagrożenie spowodowane problemem przepełnienia buforu. Problemy z przepełnieniem buforu są częstą metodą ataku systemu, co powoduje nieuzasadnione podniesienie uprawnień. Aby uzyskać więcej informacji, zobacz [Unikanie przekroczenia buforu](/windows/win32/SecBP/avoiding-buffer-overruns).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcslen**|**Strlen**|**Strlen**|**wcslen**|
|**_tcsclen**|**Strlen**|**_mbslen**|**wcslen**|
|**_tcsclen_l**|**Strlen**|**_mbslen_l**|**wcslen**|

**_mbslen** i **_mbslen_l** zwracają liczbę znaków wielobajtowych w ciągu znaków wielobajtowych, ale nie testują ważności znaków wielobajtowych. **_mbstrlen** i **_mbstrlen_l** test ważności znaków wielobajtowych i rozpoznaje sekwencje znaków wielobajtowych. Jeśli ciąg przekazany do **_mbstrlen** lub **_mbstrlen_l** zawiera nieprawidłowy znak wielobajtowy dla strony kodowej, funkcja zwraca wartość -1 i ustawia **errno** na **EILSEQ**.

Na wartość wyjściową ma wpływ ustawienie **LC_CTYPE** kategorii ustawień regionalnych; zobacz [setlocale,](setlocale-wsetlocale.md) aby uzyskać więcej informacji. Wersje tych funkcji bez sufiksu **_l** używają bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych; wersje z sufiksem **_l** są identyczne, z tą różnicą, że zamiast tego używają parametru ustawień regionalnych przekazanych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**Strlen**|\<string.h>|
|**wcslen**|\<string.h> lub \<wchar.h>|
|**_mbslen**, **_mbslen_l**|\<mbstring.h>|
|**_mbstrlen** **, _mbstrlen_l**|\<>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_strlen.c
// Determine the length of a string. For the multi-byte character
// example to work correctly, the Japanese language support for
// non-Unicode programs must be enabled by the operating system.

#include <string.h>
#include <locale.h>

int main()
{
   char* str1 = "Count.";
   wchar_t* wstr1 = L"Count.";
   char * mbstr1;
   char * locale_string;

   // strlen gives the length of single-byte character string
   printf("Length of '%s' : %d\n", str1, strlen(str1) );

   // wstrlen gives the length of a wide character string
   wprintf(L"Length of '%s' : %d\n", wstr1, wcslen(wstr1) );

   // A multibyte string: [A] [B] [C] [katakana A] [D] [\0]
   // in Code Page 932. For this example to work correctly,
   // the Japanese language support must be enabled by the
   // operating system.
   mbstr1 = "ABC" "\x83\x40" "D";

   locale_string = setlocale(LC_CTYPE, "Japanese_Japan");

   if (locale_string == NULL)
   {
      printf("Japanese locale not enabled. Exiting.\n");
      exit(1);
   }
   else
   {
      printf("Locale set to %s\n", locale_string);
   }

   // _mbslen will recognize the Japanese multibyte character if the
   // current locale used by the operating system is Japanese
   printf("Length of '%s' : %d\n", mbstr1, _mbslen(mbstr1) );

   // _mbstrlen will recognize the Japanese multibyte character
   // since the CRT locale is set to Japanese even if the OS locale
   // isnot.
   printf("Length of '%s' : %d\n", mbstr1, _mbstrlen(mbstr1) );
   printf("Bytes in '%s' : %d\n", mbstr1, strlen(mbstr1) );

}
```

```Output
Length of 'Count.' : 6
Length of 'Count.' : 6
Length of 'ABCァD' : 5
Length of 'ABCァD' : 5
Bytes in 'ABCァD' : 6
```

## <a name="see-also"></a>Zobacz też

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcoll — Funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
