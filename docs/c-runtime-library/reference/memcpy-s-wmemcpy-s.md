---
title: memcpy_s, wmemcpy_s
ms.date: 11/04/2016
api_name:
- memcpy_s
- wmemcpy_s
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wmemcpy_s
- memcpy_s
helpviewer_keywords:
- memcpy_s function
- wmemcpy_s function
ms.assetid: 5504e20a-83d9-4063-91fc-3f55f7dabe99
ms.openlocfilehash: 8078590df6950201ef81356ba6c28173e80572ee
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952798"
---
# <a name="memcpy_s-wmemcpy_s"></a>memcpy_s, wmemcpy_s

Kopiuje bajty między buforami. Są to wersje [memcpy, wmemcpy](memcpy-wmemcpy.md) z ulepszeniami zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t memcpy_s(
   void *dest,
   size_t destSize,
   const void *src,
   size_t count
);
errno_t wmemcpy_s(
   wchar_t *dest,
   size_t destSize,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>Parametry

*dest*<br/>
Nowy bufor.

*destSize*<br/>
Rozmiar buforu docelowego (w bajtach) dla memcpy_s i znaków wide (wchar_t) dla wmemcpy_s.

*SRC*<br/>
Bufor do skopiowania.

*liczbą*<br/>
Liczba znaków do skopiowania.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli pomyślne; kod błędu w przypadku niepowodzenia.

### <a name="error-conditions"></a>Warunki błędów

|*dest*|*destSize*|*SRC*|*liczbą*|Wartość zwracana|Zawartość miejsca *docelowego*|
|------------|----------------|-----------|---|------------------|------------------------|
|Ile|Ile|Ile|0|0|nie zmodyfikowano|
|**NULL**|Ile|Ile|non-zero|**EINVAL**|nie zmodyfikowano|
|Ile|Ile|**NULL**|non-zero|**EINVAL**|wartość *docelowy* jest zerowa|
|Ile|< *liczbą*|Ile|non-zero|**ERANGE**|wartość *docelowy* jest zerowa|

## <a name="remarks"></a>Uwagi

**memcpy_s** kopiuje *liczbę* bajtów z *src* do miejsca *docelowego*; **wmemcpy_s** kopiuje *znaki* szerokie (dwa bajty). Jeśli źródło i miejsce docelowe nakładają się na siebie, zachowanie **memcpy_s** jest niezdefiniowane. Użyj **memmove_s** , aby obsłużyć nakładające się regiony.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *Liczba* jest różna od zera, a element *docelowy* lub *src* jest wskaźnikiem o wartości null lub *destSize* jest mniejszy niż *Count*, te funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **EINVAL** lub **ERANGE** i ustawiają **errno** na wartość zwracaną.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**memcpy_s**|\<> pamięci. h > \<lub String. h|
|**wmemcpy_s**|\<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_memcpy_s.c
// Copy memory in a more secure way.

#include <memory.h>
#include <stdio.h>

int main()
{
   int a1[10], a2[100], i;
   errno_t err;

   // Populate a2 with squares of integers
   for (i = 0; i < 100; i++)
   {
      a2[i] = i*i;
   }

   // Tell memcpy_s to copy 10 ints (40 bytes), giving
   // the size of the a1 array (also 40 bytes).
   err = memcpy_s(a1, sizeof(a1), a2, 10 * sizeof (int) );
   if (err)
   {
      printf("Error executing memcpy_s.\n");
   }
   else
   {
     for (i = 0; i < 10; i++)
       printf("%d ", a1[i]);
   }
   printf("\n");
}
```

```Output
0 1 4 9 16 25 36 49 64 81
```

## <a name="see-also"></a>Zobacz także

[Manipulowanie buforem](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memmove, wmemmove](memmove-wmemmove.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
