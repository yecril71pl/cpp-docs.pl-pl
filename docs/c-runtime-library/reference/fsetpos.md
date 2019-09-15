---
title: fsetpos
ms.date: 11/04/2016
api_name:
- fsetpos
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fsetpos
helpviewer_keywords:
- streams, setting position indicators
- fsetpos function
ms.assetid: 6d19ff48-1a2b-47b3-9f23-ed0a47b5a46e
ms.openlocfilehash: f44ab1b35c9e598f82dbc0af96979476ee353541
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956522"
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

*stream*<br/>
Wskaźnik do struktury **pliku** .

*Terminal*<br/>
Miejsce — magazyn wskaźnika.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia funkcja **fsetpos** zwraca wartość 0. W przypadku niepowodzenia funkcja zwraca wartość różną od zera i ustawia **errno** na jedną z następujących stałych manifestu (zdefiniowanej w errno. H): **EBADF**, co oznacza, że plik nie jest dostępny lub obiekt, do *którego wskazuje,* że nie jest prawidłową strukturą pliku; lub **EINVAL**, co oznacza, że przekazano nieprawidłową wartość *strumienia* lub *punktu sprzedaży* . Jeśli przeszedł nieprawidłowy parametr, te funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md).

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) , aby uzyskać więcej informacji na temat tych i innych kodów powrotu.

## <a name="remarks"></a>Uwagi

Funkcja **fsetpos** ustawia wskaźnik położenia plików dla *strumienia* do wartości *punktu sprzedaży*, która jest uzyskiwana we wcześniejszej wywołaniu **fgetpos** względem *strumienia*. Funkcja czyści wskaźnik końca pliku i cofa wszystkie efekty [ungetc —](ungetc-ungetwc.md) w *strumieniu*. Po wywołaniu **fsetpos**kolejna operacja na *strumieniu* może być wartością wejściową lub wyjściową.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fsetpos**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład dla [fgetpos](fgetpos.md).

## <a name="see-also"></a>Zobacz także

[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fgetpos](fgetpos.md)<br/>
