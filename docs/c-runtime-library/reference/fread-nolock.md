---
title: _fread_nolock
ms.date: 11/04/2016
apiname:
- _fread_nolock
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
- _fread_nolock
- fread_nolock
helpviewer_keywords:
- reading data [C++], from input streams
- data [C++], reading from input stream
- fread_nolock function
- _fread_nolock function
- streams [C++], reading data from
ms.assetid: 60e4958b-1097-46f5-a77b-94af5e7dba40
ms.openlocfilehash: 81827363d670c7cdeeddcb86390323bf431c6f98
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597291"
---
# <a name="freadnolock"></a>_fread_nolock

Odczytuje dane ze strumienia bez blokowania inne wątki.

## <a name="syntax"></a>Składnia

```C
size_t _fread_nolock(
   void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*buffer*<br/>
Lokalizacja magazynowa danych.

*Rozmiar*<br/>
Rozmiar elementu w bajtach.

*Liczba*<br/>
Maksymalna liczba elementów, które mają być odczytywane.

*Stream*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

Zobacz [fread —](fread.md).

## <a name="remarks"></a>Uwagi

Ta funkcja jest wersji bez blokady **fread —**. Jest on identyczny **fread —** z tą różnicą, że nie jest chronione przed ingerencją przez inne wątki. Może on być szybsze, ponieważ nie są naliczane z obciążeniem związanym z blokowaniem innych wątków. Ta funkcja służy tylko w kontekstach wątków, takich jak aplikacje jednowątkowe lub gdzie zakres wywołujący już obsługuje izolację wątków.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fread_nolock**|\<stdio.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
