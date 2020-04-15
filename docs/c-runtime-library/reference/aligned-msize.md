---
title: _aligned_msize
ms.date: 4/2/2020
api_name:
- _aligned_msize
- _o__aligned_msize
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _aligned_msize
- aligned_msize
helpviewer_keywords:
- aligned_msize function
- _aligned_msize function
ms.assetid: 10995edc-2110-4212-9ca9-5e0220a464f4
ms.openlocfilehash: 21ae07c90bbf9a729a212a97b7de3e0916f8e2c6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350600"
---
# <a name="_aligned_msize"></a>_aligned_msize

Zwraca rozmiar bloku pamięci przydzielonego w stercie.

## <a name="syntax"></a>Składnia

```C
size_t _msize(
   void *memblock,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Parametry

*blok memblock*<br/>
Wskaźnik do bloku pamięci.

*Wyrównanie*<br/>
Wartość wyrównania, która musi być całkowitą potęgą liczby 2.

*Przesunięcie*<br/>
Przesunięcie alokacji pamięci, aby wymusić wyrównanie.

## <a name="return-value"></a>Wartość zwracana

Zwraca rozmiar (w bajtach) jako niepodpisaną liczbę całkowitą.

## <a name="remarks"></a>Uwagi

Funkcja **_aligned_msize** zwraca rozmiar w bajtach bloku pamięci przydzielonego przez wywołanie [_aligned_malloc](aligned-malloc.md) lub [_aligned_realloc](aligned-realloc.md). *Wyrównanie* i *przesunięcie* wartości muszą być takie same jak wartości przekazywane do funkcji, która alokowała blok.

Gdy aplikacja jest połączona z wersją debugowania bibliotek w czasie wykonywania języka C, **_aligned_msize** jest _aligned_msize_dbg [.](aligned-msize-dbg.md) Aby uzyskać więcej informacji na temat zarządzania stertą podczas procesu debugowania, zobacz [Sterta debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

Ta funkcja sprawdza poprawność jego parametru. Jeśli *memblock* jest wskaźnikiem zerowym lub *wyrównanie* nie jest potęgą 2, **_msize** wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli błąd jest obsługiwany, funkcja ustawia **errno** na **EINVAL** i zwraca -1.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_msize**|\<> malloc.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz też

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
