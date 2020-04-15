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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: db4fa65fa47dfe11d7ab56ffc5feee06f2634e2a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364470"
---
# <a name="strnlen-strnlen_s-wcsnlen-wcsnlen_s-_mbsnlen-_mbsnlen_l-_mbstrnlen-_mbstrnlen_l"></a>strnlen, strnlen_s, wcsnlen, wcsnlen_s, _mbsnlen, _mbsnlen_l, _mbstrnlen, _mbstrnlen_l

Pobiera długość ciągu przy użyciu bieżących ustawień regionalnych lub jeden, który został przekazany w. Są to bezpieczniejsze wersje [strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md).

> [!IMPORTANT]
> **_mbsnlen**, **_mbsnlen_l** **, _mbstrnlen**i **_mbstrnlen_l** nie mogą być używane w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Str*<br/>
Ciąg zakończony zerem.

*liczbaOfElements*<br/>
Rozmiar buforu ciągu.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Te funkcje zwracają liczbę znaków w ciągu, nie wliczając w to kończącego się znaku null. Jeśli nie ma zerowego terminatora w obrębie pierwszego *bajtów numberOfElements* ciągu (lub znaków szerokich dla **wcsnlen),** a następnie *numberOfElements* jest zwracany, aby wskazać warunek błędu; ciągi zakończone zerem mają długości, które są ściśle mniejsze niż *numberOfElements*.

**_mbstrnlen** i **_mbstrnlen_l** zwracaj -1, jeśli ciąg zawiera nieprawidłowy znak wielobajtowy.

## <a name="remarks"></a>Uwagi

> [!NOTE]
> **strnlen** nie zastępuje **strlen;** **strnlen** jest przeznaczony do użycia tylko do obliczania rozmiaru przychodzących niezaufanych danych w buforze o znanym rozmiarze — na przykład w pakiecie sieciowym. **strnlen** oblicza długość, ale nie przechodzi poza koniec buforu, jeśli ciąg jest nieokreślony. W innych sytuacjach należy użyć **strlen**. (To samo dotyczy **wcsnlen**, **_mbsnlen**i **_mbstrnlen**.)

Każda z tych funkcji zwraca liczbę znaków w *str*, z wyłączeniem kończącego się znaku null. Jednak **strnlen** i **strnlen_s** interpretować ciąg jako ciąg znaków jednobajtowych i dlatego zwracana wartość jest zawsze równa liczbie bajtów, nawet jeśli ciąg zawiera znaki wielobajtowe. **wcsnlen** i **wcsnlen_s** są szerokoznakowymi wersjami **strnlen** i **strnlen_s** odpowiednio; argumenty dla **wcsnlen** i **wcsnlen_s** są ciągami znaków o szerokich znakach, a liczba znaków jest w jednostkach o szerokich znakach. W przeciwnym razie **wcsnlen** i **strnlen** zachowują się identycznie, podobnie jak **strnlen_s** i **wcsnlen_s**.

**strnlen**, **wcsnlen**i **_mbsnlen** nie weryfikują swoich parametrów. Jeśli *str* ma **wartość NULL**, występuje naruszenie zasad dostępu.

**strnlen_s** i **wcsnlen_s** zweryfikować swoje parametry. Jeśli *str* ma **wartość NULL**, funkcje zwracają 0.

**_mbstrnlen** sprawdza również jego parametry. Jeśli *str* ma **wartość NULL**lub *liczbaElementów* jest większa niż **INT_MAX**, **_mbstrnlen** generuje nieprawidłowy wyjątek parametru, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, **_mbstrnlen** ustawia **errno** na **EINVAL** i zwraca -1.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnlen**|**strnlen**|**strnlen**|**wcsnlen**|
|**_tcscnlen**|**strnlen**|**_mbsnlen**|**wcsnlen**|
|**_tcscnlen_l**|**strnlen**|**_mbsnlen_l**|**wcsnlen**|

**_mbsnlen** i **_mbstrnlen** zwracają liczbę znaków wielobajtowych w ciągu znaków wielobajtowych. **_mbsnlen** rozpoznaje sekwencje znaków wielobajtowych zgodnie ze stroną kodową wielobajtową, która jest obecnie używana lub zgodnie z ustawieniami regionalnymi, które są przekazywane; nie sprawdza ważności znaków wielobajtowych. **_mbstrnlen** testy ważności znaków wielobajtowych i rozpoznaje sekwencje znaków wielobajtowych. Jeśli ciąg przekazany do **_mbstrnlen** zawiera nieprawidłowy znak wielobajtowy, **errno** jest ustawiony na **EILSEQ**.

Na wartość wyjściową ma wpływ ustawienie **LC_CTYPE** kategorii ustawień regionalnych; zobacz [setlocale, _wsetlocale aby](setlocale-wsetlocale.md) uzyskać więcej informacji. Wersje tych funkcji są identyczne, z tą różnicą, że te, które nie mają **sufiksu _l** używają bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych i wersji, które mają sufiks **_l** zamiast tego używają parametru ustawień regionalnych, który jest przekazywany. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strnlen**, **strnlen_s**|\<string.h>|
|**wcsnlen**, **wcsnlen_s**|\<string.h> lub \<wchar.h>|
|**_mbsnlen**, **_mbsnlen_l**|\<mbstring.h>|
|**_mbstrnlen** **, _mbstrnlen_l**|\<>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strcoll — Funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
