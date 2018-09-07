---
title: _swab | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _swab
- stdlib/_swab
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _swab
- stdlib/_swab
dev_langs:
- C++
helpviewer_keywords:
- _swab function
- swapping bytes
- swab function
- bytes, swapping
ms.assetid: 017142f2-050c-4f6a-8b49-6b094f58ec94
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2975e63f79818e5eac430056258b72b9c6641a49
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100277"
---
# <a name="swab"></a>_swab

Zamienia bajtów.

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
Dane do skopiowania i zamienione.

*dest*<br/>
Lokalizacja magazynowa danych wymienione.

*N*<br/>
Liczba bajtów do skopiowania i zamienione.

## <a name="return-value"></a>Wartość zwracana

**Swab —** funkcja nie zwraca wartości. Zestawy funkcji **errno** do **EINVAL** Jeśli *src* lub *dest* wskaźnika ma wartość null lub *n* jest mniejsza od zera i nieprawidłowy parametr program obsługi zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md).

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na ten temat i inne kody powrotne.

## <a name="remarks"></a>Uwagi

Jeśli *n* jest parzysta, **_swab —** funkcja kopiuje *n* bajtów z *src*zamienia każdej pary bajtów sąsiadujących i zapisuje wynik w *dest*. Jeśli *n* jest nieparzysta, **_swab —** kopiuje i zamienia pierwszy *n*b-1 *src*, a bajt końcowy nie jest kopiowany. **_Swab —** funkcji jest zazwyczaj używany do przygotowania danych binarnych transferu na komputerze, który używa kolejności bajtów różne.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_swab**|C: \<stdlib.h > C++: \<cstdlib — > lub \<stdlib.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
