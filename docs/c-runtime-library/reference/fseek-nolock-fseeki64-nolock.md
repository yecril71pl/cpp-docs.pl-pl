---
title: _fseek_nolock, _fseeki64_nolock
ms.date: 11/04/2016
apiname:
- _fseek_nolock
- _fseeki64_nolock
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
- _fseek_nolock
- _fseeki64_nolock
- fseek_nolock
- fseeki64_nolock
helpviewer_keywords:
- _fseek_nolock function
- fseeki64_nolock function
- file pointers [C++], moving
- fseek_nolock function
- _fseeki64_nolock function
- seek file pointers
ms.assetid: 2dd4022e-b715-462b-b935-837561605a02
ms.openlocfilehash: 57e9a57223d6af620f4f9160923675b4873ab3ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502456"
---
# <a name="fseeknolock-fseeki64nolock"></a>_fseek_nolock, _fseeki64_nolock

Przenosi wskaźnik pliku do określonej lokalizacji.

## <a name="syntax"></a>Składnia

```C
int _fseek_nolock(
   FILE *stream,
   long offset,
   int origin
);
int _fseeki64_nolock(
   FILE *stream,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Wskaźnik do **pliku** struktury.

*offset*<br/>
Liczba bajtów z *pochodzenia*.

*Punkt początkowy*<br/>
Pozycja początkowa.

## <a name="return-value"></a>Wartość zwracana

Taki sam jak [fseek](fseek-fseeki64.md) i [_fseeki64 —](fseek-fseeki64.md), odpowiednio.

## <a name="remarks"></a>Uwagi

Te funkcje są wersji bez blokady [fseek](fseek-fseeki64.md) i [_fseeki64 —](fseek-fseeki64.md), odpowiednio. Są one takie same jak [fseek](fseek-fseeki64.md) i [_fseeki64 —](fseek-fseeki64.md) z tą różnicą, że nie są chronione przed ingerencją przez inne wątki. Funkcje te mogą być szybsze, ponieważ nie wiążą się z obciążeniem związanym z blokowaniem innych wątków. Za pomocą tych funkcji tylko w kontekstach wątków, takich jak aplikacje jednowątkowe lub gdzie zakres wywołujący już obsługuje izolację wątków.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fseek_nolock —**, **_fseeki64_nolock —**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[ftell, _ftelli64](ftell-ftelli64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
[rewind](rewind.md)<br/>
