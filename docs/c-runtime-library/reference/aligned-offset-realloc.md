---
title: _aligned_offset_realloc
ms.date: 4/2/2020
api_name:
- _aligned_offset_realloc
- _o__aligned_offset_realloc
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
- aligned_offset_realloc
- _aligned_offset_realloc
helpviewer_keywords:
- aligned_offset_realloc function
- _aligned_offset_realloc function
ms.assetid: e0263533-991e-41b0-acc9-1b8a51ab9ecd
ms.openlocfilehash: b27f5000a48ec3aafe37c6bd59e9b9acddd5bec5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350574"
---
# <a name="_aligned_offset_realloc"></a>_aligned_offset_realloc

Zmienia rozmiar bloku pamięci, który został przydzielony z [_aligned_malloc](aligned-malloc.md) lub [_aligned_offset_malloc](aligned-offset-malloc.md).

## <a name="syntax"></a>Składnia

```C
void * _aligned_offset_realloc(
   void *memblock,
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Parametry

*blok memblock*<br/>
Bieżący wskaźnik bloku pamięci.

*Rozmiar*<br/>
Rozmiar alokacji pamięci.

*Wyrównanie*<br/>
Wartość wyrównania, która musi być całkowitą potęgą liczby 2.

*Przesunięcie*<br/>
Przesunięcie alokacji pamięci, aby wymusić wyrównanie.

## <a name="return-value"></a>Wartość zwracana

**_aligned_offset_realloc** zwraca wskaźnik void do ponownie przydzielonego (i ewentualnie przeniesionego) bloku pamięci. Zwracana wartość jest **NULL,** jeśli rozmiar wynosi zero, a argument buforu nie jest **null**, lub jeśli nie ma wystarczającej ilości dostępnej pamięci, aby rozwinąć blok do danego rozmiaru. W pierwszym przypadku oryginalny blok jest zwalniany. W drugim przypadku oryginalny blok pozostaje niezmieniony. Zwracana wartość wskazuje miejsce do magazynowania, które jest gwarantowane odpowiednio wyrównane do przechowywania dowolnego typu obiektu. Aby uzyskać wskaźnik do typu innego niż void, należy użyć typu rzutu na wartość zwracaną.

**_aligned_offset_realloc** jest oznaczony `__declspec(noalias)` i `__declspec(restrict)`, co oznacza, że funkcja jest gwarantowana, aby nie modyfikować zmiennych globalnych i że wskaźnik zwrócony nie jest aliasem. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczyć](../../cpp/restrict.md).

## <a name="remarks"></a>Uwagi

Podobnie [jak _aligned_offset_malloc,](aligned-offset-malloc.md) **_aligned_offset_realloc** umożliwia wyrównanie konstrukcji z przesunięciem w obrębie konstrukcji.

**_aligned_offset_realloc** opiera się na **malloc**. Aby uzyskać więcej informacji na temat korzystania z **_aligned_offset_malloc**, zobacz [malloc](malloc.md). Jeśli *memblock* ma **wartość NULL**, funkcja wywołuje **_aligned_offset_malloc** wewnętrznie.

Ta funkcja ustawia **errno** na **ENOMEM,** jeśli alokacja pamięci nie powiodła się lub żądany rozmiar był większy niż **_HEAP_MAXREQ**. Aby uzyskać więcej informacji o **errno**, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Ponadto **_aligned_offset_realloc** sprawdza poprawność jego parametrów. Jeśli *wyrównanie* nie jest potęgą 2 lub jeśli *przesunięcie* jest większe lub równe *rozmiarowi* i niezerowej, ta funkcja wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [zatwierdzeniu parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, ta funkcja zwraca **wartość NULL** i ustawia **errno** na **wartość EINVAL**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_offset_realloc**|\<> malloc.h|

## <a name="example"></a>Przykład

Aby uzyskać więcej informacji, zobacz [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Zobacz też

[Wyrównywanie danych](../../c-runtime-library/data-alignment.md)<br/>
