---
title: strnlen, strnlen_s, wcsnlen, wcsnlen_s, _mbsnlen, _mbsnlen_l, _mbstrnlen, _mbstrnlen_l
ms.date: 4/2/2020
api_name:
- wcsnlen
- strnlen_s
- _mbstrnlen
- _mbsnlen_l
- _mbstrnlen_l
- strnlen
- wcsnlen_s
- _mbsnlen
- _o__mbsnlen
- _o__mbsnlen_l
- _o__mbstrnlen
- _o__mbstrnlen_l
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcsnlen
- strnlen_s
- _mbsnlen
- _mbsnlen_l
- _tcsnlen
- _tcscnlen
- _mbstrnlen_l
- wcsnlen_s
- _mbstrnlen
- strnlen
- _tcscnlen_l
helpviewer_keywords:
- _tcscnlen function
- _mbstrnlen function
- _mbsnlen_l function
- lengths, strings
- mbstrnlen function
- mbsnlen_l function
- _mbstrnlen_l function
- _tcscnlen_l function
- wcsnlen_l function
- _tcsnlen function
- _mbsnlen function
- strnlen function
- mbsnlen function
- wcsnlen_s function
- strnlen_s function
- mbstrnlen_l function
- wcsnlen function
- string length
- strnlen_l function
ms.assetid: cc05ce1c-72ea-4ae4-a7e7-4464e56e5f80
ms.openlocfilehash: be13a67d51b0296d91355c970e5e37ad227812ad
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919253"
---
# <a name="strnlen-strnlen_s-wcsnlen-wcsnlen_s-_mbsnlen-_mbsnlen_l-_mbstrnlen-_mbstrnlen_l"></a>strnlen, strnlen_s, wcsnlen, wcsnlen_s, _mbsnlen, _mbsnlen_l, _mbstrnlen, _mbstrnlen_l

Pobiera długość ciągu przy użyciu bieżących ustawień regionalnych lub jednego, który został przekazano. Są to bezpieczniejsze wersje [strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md).

