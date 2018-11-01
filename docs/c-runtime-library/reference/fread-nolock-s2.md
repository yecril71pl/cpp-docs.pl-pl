---
title: _fread_nolock_s2
ms.date: 11/04/2016
apiname:
- _fread_nolock_s
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
- _fread_nolock_s
- stdio/_fread_nolock_s
ms.assetid: 5badb9ab-11df-4e17-8162-30bda2a4572e
ms.openlocfilehash: 1dccbd362577e524f0455a2248d4d0f209ea6295
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580808"
---
# <a name="freadnolocks"></a>_fread_nolock_s

Odczytuje dane ze strumienia bez blokowania inne wątki. Ta wersja [fread_nolock —](fread-nolock.md) ma wzmocnienia zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
size_t _fread_nolock_s(
   void *buffer,
   size_t bufferSize,
   size_t elementSize,
   size_t elementCount,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*buffer*<br/>
Lokalizacja magazynowa danych.

*BufferSize*<br/>
Rozmiar buforu miejsca docelowego w bajtach.

*elementSize*<br/>
Rozmiar elementu do odczytu w bajtach.

*elementu elementCount*<br/>
Maksymalna liczba elementów, które mają być odczytywane.

*Stream*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

Zobacz [fread_s](fread-s.md).

## <a name="remarks"></a>Uwagi

Ta funkcja jest wersji bez blokady **fread_s**. Jest on identyczny **fread_s** z tą różnicą, że nie jest chronione przed ingerencją przez inne wątki. Może on być szybsze, ponieważ nie są naliczane z obciążeniem związanym z blokowaniem innych wątków. Ta funkcja służy tylko w kontekstach wątków, takich jak aplikacje jednowątkowe lub gdzie zakres wywołujący już obsługuje izolację wątków.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fread_nolock_s**|C: \<stdio.h >; C++: \<cstdio — > lub \<stdio.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
