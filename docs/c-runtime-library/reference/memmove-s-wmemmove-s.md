---
title: memmove_s, wmemmove_s
ms.date: 11/04/2016
apiname:
- wmemmove_s
- memmove_s
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
- wmemmove_s
- memmove_s
helpviewer_keywords:
- wmemmove_s function
- memmove_s function
ms.assetid: a17619e4-1307-4bb0-98c6-77f8c68dab2d
ms.openlocfilehash: 28d879a205790d1f132caca1022d0740e317c342
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210604"
---
# <a name="memmoves-wmemmoves"></a>memmove_s, wmemmove_s

Przenosi buforu na inny. Są to wersje [memmove, wmemmove —](memmove-wmemmove.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t memmove_s(
   void *dest,
   size_t numberOfElements,
   const void *src,
   size_t count
);
errno_t wmemmove_s(
   wchar_t *dest,
   size_t numberOfElements,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>Parametry

*dest*<br/>
Obiekt docelowy.

*numberOfElements*<br/>
Rozmiar buforu miejsca docelowego.

*src*<br/>
Obiekt źródłowy.

*Liczba*<br/>
Liczba bajtów (**memmove_s —**) ani znaków (**wmemmove_s —**) do skopiowania.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie; Kod błędu

### <a name="error-conditions"></a>Warunki błędów

|*dest*|*numberOfElements*|*src*|Wartość zwracana|Zawartość *miejsca docelowego*|
|------------|------------------------|-----------|------------------|------------------------|
|**NULL**|Wszystkie|Wszystkie|**EINVAL**|Nie zmodyfikowano|
|Wszystkie|Wszystkie|**NULL**|**EINVAL**|Nie zmodyfikowano|
|Wszystkie|< *Liczba*|Wszystkie|**ERANGE**|Nie zmodyfikowano|

## <a name="remarks"></a>Uwagi

Kopiuje *liczba* bajtów znaków ze zbioru *src* do *dest*. Jeśli niektóre regiony obszaru źródłowy i docelowy zachodziły na siebie, **memmove_s —** gwarantuje, że oryginalne źródło bajty nakładających się są kopiowane przed zastąpieniem.

Jeśli *dest* lub jeśli *src* jest wskaźnikiem typu null lub jeśli ciąg docelowy jest zbyt mały, funkcje te wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, te funkcje zwracają **EINVAL** i ustaw **errno** do **EINVAL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**memmove_s —**|\<string.h>|
|**wmemmove_s —**|\<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_memmove_s.c
//
// The program demonstrates the
// memmove_s function which works as expected
// for moving overlapping regions.

#include <stdio.h>
#include <string.h>

int main()
{
   char str[] = "0123456789";

   printf("Before: %s\n", str);

   // Move six bytes from the start of the string
   // to a new position shifted by one byte. To protect against
   // buffer overrun, the secure version of memmove requires the
   // the length of the destination string to be specified.

   memmove_s((str + 1), strnlen(str + 1, 10), str, 6);

   printf_s(" After: %s\n", str);
}
```

### <a name="output"></a>Dane wyjściowe

```Output
Before: 0123456789
After: 0012345789
```

## <a name="see-also"></a>Zobacz także

[Manipulowanie buforem](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[strcpy_s, wcscpy_s, _mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
