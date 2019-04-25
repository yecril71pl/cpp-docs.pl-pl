---
title: strnlen — strnlen_s —, wcsnlen —, wcsnlen_s —, _mbsnlen —, _mbsnlen_l —, _mbstrnlen —, _mbstrnlen_l —
ms.date: 11/04/2016
apiname:
- wcsnlen
- strnlen_s
- _mbstrnlen
- _mbsnlen_l
- _mbstrnlen_l
- strnlen
- wcsnlen_s
- _mbsnlen
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
- ntoskrnl.exe
apitype: DLLExport
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
ms.openlocfilehash: 960d57ed8c2b1d1dbc6843932b8c76fef35c34a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209673"
---
# <a name="strnlen-strnlens-wcsnlen-wcsnlens-mbsnlen-mbsnlenl-mbstrnlen-mbstrnlenl"></a>strnlen — strnlen_s —, wcsnlen —, wcsnlen_s —, _mbsnlen —, _mbsnlen_l —, _mbstrnlen —, _mbstrnlen_l —

Pobiera długość ciągu przy użyciu bieżących ustawień regionalnych lub taki, który został przekazany w. Oto bardziej bezpieczne wersje [strlen —, wcslen —, _mbslen —, _mbslen_l —, _mbstrlen —, _mbstrlen_l —](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md).

> [!IMPORTANT]
> **_mbsnlen —**, **_mbsnlen_l —**, **_mbstrnlen —**, i **_mbstrnlen_l —** nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Ciąg zakończony wartością null.

*numberOfElements*<br/>
Rozmiar buforu ciągu.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Te funkcje zwracają liczbę znaków w ciągu, nie wliczając kończącego znaku null. Jeśli nie ma żadnych terminator o wartości null w obrębie pierwszych *numberOfElements* bajty ciągu (lub znaków dwubitowych, dla **wcsnlen —**), następnie *numberOfElements* są zwracane do wskazuje warunek błędu; ciągi zakończone wartością null mieć długości, które są ściśle mniejsza niż *numberOfElements*.

**_mbstrnlen —** i **_mbstrnlen_l —** zwracają wartość -1, jeśli ciąg zawiera nieprawidłowy znak wielobajtowy.

## <a name="remarks"></a>Uwagi

> [!NOTE]
> **strnlen —** nie jest zamiennikiem **strlen —**; **strnlen —** jest przeznaczona do użycia tylko w celu obliczania rozmiaru niezaufanych danych przychodzących w buforze znany obszar — na przykład pakiet sieciowy. **strnlen —** oblicza długość, ale nie zapoznaj się z końcem bufor przypadku niezakończony ciąg. W innych sytuacjach należy użyć **strlen —**. (To samo dotyczy **wcsnlen —**, **_mbsnlen —**, i **_mbstrnlen —**.)

Każda z tych funkcji zwraca liczbę znaków w *str*, bez uwzględniania kończącego znaku null. Jednak **strnlen —** i **strnlen_s —** zinterpretować ciąg jako ciąg znaków jednobajtowych i w związku z tym, wartość zwracana jest zawsze równa liczbie bajtów, nawet jeśli ciąg zawiera znaków wielobajtowych znaki. **wcsnlen —** i **wcsnlen_s —** są wersjami znaków dwubajtowych **strnlen —** i **strnlen_s —** odpowiednio; argumenty **wcsnlen —**  i **wcsnlen_s —** są ciągami znaków dwubajtowych i liczba znaków w jednostce znaków dwubajtowych. W przeciwnym razie **wcsnlen —** i **strnlen —** zachowują się identycznie, tak jak **strnlen_s —** i **wcsnlen_s —**.

**strnlen —**, **wcsnlen —**, i **_mbsnlen —** nie sprawdzają poprawność swoich parametrów. Jeśli *str* jest **NULL**, nastąpi naruszenie zasad dostępu.

**strnlen_s —** i **wcsnlen_s —** sprawdzają poprawność swoich parametrów. Jeśli *str* jest **NULL**, te funkcje zwracają 0.

**_mbstrnlen —** również sprawdza poprawność parametrów. Jeśli *str* jest **NULL**, lub jeśli *numberOfElements* jest większa niż **INT_MAX**, **_mbstrnlen —** generuje wyjątek nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **_mbstrnlen —** ustawia **errno** do **EINVAL** i zwraca wartość -1.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnlen**|**strnlen**|**strnlen**|**wcsnlen**|
|**_tcscnlen**|**strnlen**|**_mbsnlen**|**wcsnlen**|
|**_tcscnlen_l —**|**strnlen**|**_mbsnlen_l**|**wcsnlen**|

**_mbsnlen —** i **_mbstrnlen —** zwracają liczbę znaków wielobajtowych w ciągu znaków wielobajtowych. **_mbsnlen —** rozpoznaje sekwencje znaków wielobajtowych według stronę kodu wielobajtowego, jest obecnie w użyciu lub w zależności od ustawień regionalnych, który jest przekazywany; nie sprawdza poprawność znaków wielobajtowych. **_mbstrnlen —** sprawdza ważność znaków wielobajtowych i rozpoznaje sekwencje znaków wielobajtowych. Jeśli ciąg, który jest przekazywany do **_mbstrnlen —** zawiera nieprawidłowy znak wielobajtowy **errno** ustawiono **EILSEQ**.

Wartość wyjściowa jest zależna od ustawienia **LC_CTYPE** ustawienia kategorii ustawień regionalnych; zobacz [setlocale, _wsetlocale](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji są identyczne, z tą różnicą, że te, które nie mają **_l** sufiksa używa bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych i wersji, które mają **_l** sufiks Zamiast tego należy użyć parametru ustawień regionalnych, które zostały przekazane. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strnlen —**, **strnlen_s —**|\<string.h>|
|**wcsnlen —**, **wcsnlen_s —**|\<Włącz String.h > lub \<wchar.h >|
|**_mbsnlen**, **_mbsnlen_l**|\<mbstring.h>|
|**_mbstrnlen**, **_mbstrnlen_l**|\<stdlib.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strcoll, funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
