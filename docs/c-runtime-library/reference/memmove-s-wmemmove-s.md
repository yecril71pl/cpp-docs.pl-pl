---
title: memmove_s —, wmemmove_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
apitype: DLLExport
f1_keywords:
- wmemmove_s
- memmove_s
dev_langs:
- C++
helpviewer_keywords:
- wmemmove_s function
- memmove_s function
ms.assetid: a17619e4-1307-4bb0-98c6-77f8c68dab2d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 39fde456dd2e45d38bdd1b6ba8d9d7eb9811dd05
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403898"
---
# <a name="memmoves-wmemmoves"></a>memmove_s, wmemmove_s

Przenosi buforu na inny. Są to wersje [memmove —, wmemmove —](memmove-wmemmove.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Rozmiar buforu docelowego.

*src*<br/>
Obiekt źródłowy.

*Liczba*<br/>
Liczba bajtów (**memmove_s —**) ani znaków (**wmemmove_s —**) do skopiowania.

## <a name="return-value"></a>Wartość zwracana

Zero w przypadku powodzenia; Kod błędu w przypadku awarii

### <a name="error-conditions"></a>Warunki błędów

|*dest*|*numberOfElements*|*src*|Wartość zwracana|Zawartość *docelowy*|
|------------|------------------------|-----------|------------------|------------------------|
|**NULL**|wszystkie|wszystkie|**EINVAL —**|Nie zmodyfikowano|
|wszystkie|wszystkie|**NULL**|**EINVAL —**|Nie zmodyfikowano|
|wszystkie|< *Liczba*|wszystkie|**ERANGE —**|Nie zmodyfikowano|

## <a name="remarks"></a>Uwagi

Kopie *liczba* bajtów znaków z *src* do *dest*. Jeśli nakładają się pewnych regionach obszar źródłowy i docelowy, **memmove_s —** gwarantuje, że oryginalne źródło bajty nakładających się są kopiowane przed zastąpieniem.

Jeśli *dest* lub, jeśli *src* jest wskaźnika o wartości null, lub jeśli ciągu docelowego jest zbyt mały, te funkcje wywołanie program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md) . Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracają **einval —** i ustaw **errno** do **einval —**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**memmove_s —**|\<string.h>|
|**wmemmove_s —**|\<WChar.h >|

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
