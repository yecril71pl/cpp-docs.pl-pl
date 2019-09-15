---
title: _fseek_nolock, _fseeki64_nolock
ms.date: 11/04/2016
api_name:
- _fseek_nolock
- _fseeki64_nolock
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
ms.openlocfilehash: c72f44b214893a6702f5da5594db7725a2f02136
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956530"
---
# <a name="_fseek_nolock-_fseeki64_nolock"></a>_fseek_nolock, _fseeki64_nolock

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

*stream*<br/>
Wskaźnik do struktury **pliku** .

*offset*<br/>
Liczba bajtów od *początku*.

*źródł*<br/>
Pozycja początkowa.

## <a name="return-value"></a>Wartość zwracana

Analogicznie jak [fseek](fseek-fseeki64.md) i [_fseeki64](fseek-fseeki64.md).

## <a name="remarks"></a>Uwagi

Te funkcje są odpowiednio nieblokowanymi wersjami [fseek](fseek-fseeki64.md) i [_fseeki64](fseek-fseeki64.md). Są one identyczne z [fseek](fseek-fseeki64.md) i [_fseeki64](fseek-fseeki64.md) , z tą różnicą, że nie są chronione przed ingerencją przez inne wątki. Te funkcje mogą być szybsze, ponieważ nie wiążą się z zablokowaniem innych wątków. Tych funkcji należy używać tylko w kontekstach bezpiecznych dla wątków, takich jak aplikacje jednowątkowe lub gdzie zakres wywoływania już obsługuje izolację wątku.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fseek_nolock**, **_fseeki64_nolock**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[ftell, _ftelli64](ftell-ftelli64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
[rewind](rewind.md)<br/>
