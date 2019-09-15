---
title: _swab
ms.date: 11/04/2016
api_name:
- _swab
- stdlib/_swab
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
- api-ms-win-crt-utility-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _swab
- stdlib/_swab
helpviewer_keywords:
- _swab function
- swapping bytes
- swab function
- bytes, swapping
ms.assetid: 017142f2-050c-4f6a-8b49-6b094f58ec94
ms.openlocfilehash: b0faba55c42023f4d66adae68de6be2c1ab009a0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946287"
---
# <a name="_swab"></a>_swab

Zamienia bajty.

## <a name="syntax"></a>Składnia

```C
void _swab(
   char *src,
   char *dest,
   int n
);
```

## <a name="parameters"></a>Parametry

*SRC*<br/>
Dane, które mają zostać skopiowane i zamienione.

*dest*<br/>
Lokalizacja magazynu dla zamienionych danych.

*n*<br/>
Liczba bajtów, które mają zostać skopiowane i zamienione.

## <a name="return-value"></a>Wartość zwracana

Funkcja **wymazania** nie zwraca wartości. Funkcja ustawia **errno** na **EINVAL** , jeśli wskaźnik *src* lub *docelowy* ma wartość null lub *n* jest mniejszy od zera i zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md).

Aby uzyskać więcej informacji na temat tego i innych kodów powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Uwagi

Jeśli *n* jest nawet, funkcja **_swab** kopiuje *n* bajtów z elementu *src*, zamienia każdą parę sąsiadujących bajtów i zapisuje wynik w miejscu *docelowego*. Jeśli *n* jest nieparzysta, **_swab** kopiuje i zamienia pierwsze *n*-1 bajty *src*, a końcowy bajt nie jest kopiowany. Funkcja **_swab** jest zwykle używana do przygotowywania danych binarnych do przesłania do komputera, który używa innej kolejności bajtów.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_swab**|C: \<STDLIB. h > C++: \<cstdlib > lub \<STDLIB. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_swab.c

#include <stdlib.h>
#include <stdio.h>

char from[] = "BADCFEHGJILKNMPORQTSVUXWZY";
char to[] =   "...........................";

int main()
{
    printf("Before: %s  %d bytes\n        %s\n\n", from, sizeof(from), to);
    _swab(from, to, sizeof(from));
    printf("After:  %s\n        %s\n\n", from, to);
}
```

```Output
Before: BADCFEHGJILKNMPORQTSVUXWZY  27 bytes
        ...........................

After:  BADCFEHGJILKNMPORQTSVUXWZY
        ABCDEFGHIJKLMNOPQRSTUVWXYZ.
```

## <a name="see-also"></a>Zobacz także

[Manipulowanie buforem](../../c-runtime-library/buffer-manipulation.md)<br/>
