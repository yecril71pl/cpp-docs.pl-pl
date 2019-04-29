---
title: _setmaxstdio
ms.date: 11/04/2016
apiname:
- _setmaxstdio
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- setmaxstdio
- _setmaxstdio
helpviewer_keywords:
- maximum open files
- _setmaxstdio function
- setmaxstdio function
- open files, maximum
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
ms.openlocfilehash: 58cffedf673e23a69c2d8040071b2e3353ff4502
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356345"
---
# <a name="setmaxstdio"></a>_setmaxstdio

Ustawia maksymalną liczbę jednocześnie otwarte pliki na **stdio —** poziom.

## <a name="syntax"></a>Składnia

```C
int _setmaxstdio(
   int newmax
);
```

### <a name="parameters"></a>Parametry

*newmax*<br/>
Nowe maksymalną liczbę jednocześnie otwarte pliki na **stdio —** poziom.

## <a name="return-value"></a>Wartość zwracana

Zwraca *newmax* w przypadku powodzenia; w przeciwnym razie -1.

Jeśli *newmax* jest mniejsza niż **_IOB_ENTRIES** lub nowszej, a następnie maksymalną liczbę uchwytów dostępne w systemie operacyjnym, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [ Walidacja parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja zwraca wartość -1 i ustawia **errno** do **EINVAL**.

Aby uzyskać informacje na temat tych i innych kodów błędu, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Setmaxstdio —** funkcji zmienia wartość maksymalna liczba plików, które mogą być jednocześnie otwarty na **stdio —** poziom.

Operacje We/Wy dla środowiska wykonawczego języka C obsługuje teraz wielu bardziej otwarte pliki na platformach Win32 niż w poprzednich wersjach. Maksymalnie 2048 pliki można otworzyć jednocześnie na [lowio poziom](../../c-runtime-library/low-level-i-o.md) (czyli otwarte i dostępne poprzez **_otwórz**, **_przeczytaj**, **_write**itd rodzinnych funkcji we/wy). Maksymalnie 512 pliki można otworzyć jednocześnie na [stdio — poziom](../../c-runtime-library/stream-i-o.md) (czyli otwarte i dostępne poprzez **fopen —**, **fgetc —**, **fputc** itd rodziny funkcji). Limit równy 512 otwarte pliki na **stdio —** można zwiększyć poziom maksymalnie 2048 przez **_setmaxstdio —** funkcji.

Ponieważ **stdio —**— poziom funkcji, takich jak **fopen —**, są tworzone w górnej części **lowio** funkcje, maksymalnie 2048 jest sztywnego, górnego limitu liczby jednocześnie Otwórz pliki dostępne za pośrednictwem biblioteki wykonawczej C.

> [!NOTE]
> Ta górny limit może być poza to, co jest obsługiwane przez określonej platformy Win32 i konfigurację.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_setmaxstdio**|\<stdio.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz [_getmaxstdio —](getmaxstdio.md) na przykład za pomocą **_setmaxstdio —**.

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
