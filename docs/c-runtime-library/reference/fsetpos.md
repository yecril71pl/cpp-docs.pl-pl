---
title: fsetpos
ms.date: 11/04/2016
apiname:
- fsetpos
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
- fsetpos
helpviewer_keywords:
- streams, setting position indicators
- fsetpos function
ms.assetid: 6d19ff48-1a2b-47b3-9f23-ed0a47b5a46e
ms.openlocfilehash: 9854c71e381da6ec9a75d440b9588e2476bada7c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528235"
---
# <a name="fsetpos"></a>fsetpos

Ustawia wskaźnik pozycji strumienia.

## <a name="syntax"></a>Składnia

```C
int fsetpos(
   FILE *stream,
   const fpos_t *pos
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Wskaźnik do **pliku** struktury.

*punktu sprzedaży*<br/>
Wskaźnik położenia magazynu.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia **fsetpos** zwraca wartość 0. W przypadku awarii, funkcja zwraca wartość różną od zera i ustawia **errno** do jednej z następujących manifestu stałych (zdefiniowany w numer błędu. Godz.): **EBADF**, co oznacza, że plik nie jest dostępna, albo ten obiekt, *strumienia* wskazuje nie jest prawidłowym plikiem struktury; lub **EINVAL**, co oznacza nieprawidłową wartością dla *strumienia* lub *pos* został przekazany. Jeśli podano nieprawidłowy parametr jest przekazywany w, funkcje te wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md).

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) kody powrotne — Aby uzyskać więcej informacji na temat tych i innych.

## <a name="remarks"></a>Uwagi

**Fsetpos** funkcja ustawia wskaźnik położenia pliku *strumienia* wartość *pos*, jest uzyskiwany podczas wcześniejszego wywołania **fgetpos**względem *strumienia*. Funkcja czyści wskaźnik końca pliku i cofa efekty [ungetc —](ungetc-ungetwc.md) na *strumienia*. Po wywołaniu **fsetpos**, następnej operacji na *strumienia* mogą być danych wejściowych lub wyjściowych.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fsetpos**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [fgetpos](fgetpos.md).

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[fgetpos](fgetpos.md)<br/>
