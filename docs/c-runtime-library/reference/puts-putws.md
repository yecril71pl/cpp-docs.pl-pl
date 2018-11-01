---
title: puts, _putws
ms.date: 11/04/2016
apiname:
- _putws
- puts
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
- _putts
- _putws
- puts
helpviewer_keywords:
- strings [C++], writing
- _putts function
- standard output, writing to
- putws function
- puts function
- putts function
- _putws function
ms.assetid: 32dada12-ed45-40ac-be06-3feeced9ecd6
ms.openlocfilehash: 0151d29f627a8f6b91142d619f64921333bb48f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667327"
---
# <a name="puts-putws"></a>puts, _putws

Zapisuje ciąg do **stdout**.

## <a name="syntax"></a>Składnia

```C
int puts(
   const char *str
);
int _putws(
   const wchar_t *str
);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Ciąg wyjściowy.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość nieujemną, jeśli to się powiedzie. Jeśli **umieszcza** nie powiedzie się, zwraca **EOF**; Jeśli **_putws —** nie powiedzie się, zwraca **WEOF**. Jeśli *str* jest pustym wskaźnikiem, wywoływany nieprawidłowy parametr uchwytu, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcje ustawiają **errno** do **EINVAL** i zwracają **EOF** lub **WEOF**.

Aby uzyskać informacje na temat tych i innych kodów błędu, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**Umieszcza** funkcja pisze *str* do strumienia wyjścia standardowego **stdout**, zastępując ciąg kończący znak null (\0) znakiem nowego wiersza (\n) w strumień wyjściowy.

**_putws —** jest wersją znaków dwubajtowych **umieszcza**; dwie funkcje zachowują się identycznie, jeżeli strumień jest otwarty w trybie ANSI. **umieszcza** aktualnie nie obsługuje danych wyjściowych w strumieniu UNICODE.

**_putwch** zapisuje znaki Unicode przy użyciu bieżących ustawień regionalnych konsoli.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_putts —**|**umieszcza**|**umieszcza**|**_putws**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**umieszcza**|\<stdio.h>|
|**_putws**|\<stdio.h>|

Konsola nie jest obsługiwana w aplikacjach platformy uniwersalnej Windows (UWP). Standardowe uchwyty strumienia, które są powiązane z konsolą, **stdin**, **stdout**, i **stderr**, muszą zostać przekierowane zanim funkcje środowiska wykonawczego języka C można ich używać w aplikacjach platformy UWP . Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_puts.c
// This program uses puts to write a string to stdout.

#include <stdio.h>

int main( void )
{
   puts( "Hello world from puts!" );
}
```

### <a name="output"></a>Dane wyjściowe

```Output
Hello world from puts!
```

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[fgets, fgetws](fgets-fgetws.md)<br/>
