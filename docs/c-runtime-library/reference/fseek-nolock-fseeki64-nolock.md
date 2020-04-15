---
title: _fseek_nolock, _fseeki64_nolock
ms.date: 4/2/2020
api_name:
- _fseek_nolock
- _fseeki64_nolock
- _o__fseek_nolock
- _o__fseeki64_nolock
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 3533e7897e9c460d3be73b8907a6bd3c96f6888f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345733"
---
# <a name="_fseek_nolock-_fseeki64_nolock"></a>_fseek_nolock, _fseeki64_nolock

Przenosi wskaźnik pliku w określoną lokalizację.

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

*Strumienia*<br/>
Wskaźnik do struktury **PLIK.**

*Przesunięcie*<br/>
Liczba bajtów od *początku .*

*Pochodzenia*<br/>
Pozycja początkowa.

## <a name="return-value"></a>Wartość zwracana

Tak samo jak [fseek](fseek-fseeki64.md) i [_fseeki64](fseek-fseeki64.md), odpowiednio.

## <a name="remarks"></a>Uwagi

Funkcje te są nieblokujące wersje [fseek](fseek-fseeki64.md) i [_fseeki64](fseek-fseeki64.md), odpowiednio. Są one [identyczne z fseek](fseek-fseeki64.md) i [_fseeki64](fseek-fseeki64.md) z tą różnicą, że nie są chronione przed zakłóceniami przez inne wątki. Te funkcje mogą być szybsze, ponieważ nie ponoszą narzutu blokowania innych wątków. Użyj tych funkcji tylko w kontekstach bezpiecznych dla wątków, takich jak aplikacje jednowątkowe lub gdzie zakres wywołujący obsługuje już izolację wątku.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fseek_nolock** **, _fseeki64_nolock**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[ftell, _ftelli64](ftell-ftelli64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
[rewind](rewind.md)<br/>
