---
title: _lrotl, _lrotr
description: 'Dokumentacja interfejsu API dla _lrotl i _lrotr; co powoduje obrócenie bitów w lewo (_lrotl) lub w prawo (_lrotr). '
ms.date: 04/04/2018
api_name:
- _lrotl
- _lrotr
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
- lrotr
- lrotl
- _lrotr
- _lrotl
helpviewer_keywords:
- lrotl function
- bits
- _lrotr function
- lrotr function
- rotating bits
- _lrotl function
- bits, rotating
ms.assetid: d42f295b-35f9-49d2-9ee4-c66896ffe68e
ms.openlocfilehash: ccd14f7aa6ba3c1278063593aecee20c6789110d
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555010"
---
# <a name="_lrotl-_lrotr"></a>_lrotl, _lrotr

Powoduje obrócenie bitów w lewo (**_lrotl**) lub w prawo (**_lrotr**).

## <a name="syntax"></a>Składnia

```C
unsigned long _lrotl( unsigned long value, int shift );
unsigned long _lrotr( unsigned long value, int shift );
```

### <a name="parameters"></a>Parametry

*wartościami*<br/>
Wartość, która ma zostać obrócona.

*nocn*<br/>
Liczba bitów na *wartość*przesunięcia.

## <a name="return-value"></a>Wartość zwracana

Obie funkcje zwracają wartość obróconą. Nie ma żadnego powrotu błędu.

## <a name="remarks"></a>Uwagi

Funkcje **_lrotl** i **_lrotr** obracają *wartość* przez bity *SHIFT* . **_lrotl** obraca wartość z lewej strony w kierunku bardziej znaczących bitów. **_lrotr** obraca wartość w prawo w kierunku mniej znaczących bitów. Obie funkcje zawijają bity, obracają się z jednego końca *wartości* do drugiego.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_lrotl**, **_lrotr**|\<stdlib.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_lrot.c

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   unsigned long val = 0x0fac35791;

   printf( "0x%8.8lx rotated left eight bits is 0x%8.8lx\n",
            val, _lrotl( val, 8 ) );
   printf( "0x%8.8lx rotated right four bits is 0x%8.8lx\n",
            val, _lrotr( val, 4 ) );
}
```

```Output
0xfac35791 rotated left eight bits is 0xc35791fa
0xfac35791 rotated right four bits is 0x1fac3579
```

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[_rotl, _rotl64, _rotr, _rotr64](rotl-rotl64-rotr-rotr64.md)<br/>
