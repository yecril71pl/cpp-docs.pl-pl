---
title: _aligned_recalloc
ms.date: 4/2/2020
api_name:
- _aligned_recalloc
- _o__aligned_recalloc
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
- aligned_recalloc
- _aligned_recalloc
helpviewer_keywords:
- aligned_recalloc function
- _aligned_recalloc function
ms.assetid: d3da3dcc-79ef-4273-8af5-ac7469420142
ms.openlocfilehash: af12322742c777cda879e01cb9c054297f807725
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350496"
---
# <a name="_aligned_recalloc"></a>_aligned_recalloc

Zmienia rozmiar bloku pamięci, który został przydzielony z [_aligned_malloc](aligned-malloc.md) lub [_aligned_offset_malloc](aligned-offset-malloc.md) i inicjuje pamięć do 0.

## <a name="syntax"></a>Składnia

```C
void * _aligned_recalloc(
   void *memblock,
   size_t num,
   size_t size,
   size_t alignment
);
```

### <a name="parameters"></a>Parametry

*blok memblock*<br/>
Bieżący wskaźnik bloku pamięci.

*numer*<br/>
Liczba elementów.

*Rozmiar*<br/>
Rozmiar w bajtach każdego elementu.

*Wyrównanie*<br/>
Wartość wyrównania, która musi być całkowitą potęgą liczby 2.

## <a name="return-value"></a>Wartość zwracana

**_aligned_recalloc** zwraca wskaźnik void do ponownie przydzielonego (i ewentualnie przeniesionego) bloku pamięci. Zwracana wartość jest **NULL,** jeśli rozmiar wynosi zero, a argument buforu nie jest **null**, lub jeśli nie ma wystarczającej ilości dostępnej pamięci, aby rozwinąć blok do danego rozmiaru. W pierwszym przypadku oryginalny blok jest zwalniany. W drugim przypadku oryginalny blok pozostaje niezmieniony. Zwracana wartość wskazuje miejsce do magazynowania, które jest gwarantowane odpowiednio wyrównane do przechowywania dowolnego typu obiektu. Aby uzyskać wskaźnik do typu innego niż void, należy użyć typu rzutu na wartość zwracaną.

Jest to błąd, aby ponownie przydzielić pamięć i zmienić wyrównanie bloku.

## <a name="remarks"></a>Uwagi

**_aligned_recalloc** opiera się na **malloc**. Aby uzyskać więcej informacji na temat korzystania z **_aligned_offset_malloc**, zobacz [malloc](malloc.md).

Ta funkcja ustawia **errno** na **ENOMEM,** jeśli alokacja pamięci nie powiodła się lub żądany rozmiar był większy niż **_HEAP_MAXREQ**. Aby uzyskać więcej informacji o **errno**, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Ponadto **_aligned_recalloc** sprawdza poprawność jego parametrów. Jeśli *wyrównanie* nie jest potęgą 2, ta funkcja wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, ta funkcja zwraca **wartość NULL** i ustawia **errno** na **wartość EINVAL**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_recalloc**|\<> malloc.h|

## <a name="see-also"></a>Zobacz też

[Wyrównywanie danych](../../c-runtime-library/data-alignment.md)<br/>
[_recalloc](recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
