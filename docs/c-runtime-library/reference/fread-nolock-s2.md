---
title: _fread_nolock_s2
ms.date: 4/2/2020
api_name:
- _fread_nolock_s
- _o__fread_nolock_s
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
- _fread_nolock_s
- stdio/_fread_nolock_s
ms.assetid: 5badb9ab-11df-4e17-8162-30bda2a4572e
ms.openlocfilehash: 3fb34a75a0281058a1d70ce41e1ce33b4b1bbb59
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346133"
---
# <a name="_fread_nolock_s"></a>_fread_nolock_s

Odczytuje dane ze strumienia, bez blokowania innych wątków. Ta wersja [fread_nolock](fread-nolock.md) ma ulepszenia zabezpieczeń, zgodnie z opisem w [funkcji zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Buforu*<br/>
Lokalizacja przechowywania danych.

*Buffersize*<br/>
Rozmiar buforu docelowego w bajtach.

*elementSize*<br/>
Rozmiar elementu do odczytu w bajtach.

*liczba elementów*<br/>
Maksymalna liczba elementów do odczytania.

*Strumienia*<br/>
Wskaźnik do struktury **PLIK.**

## <a name="return-value"></a>Wartość zwracana

Zobacz [fread_s](fread-s.md).

## <a name="remarks"></a>Uwagi

Ta funkcja jest nieblokującą wersją **fread_s**. Jest identyczny **z fread_s** z tą różnicą, że nie jest chroniony przed zakłóceniami przez inne wątki. Może to być szybsze, ponieważ nie ponosi obciążenie blokowania innych wątków. Tej funkcji należy używać tylko w kontekstach bezpiecznych dla wątków, takich jak aplikacje jednowątkowe lub gdy zakres wywołujący obsługuje już izolację wątku.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fread_nolock_s**|C: \<stdio.h>; C++: \<cstdio> lub \<stdio.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
