---
title: _swab | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1ab841400bd002595508806797a9a204415b5f15
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
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

*SRC* dane do skopiowania i zamienione.

*docelowy* lokalizację magazynowania danych zamienione.

*n* liczba bajtów do skopiowania i zamienione.

## <a name="return-value"></a>Wartość zwracana

**Swab —** funkcja nie zwraca wartości. Zestawy funkcji **errno** do **einval —** Jeśli *src* lub *dest* wskaźnik ma wartość null lub *n* jest mniejsza od zera i nieprawidłowy parametr zostanie wywołany program obsługi, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md).

Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na ten temat oraz inne kody powrotu.

## <a name="remarks"></a>Uwagi

Jeśli *n* jest parzysta, **_swab —** funkcji kopie *n* bajtów z *src*zamienia każda para bajtów sąsiadujących ze sobą i zapisuje wynik w *dest*. Jeśli *n* jest nieparzysta, **_swab —** kopiuje i zamienia pierwszy *n*-1 bajtów *src*, i końcowe bajtów nie zostaną skopiowane. **_Swab —** używane zwykle do przygotować dane binarne do przeniesienia do urządzenia, które używa kolejności bajtów różnych funkcji.

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
