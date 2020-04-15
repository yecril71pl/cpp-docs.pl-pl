---
title: _aligned_offset_recalloc
ms.date: 4/2/2020
api_name:
- _aligned_offset_recalloc
- _o__aligned_offset_recalloc
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
- aligned_offset_recalloc
- _aligned_offset_recalloc
helpviewer_keywords:
- aligned_offset_recalloc function
- _aligned_offset_recalloc function
ms.assetid: a258f54e-eeb4-4853-96fc-007d710f98e9
ms.openlocfilehash: 4c710712138d07191468cdc7ef02fc75e2f46dad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350548"
---
# <a name="_aligned_offset_recalloc"></a>_aligned_offset_recalloc

Zmienia rozmiar bloku pamięci, który został przydzielony z [_aligned_malloc](aligned-malloc.md) lub [_aligned_offset_malloc](aligned-offset-malloc.md) i inicjuje pamięć do 0.

## <a name="syntax"></a>Składnia

```C
void * _aligned_offset_recalloc(
   void *memblock,
   size_t num,
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Parametry

*blok memblock*<br/>
Bieżący wskaźnik bloku pamięci.

*numer*<br/>
Liczba elementów.

*Rozmiar*<br/>
Długość w bajtach każdego elementu.

*Wyrównanie*<br/>
Wartość wyrównania, która musi być całkowitą potęgą liczby 2.

*Przesunięcie*<br/>
Przesunięcie alokacji pamięci, aby wymusić wyrównanie.

## <a name="return-value"></a>Wartość zwracana

**_aligned_offset_recalloc** zwraca wskaźnik void do ponownie przydzielonego (i ewentualnie przeniesionego) bloku pamięci. Zwracana wartość jest **NULL,** jeśli rozmiar wynosi zero, a argument buforu nie jest **null**, lub jeśli nie ma wystarczającej ilości dostępnej pamięci, aby rozwinąć blok do danego rozmiaru. W pierwszym przypadku oryginalny blok jest zwalniany. W drugim przypadku oryginalny blok pozostaje niezmieniony. Zwracana wartość wskazuje miejsce do magazynowania, które jest gwarantowane odpowiednio wyrównane do przechowywania dowolnego typu obiektu. Aby uzyskać wskaźnik do typu innego niż void, należy użyć typu rzutu na wartość zwracaną.

**_aligned_offset_recalloc** jest oznaczony `__declspec(noalias)` `__declspec(restrict)`i , co oznacza, że funkcja jest gwarantowana nie modyfikować zmiennych globalnych i że wskaźnik zwrócony nie jest aliasem. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczyć](../../cpp/restrict.md).

## <a name="remarks"></a>Uwagi

Podobnie [jak _aligned_offset_malloc,](aligned-offset-malloc.md) **_aligned_offset_recalloc** umożliwia wyrównanie konstrukcji z przesunięciem w obrębie konstrukcji.

**_aligned_offset_recalloc** opiera się na **malloc**. Aby uzyskać więcej informacji na temat korzystania z **_aligned_offset_malloc**, zobacz [malloc](malloc.md). Jeśli *memblock* ma **wartość NULL**, funkcja wywołuje **_aligned_offset_malloc** wewnętrznie.

Ta funkcja ustawia **errno** na **ENOMEM,** jeśli alokacja pamięci nie powiodła się lub jeśli żądany rozmiar *(rozmiar**liczby)* * był większy niż **_HEAP_MAXREQ**. Aby uzyskać więcej informacji o **errno**, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Ponadto **_aligned_offset_recalloc** sprawdza poprawność jego parametrów. Jeśli *wyrównanie* nie jest potęgą 2 lub jeśli *przesunięcie* jest większe lub równe żądanemu rozmiarowi i niezerowe, ta funkcja wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [zatwierdzeniu parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, ta funkcja zwraca **wartość NULL** i ustawia **errno** na **wartość EINVAL**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_offset_recalloc**|\<> malloc.h|

## <a name="see-also"></a>Zobacz też

[Wyrównywanie danych](../../c-runtime-library/data-alignment.md)<br/>
[_recalloc](recalloc.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
