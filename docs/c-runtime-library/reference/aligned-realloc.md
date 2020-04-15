---
title: _aligned_realloc
ms.date: 4/2/2020
api_name:
- _aligned_realloc
- _o__aligned_realloc
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
- _aligned_realloc
- aligned_realloc
helpviewer_keywords:
- aligned_realloc function
- _aligned_realloc function
ms.assetid: 80ce96e8-6087-416f-88aa-4dbb8cb1d218
ms.openlocfilehash: 8b9dfae3fe7b17ad4ad28f69a36fbe0aa1c421e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350509"
---
# <a name="_aligned_realloc"></a>_aligned_realloc

Zmienia rozmiar bloku pamięci, który został przydzielony z [_aligned_malloc](aligned-malloc.md) lub [_aligned_offset_malloc](aligned-offset-malloc.md).

## <a name="syntax"></a>Składnia

```C
void * _aligned_realloc(
   void *memblock,
   size_t size,
   size_t alignment
);
```

### <a name="parameters"></a>Parametry

*blok memblock*<br/>
Bieżący wskaźnik bloku pamięci.

*Rozmiar*<br/>
Rozmiar alokacji żądanej pamięci.

*Wyrównanie*<br/>
Wartość wyrównania, która musi być całkowitą potęgą liczby 2.

## <a name="return-value"></a>Wartość zwracana

**_aligned_realloc** zwraca wskaźnik void do ponownie przydzielonego (i ewentualnie przeniesionego) bloku pamięci. Zwracana wartość jest **NULL,** jeśli rozmiar wynosi zero, a argument buforu nie jest **null**, lub jeśli nie ma wystarczającej ilości dostępnej pamięci, aby rozwinąć blok do danego rozmiaru. W pierwszym przypadku oryginalny blok jest zwalniany. W drugim oryginalny blok pozostaje niezmieniony. Zwracana wartość wskazuje miejsce do magazynowania, które jest gwarantowane odpowiednio wyrównane do przechowywania dowolnego typu obiektu. Aby uzyskać wskaźnik do typu innego niż void, należy użyć typu rzutu na wartość zwracaną.

Jest to błąd, aby ponownie przydzielić pamięć i zmienić wyrównanie bloku.

## <a name="remarks"></a>Uwagi

**_aligned_realloc** opiera się na **malloc**. Aby uzyskać więcej informacji na temat korzystania z **_aligned_offset_malloc**, zobacz [malloc](malloc.md).

Ta funkcja ustawia **errno** na **ENOMEM,** jeśli alokacja pamięci nie powiodła się lub żądany rozmiar był większy niż **_HEAP_MAXREQ**. Aby uzyskać więcej informacji o **errno**, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Ponadto **_aligned_realloc** sprawdza poprawność jego parametrów. Jeśli *wyrównanie* nie jest potęgą 2, ta funkcja wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, ta funkcja zwraca **wartość NULL** i ustawia **errno** na **wartość EINVAL**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_realloc**|\<> malloc.h|

## <a name="example"></a>Przykład

Aby uzyskać więcej informacji, zobacz [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Zobacz też

[Wyrównywanie danych](../../c-runtime-library/data-alignment.md)<br/>
