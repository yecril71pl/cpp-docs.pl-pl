---
title: _aligned_offset_recalloc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _aligned_offset_recalloc
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- aligned_offset_recalloc
- _aligned_offset_recalloc
dev_langs:
- C++
helpviewer_keywords:
- aligned_offset_recalloc function
- _aligned_offset_recalloc function
ms.assetid: a258f54e-eeb4-4853-96fc-007d710f98e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9297defc32966209dd484da80e9230d6df5dbab
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="alignedoffsetrecalloc"></a>_aligned_offset_recalloc

Zmienia rozmiar blok pamięci przydzielony przy [_aligned_malloc —](aligned-malloc.md) lub [_aligned_offset_malloc —](aligned-offset-malloc.md) i inicjuje pamięci na 0.

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

*memblock*<br/>
Bieżący wskaźnik bloku pamięci.

*Numer*<br/>
Liczba elementów.

*Rozmiar*<br/>
Długość w bajtach każdego elementu.

*Wyrównanie*<br/>
Wartość wyrównania, która musi być całkowitą potęgą liczby 2.

*offset*<br/>
Przesunięcie alokacji pamięci, aby wymusić wyrównanie.

## <a name="return-value"></a>Wartość zwracana

**_aligned_offset_recalloc —** zwraca typ void wskaźnik do bloku pamięci przydzielić (i prawdopodobnie przenoszenia). Wartość zwracana jest **NULL** Jeśli rozmiar wynosi zero, a argument bufor nie jest **NULL**, lub jeśli nie ma dostatecznej ilości dostępnej pamięci, aby rozwinąć blok na dany rozmiar. W pierwszym przypadku oryginalnego bloku zostanie zwolniona. W drugim przypadku oryginalnego bloku jest bez zmian. Wartości zwracanej wskazuje miejsce do magazynowania, które na pewno jest odpowiednio dopasowany do przechowywania obiekty dowolnego typu. Aby uzyskać wskaźnik do typu innego niż void, użyj typu rzutowania wartości zwracanej.

**_aligned_offset_recalloc —** jest oznaczony jako `__declspec(noalias)` i `__declspec(restrict)`, co oznacza zagwarantowanie funkcji nie można modyfikować zmienne globalne i czy wskaźnik zwrócone, nie jest używane z aliasem. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczyć](../../cpp/restrict.md).

## <a name="remarks"></a>Uwagi

Podobnie jak [_aligned_offset_malloc —](aligned-offset-malloc.md), **_aligned_offset_recalloc —** umożliwia struktury wyrównania przy przesunięciu w strukturze.

**_aligned_offset_recalloc —** opiera się na **— funkcja malloc**. Aby uzyskać więcej informacji o korzystaniu z **_aligned_offset_malloc —**, zobacz [— funkcja malloc](malloc.md). Jeśli *memblock* jest **NULL**, wywołania funkcji **_aligned_offset_malloc —** wewnętrznie.

Ta funkcja ustawia **errno** do **enomem —** czy alokacja pamięci nie powiodła się, czy żądany rozmiar (*numer* * *rozmiar* ) była większa niż **_heap_maxreq —**. Aby uzyskać więcej informacji na temat **errno**, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Ponadto **_aligned_offset_recalloc —** sprawdza poprawność parametrów. Jeśli *wyrównanie* nie jest potęgą liczby 2 lub, jeśli *przesunięcie* jest większa niż lub równa żądany rozmiar i różną od zera, ta funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [parametru Sprawdzanie poprawności](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, ta funkcja zwraca **NULL** i ustawia **errno** do **einval —**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_offset_recalloc**|\<malloc.h>|

## <a name="see-also"></a>Zobacz także

[Wyrównywanie danych](../../c-runtime-library/data-alignment.md)<br/>
[_recalloc](recalloc.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