> [!IMPORTANT]
> **_mbsnlen**, **_mbsnlen_l**, **_mbstrnlen**i **_mbstrnlen_l** nie mogą być używane w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
size_t strnlen(
   const char *str,
   size_t numberOfElements
);
size_t strnlen_s(
   const char *str,
   size_t numberOfElements
);
size_t wcsnlen(
   const wchar_t *str,
   size_t numberOfElements
);
size_t wcsnlen_s(
   const wchar_t *str,
   size_t numberOfElements
);
size_t _mbsnlen(
   const unsigned char *str,
   size_t numberOfElements
);
size_t _mbsnlen_l(
   const unsigned char *str,
   size_t numberOfElements,
   _locale_t locale
);
size_t _mbstrnlen(
   const char *str,
   size_t numberOfElements
);
size_t _mbstrnlen_l(
   const char *str,
   size_t numberOfElements,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Ciąg zakończony znakiem null.

*numberOfElements*<br/>
Rozmiar buforu ciągu.

*locale*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Te funkcje zwracają liczbę znaków w ciągu, bez uwzględnienia kończącego znaku null. Jeśli nie ma terminatora zerowego w ciągu pierwszych *NumberOfElements* bajtów ciągu (lub szerokich znaków dla **wcsnlen**), wówczas *NumberOfElements* jest zwracany, aby wskazać warunek błędu; ciągi zakończone wartością null mają długości, które są ściśle mniejsze niż *NumberOfElements*.

**_mbstrnlen** i **_mbstrnlen_l** Return-1, jeśli ciąg zawiera nieprawidłowy znak wielobajtowy.

## <a name="remarks"></a>Uwagi

> [!NOTE]
> **strnlen** nie zastępuje elementu **strlen**; **strnlen** jest przeznaczona do użycia tylko w celu obliczenia rozmiaru niezaufanych danych przychodzących w buforze o znanym rozmiarze, na przykład w przypadku pakietu sieciowego. **strnlen** oblicza długość, ale nie przekroczy końca buforu, jeśli ciąg jest niezakończony. W innych sytuacjach należy użyć **strlen**. (To samo dotyczy **wcsnlen**, **_mbsnlen**i **_mbstrnlen**).

Każda z tych funkcji zwraca liczbę znaków w *str*, bez uwzględniania kończącego znaku null. Jednak **strnlen** i **strnlen_s** interpretują ciąg jako jednobajtowy ciąg znaków, dlatego zwracana wartość jest zawsze równa liczbie bajtów, nawet jeśli ciąg zawiera znaki wielobajtowe. **wcsnlen** i **wcsnlen_s** są odpowiednio wersjami **strnlen** i **strnlen_s** ; argumenty dla **wcsnlen** i **wcsnlen_s** są ciągami znaków dwubajtowych, a liczba znaków w jednostkach dwubajtowych. W przeciwnym razie **wcsnlen** i **strnlen** zachowują się identycznie, jak **strnlen_s** i **wcsnlen_s**.

**strnlen**, **wcsnlen**i **_mbsnlen** nie weryfikują ich parametrów. Jeśli *str* ma **wartość null**, występuje naruszenie zasad dostępu.

**strnlen_s** i **wcsnlen_s** weryfikują ich parametry. Jeśli *str* ma **wartość null**, funkcje zwracają wartość 0.

**_mbstrnlen** również sprawdza poprawność parametrów. Jeśli *str* ma **wartość null**lub jeśli *NumberOfElements* jest większa niż **INT_MAX**, **_mbstrnlen** generuje wyjątek nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **_mbstrnlen** ustawia **errno** na **EINVAL** i zwraca wartość-1.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnlen**|**strnlen**|**strnlen**|**wcsnlen**|
|**_tcscnlen**|**strnlen**|**_mbsnlen**|**wcsnlen**|
|**_tcscnlen_l**|**strnlen**|**_mbsnlen_l**|**wcsnlen**|

**_mbsnlen** i **_mbstrnlen** zwracają liczbę znaków wielobajtowych w ciągu znaków wielobajtowych. **_mbsnlen** rozpoznaje sekwencje znaków wielobajtowych zgodnie ze stroną kodową wielobajtowego, która jest obecnie używana lub zgodnie z przekazaną ustawieniami regionalnymi; nie jest sprawdzana pod kątem ważności znaku wielobajtowego. **_mbstrnlen** testy dla ważności znaku wielobajtowego i rozpoznaje sekwencje znaków wielobajtowych. Jeśli ciąg, który jest przesyłany do **_mbstrnlen** zawiera nieprawidłowy znak wielobajtowy, **errno** jest ustawiony na **EILSEQ**.

Wartość wyjściowa jest zależna od ustawienia ustawienia kategorii **LC_CTYPE** ustawień regionalnych; Aby uzyskać więcej informacji [, zobacz setlocals, _wsetlocale](setlocale-wsetlocale.md) . Wersje tych funkcji są identyczne, z tą różnicą, że te, które nie mają sufiksu **_l** używają bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych, a wersje, które mają sufiks **_l** używają przekazaną wartość parametru ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strnlen**, **strnlen_s**|\<> String. h|
|**wcsnlen**, **wcsnlen_s**|\<ciąg. h> lub \<WCHAR. h>|
|**_mbsnlen**, **_mbsnlen_l**|\<mbstring. h>|
|**_mbstrnlen**, **_mbstrnlen_l**|\<STDLIB. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_strnlen.c

#include <string.h>

int main()
{
   // str1 is 82 characters long. str2 is 159 characters long

   char* str1 = "The length of a string is the number of characters\n"
               "excluding the terminating null.";
   char* str2 = "strnlen takes a maximum size. If the string is longer\n"
                "than the maximum size specified, the maximum size is\n"
                "returned rather than the actual size of the string.";
   size_t len;
   size_t maxsize = 100;

   len = strnlen(str1, maxsize);
   printf("%s\n Length: %d \n\n", str1, len);

   len = strnlen(str2, maxsize);
   printf("%s\n Length: %d \n", str2, len);
}
```

```Output
The length of a string is the number of characters
excluding the terminating null.
Length: 82

strnlen takes a maximum size. If the string is longer
than the maximum size specified, the maximum size is
returned rather than the actual size of the string.
Length: 100
```

## <a name="see-also"></a>Zobacz też

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Ustawienie](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strcoll — Funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
