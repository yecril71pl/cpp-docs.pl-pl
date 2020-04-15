---
title: _swab
ms.date: 4/2/2020
api_name:
- _swab
- stdlib/_swab
- _o__swab
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: f7fe23cd9c1b2eab52ebe50904d0bb18fe16cea6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362956"
---
# <a name="_swab"></a>_swab

Bajty wymiany.

## <a name="syntax"></a>Składnia

```C
void _swab(
   char *src,
   char *dest,
   int n
);
```

## <a name="parameters"></a>Parametry

*src*<br/>
Dane do skopiowania i zamiany.

*Dest*<br/>
Lokalizacja magazynu dla zamienionych danych.

*N*<br/>
Liczba bajtów do skopiowania i zamiany.

## <a name="return-value"></a>Wartość zwracana

Funkcja **wacika** nie zwraca wartości. Funkcja ustawia **errno** na **EINVAL,** jeśli wskaźnik *src* lub *dest* ma wartość null lub *n* jest mniejszy niż zero, a nieprawidłowy program obsługi parametrów jest wywoływany, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md).

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr,](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) aby uzyskać więcej informacji na temat tego i innych kodów zwrotnych.

## <a name="remarks"></a>Uwagi

Jeśli *n* jest parzyste, funkcja **_swab** kopiuje *n* bajtów z *src*, zamienia każdą parę sąsiednich bajtów i przechowuje wynik w *dest*. Jeśli *n* jest nieparzyste, **_swab** kopie i zamienia pierwszy *n*-1 bajtów *src*, a końcowy bajt nie jest kopiowany. Funkcja **_swab** jest zwykle używana do przygotowywania danych binarnych do transferu do komputera, który używa innej kolejności bajtów.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_swab**|C: \<stdlib.h> C++: \<cstdlib> \<lub stdlib.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Manipulacja buforem](../../c-runtime-library/buffer-manipulation.md)<br/>
