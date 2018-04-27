---
title: memcpy_s —, wmemcpy_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
apitype: DLLExport
f1_keywords:
- wmemcpy_s
- memcpy_s
dev_langs:
- C++
helpviewer_keywords:
- memcpy_s function
- wmemcpy_s function
ms.assetid: 5504e20a-83d9-4063-91fc-3f55f7dabe99
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5442f70e246dd8e82a6f7b3e1e78810c6d197f41
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="memcpys-wmemcpys"></a>memcpy_s, wmemcpy_s

Kopie bajty pomiędzy buforów. Są to wersje [memcpy, wmemcpy —](memcpy-wmemcpy.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Rozmiar buforu docelowego dla memcpy_s — i znaki dwubajtowe (wchar_t) dla wmemcpy_s — wyrażony w bajtach.

*src*<br/>
Bufor do skopiowania.

*Liczba*<br/>
Liczba znaków do skopiowania.

## <a name="return-value"></a>Wartość zwracana

Zero w przypadku powodzenia; błąd o kodzie błędu.

### <a name="error-conditions"></a>Warunki błędów

|*dest*|*destSize*|*src*|*Liczba*|Wartość zwracana|Zawartość *docelowy*|
|------------|----------------|-----------|---|------------------|------------------------|
|wszystkie|wszystkie|wszystkie|0|0|Nie zmodyfikowano|
|**NULL**|wszystkie|wszystkie|non-zero|**EINVAL —**|Nie zmodyfikowano|
|wszystkie|wszystkie|**NULL**|non-zero|**EINVAL —**|*docelowy* powoduje|
|wszystkie|< *Liczba*|wszystkie|non-zero|**ERANGE —**|*docelowy* powoduje|

## <a name="remarks"></a>Uwagi

**memcpy_s —** kopie *liczba* bajtów z *src* do *dest*; **wmemcpy_s —** kopie *liczba* znaki dwubajtowe (dwa bajty). Jeśli na źródłowym i docelowym nakładają się, zachowanie **memcpy_s —** jest niezdefiniowana. Użyj **memmove_s —** do obsługi pokrywających się obszarów.

Te funkcje walidację ich parametrów. Jeśli *liczba* jest różna od zera i *dest* lub *src* jest wskaźnika o wartości null, lub *destSize* jest mniejszy niż *liczba*, te funkcje Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracają **einval —** lub **erange —** i ustaw **errno** do wartości zwracanej.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**memcpy_s**|\<Memory.h > lub \<string.h >|
|**wmemcpy_s**|\<WChar.h >|

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
