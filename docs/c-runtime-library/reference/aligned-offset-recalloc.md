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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 4c71bc701beaabe179676656b331fcce966d1db1
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917169"
---
# <a name="_aligned_offset_recalloc"></a>_aligned_offset_recalloc

Zmienia rozmiar bloku pamięci, który został przydzielony do [_aligned_malloc](aligned-malloc.md) lub [_aligned_offset_malloc](aligned-offset-malloc.md) i inicjuje pamięć do 0.

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

*Liczba*<br/>
Liczba elementów.

*size*<br/>
Długość w bajtach każdego elementu.

*struktury*<br/>
Wartość wyrównania, która musi być całkowitą potęgą liczby 2.

*Przesunięcie*<br/>
Przesunięcie alokacji pamięci, aby wymusić wyrównanie.

## <a name="return-value"></a>Wartość zwracana

**_aligned_offset_recalloc** zwraca wskaźnik void do ponownie przydzielony blok pamięci (i prawdopodobnie przeniesiony). Wartość zwracana ma wartość **null** , jeśli rozmiar ma wartość zero, a argument buforu nie ma **wartości null**lub jeśli nie ma wystarczającej ilości dostępnej pamięci, aby rozszerzyć blok na dany rozmiar. W pierwszym przypadku, oryginalny blok jest zwolniony. W drugim przypadku oryginalny blok nie zmienia się. Wartość zwracana wskazuje miejsce do magazynowania, które jest gwarantowane odpowiednio wyrównane do przechowywania dowolnego typu obiektu. Aby uzyskać wskaźnik do typu innego niż void, należy użyć rzutowania typu dla zwracanej wartości.

**_aligned_offset_recalloc** jest oznaczona `__declspec(noalias)` i `__declspec(restrict)`, co oznacza, że funkcja nie modyfikuje zmiennych globalnych i że zwrócony wskaźnik nie ma aliasu. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczaj](../../cpp/restrict.md).

## <a name="remarks"></a>Uwagi

Podobnie jak [_aligned_offset_malloc](aligned-offset-malloc.md), **_aligned_offset_recalloc** umożliwia wyrównanie struktury do przesunięcia w obrębie struktury.

**_aligned_offset_recalloc** jest oparty na **malloc**. Aby uzyskać więcej informacji o korzystaniu z **_aligned_offset_malloc**, zobacz [malloc](malloc.md). Jeśli *memblock* ma **wartość null**, funkcja wywołuje **_aligned_offset_malloc** wewnętrznie.

Ta funkcja ustawia **errno** na **ENOMEM** , jeśli alokacja pamięci nie powiodła się lub żądany rozmiar (*rozmiar**numeru* * ) był większy niż **_HEAP_MAXREQ**. Aby uzyskać więcej informacji na temat **errno**, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Ponadto **_aligned_offset_recalloc** sprawdza poprawność jego parametrów. Jeśli *wyrównanie* nie jest potęgą liczby 2 lub jeśli *przesunięcie* jest większe lub równe żądanym rozmiarowi i wartości zero, ta funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja zwraca **wartość null** i ustawia **errno** na **EINVAL**.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_offset_recalloc**|\<malloc. h>|

## <a name="see-also"></a>Zobacz też

[Wyrównywanie danych](../../c-runtime-library/data-alignment.md)<br/>
[_recalloc](recalloc.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
