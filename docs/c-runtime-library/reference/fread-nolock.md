---
title: _fread_nolock
ms.date: 4/2/2020
api_name:
- _fread_nolock
- _o__fread_nolock
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
- _fread_nolock
- fread_nolock
helpviewer_keywords:
- reading data [C++], from input streams
- data [C++], reading from input stream
- fread_nolock function
- _fread_nolock function
- streams [C++], reading data from
ms.assetid: 60e4958b-1097-46f5-a77b-94af5e7dba40
ms.openlocfilehash: 97b37b4fee85a827faa4b309741afe56d8d0cbb9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346093"
---
# <a name="_fread_nolock"></a>_fread_nolock

Odczytuje dane ze strumienia, bez blokowania innych wątków.

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

*Buforu*<br/>
Lokalizacja przechowywania danych.

*Rozmiar*<br/>
Rozmiar elementu w bajtach.

*Liczba*<br/>
Maksymalna liczba elementów do odczytania.

*Strumienia*<br/>
Wskaźnik do struktury **PLIK.**

## <a name="return-value"></a>Wartość zwracana

Zobacz [fread](fread.md).

## <a name="remarks"></a>Uwagi

Ta funkcja jest nieblokującą wersją **fread**. Jest identyczny **z fread,** z tą różnicą, że nie jest chroniony przed zakłóceniami przez inne wątki. Może to być szybsze, ponieważ nie ponosi obciążenie blokowania innych wątków. Tej funkcji należy używać tylko w kontekstach bezpiecznych dla wątków, takich jak aplikacje jednowątkowe lub gdy zakres wywołujący obsługuje już izolację wątku.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fread_nolock**|\<stdio.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
