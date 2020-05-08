---
title: memmove_s, wmemmove_s
ms.date: 4/2/2020
api_name:
- wmemmove_s
- memmove_s
- _o_wmemmove_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wmemmove_s
- memmove_s
helpviewer_keywords:
- wmemmove_s function
- memmove_s function
ms.assetid: a17619e4-1307-4bb0-98c6-77f8c68dab2d
ms.openlocfilehash: 04f920543c4f6a3d433e6426a96d617a3608a270
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914095"
---
# <a name="memmove_s-wmemmove_s"></a>memmove_s, wmemmove_s

Przenosi jeden bufor do innego. Są to wersje [memmove, wmemmove](memmove-wmemmove.md) z ulepszeniami zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*liczbą*<br/>
Liczba bajtów (**memmove_s**) lub znaków (**wmemmove_s**) do skopiowania.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli pomyślne; kod błędu w przypadku niepowodzenia

### <a name="error-conditions"></a>Warunki błędów

|*dest*|*numberOfElements*|*src*|Wartość zwracana|Zawartość miejsca *docelowego*|
|------------|------------------------|-----------|------------------|------------------------|
|**NULL**|ile|ile|**EINVAL**|nie zmodyfikowano|
|ile|ile|**NULL**|**EINVAL**|nie zmodyfikowano|
|ile|< *liczbą*|ile|**ERANGE**|nie zmodyfikowano|

## <a name="remarks"></a>Uwagi

Kopiuje *liczbę* bajtów znaków z elementu *src* do miejsca *docelowego*. Jeśli niektóre regiony obszaru źródłowego i miejsca docelowego nakładają się na siebie, **memmove_s** zapewnia, że pierwotne bajty źródłowe w nakładanym regionie są kopiowane przed zastąpieniem.

Jeśli obiekt *docelowy* lub jeśli *src* jest wskaźnikiem typu null lub jeśli ciąg docelowy jest zbyt mały, te funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, te funkcje zwracają **EINVAL** i ustawiają **errno** na **EINVAL**.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**memmove_s**|\<> String. h|
|**wmemmove_s**|\<WCHAR. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Manipulowanie buforem](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[strcpy_s, wcscpy_s, _mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
