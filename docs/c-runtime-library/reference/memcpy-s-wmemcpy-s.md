---
title: memcpy_s, wmemcpy_s
ms.date: 4/2/2020
api_name:
- memcpy_s
- wmemcpy_s
- _o_memcpy_s
- _o_wmemcpy_s
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: dc5e49115b65b6883e55df13d0610231a87c1c55
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333338"
---
# <a name="memcpy_s-wmemcpy_s"></a>memcpy_s, wmemcpy_s

Kopiuje bajty między buforami. Są to wersje [memcpy, wmemcpy](memcpy-wmemcpy.md) z ulepszeniami zabezpieczeń, jak opisano w [funkcji zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Dest*<br/>
Nowy bufor.

*destSize (destSize)*<br/>
Rozmiar buforu docelowego w bajtach dla memcpy_s i znaków szerokich (wchar_t) dla wmemcpy_s.

*src*<br/>
Bufor do skopiowania.

*Liczba*<br/>
Liczba znaków do skopiowania.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie; kod błędu w przypadku awarii.

### <a name="error-conditions"></a>Warunki błędu

|*Dest*|*destSize (destSize)*|*src*|*Liczba*|Wartość zwracana|Zawartość *dest*|
|------------|----------------|-----------|---|------------------|------------------------|
|Wszelki|Wszelki|Wszelki|0|0|Nie zmodyfikowano|
|**Null**|Wszelki|Wszelki|niezerowe|**Einval**|Nie zmodyfikowano|
|Wszelki|Wszelki|**Null**|niezerowe|**Einval**|*dest* jest wyzerowany|
|Wszelki|< *Liczba*|Wszelki|niezerowe|**Układ ERANGE**|*dest* jest wyzerowany|

## <a name="remarks"></a>Uwagi

**memcpy_s** kopie *liczą* bajty od *src* do *dest;* **wmemcpy_s** kopie *zliczą* szerokie znaki (dwa bajty). Jeśli źródło i miejsce docelowe nakładają się, zachowanie **memcpy_s** jest niezdefiniowane. Użyj **memmove_s** do obsługi nakładających się regionów.

Te funkcje sprawdzają ich parametry. Jeśli *count* jest niezerowy, a *dest* lub *src* jest wskaźnikiem zerowym lub *destSize* jest mniejszy niż *count*, te funkcje wywołać nieprawidłowy program obsługi parametrów, zgodnie z opisem w sprawdzanie [poprawności parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, te funkcje zwracają **EINVAL** lub **ERANGE** i ustawić **errno** do wartości zwracanej.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**memcpy_s**|\<memory.h> lub \<string.h>|
|**wmemcpy_s**|\<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Manipulacja buforem](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memmove, wmemmove](memmove-wmemmove.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
