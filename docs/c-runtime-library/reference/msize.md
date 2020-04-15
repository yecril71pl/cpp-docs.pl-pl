---
title: _msize
ms.date: 4/2/2020
api_name:
- _msize
- _o__msize
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
- msize
- _msize
helpviewer_keywords:
- memory blocks
- msize function
- _msize function
ms.assetid: 02b1f89e-d0d7-4f12-938a-9eeba48a0f88
ms.openlocfilehash: 7d5f62bd6111a305c18b0ee19bb6d3e90f2ddb49
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338664"
---
# <a name="_msize"></a>_msize

Zwraca rozmiar bloku pamięci przydzielonego w stercie.

## <a name="syntax"></a>Składnia

```C
size_t _msize(
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*blok memblock*<br/>
Wskaźnik do bloku pamięci.

## <a name="return-value"></a>Wartość zwracana

**_msize** zwraca rozmiar (w bajtach) jako niepodpisaną liczbę całkowitą.

## <a name="remarks"></a>Uwagi

Funkcja **_msize** zwraca rozmiar w bajtach bloku pamięci przydzielonego przez wywołanie **calloc,** **malloc**lub **realloc**.

Gdy aplikacja jest połączona z wersją debugowania bibliotek w czasie wykonywania języka C, **_msize** jest _msize_dbg [.](msize-dbg.md) Aby uzyskać więcej informacji na temat zarządzania stertą podczas procesu debugowania, zobacz [Sterta debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

Ta funkcja sprawdza poprawność jego parametru. Jeśli *memblock* jest wskaźnikiem zerowym, **_msize** wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli błąd jest obsługiwany, funkcja ustawia **errno** na **EINVAL** i zwraca -1.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_msize**|\<> malloc.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

Zobacz przykład [realloc](realloc.md).

## <a name="see-also"></a>Zobacz też

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[_expand](expand.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
