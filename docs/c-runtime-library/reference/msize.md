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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: cc8eef0d28f649340715edbf4b1ebdfea85c2ff2
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914608"
---
# <a name="_msize"></a>_msize

Zwraca rozmiar bloku pamięci przydzieloną w stercie.

## <a name="syntax"></a>Składnia

```C
size_t _msize(
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Wskaźnik do bloku pamięci.

## <a name="return-value"></a>Wartość zwracana

**_msize** zwraca rozmiar (w bajtach) jako liczbę całkowitą bez znaku.

## <a name="remarks"></a>Uwagi

Funkcja **_msize** zwraca rozmiar (w bajtach) bloku pamięci przydzielonego przez wywołanie **calloc**, **malloc**lub **realloc**.

Gdy aplikacja jest połączona z wersją debugową bibliotek uruchomieniowych C, **_msize** jest rozpoznawana jako [_msize_dbg](msize-dbg.md). Aby uzyskać więcej informacji na temat sposobu zarządzania sterty podczas procesu debugowania, zobacz [sterta debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

Ta funkcja sprawdza poprawność parametru. Jeśli *memblock* jest wskaźnikiem o wartości null, **_msize** wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli błąd jest obsługiwany, funkcja ustawia **errno** na **EINVAL** i zwraca wartość-1.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_msize**|\<malloc. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

Zobacz przykład [realloc](realloc.md).

## <a name="see-also"></a>Zobacz też

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[_expand](expand.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
