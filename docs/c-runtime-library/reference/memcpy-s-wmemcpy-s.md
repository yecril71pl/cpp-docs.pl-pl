---
title: memcpy_s, wmemcpy_s
ms.date: 11/04/2016
apiname:
- memcpy_s
- wmemcpy_s
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- wmemcpy_s
- memcpy_s
helpviewer_keywords:
- memcpy_s function
- wmemcpy_s function
ms.assetid: 5504e20a-83d9-4063-91fc-3f55f7dabe99
ms.openlocfilehash: 802d75307096e649df15b1864b99699fba92a3a1
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210877"
---
# <a name="memcpys-wmemcpys"></a>memcpy_s, wmemcpy_s

Kopiuje bajtów między buforów. Są to wersje [memcpy, wmemcpy —](memcpy-wmemcpy.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Bufor nowego.

*destSize*<br/>
Rozmiar buforu miejsca docelowego, w bajtach dla memcpy_s — a znaków dwubajtowych (wchar_t) dla wmemcpy_s —.

*src*<br/>
Bufor do skopiowania.

*Liczba*<br/>
Liczba znaków do skopiowania.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie; Kod błędu.

### <a name="error-conditions"></a>Warunki błędów

|*dest*|*destSize*|*src*|*Liczba*|Wartość zwracana|Zawartość *miejsca docelowego*|
|------------|----------------|-----------|---|------------------|------------------------|
|Wszystkie|Wszystkie|Wszystkie|0|0|Nie zmodyfikowano|
|**NULL**|Wszystkie|Wszystkie|non-zero|**EINVAL**|Nie zmodyfikowano|
|Wszystkie|Wszystkie|**NULL**|non-zero|**EINVAL**|*dest* jest zerowany|
|Wszystkie|< *Liczba*|Wszystkie|non-zero|**ERANGE**|*dest* jest zerowany|

## <a name="remarks"></a>Uwagi

**memcpy_s —** kopie *liczba* bajtów z *src* do *dest*; **wmemcpy_s —** kopie *liczba* znaków dwubajtowych (dwa bajty). Jeśli źródłowe i docelowe nakładają się, zachowanie **memcpy_s —** jest niezdefiniowana. Użyj **memmove_s —** do obsługi nakładających się regionów.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *liczba* jest różna od zera i *dest* lub *src* jest wskaźnikiem wartości null lub *destSize* jest mniejszy niż *liczba*, funkcje te wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **EINVAL** lub **ERANGE** i ustaw **errno** na wartość zwracaną.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**memcpy_s**|\<Memory.h > lub \<string.h >|
|**wmemcpy_s**|\<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
