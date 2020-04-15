---
title: _aligned_free
ms.date: 4/2/2020
api_name:
- _aligned_free
- _o__aligned_free
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
- aligned_free
- _aligned_free
helpviewer_keywords:
- _aligned_free function
- aligned_free function
ms.assetid: ed1ce952-cdfc-4682-85cc-f75d4101603d
ms.openlocfilehash: a6e5f0dcd0bbea436ecdad7abb1fd6fc948f80dc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350713"
---
# <a name="_aligned_free"></a>_aligned_free

Zwalnia blok pamięci, który został przydzielony z [_aligned_malloc](aligned-malloc.md) lub [_aligned_offset_malloc](aligned-offset-malloc.md).

## <a name="syntax"></a>Składnia

```C
void _aligned_free (
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*blok memblock*<br/>
Wskaźnik do bloku pamięci, który `_aligned_malloc` został `_aligned_offset_malloc` zwrócony do funkcji lub.

## <a name="remarks"></a>Uwagi

**_aligned_free** jest oznaczony, `__declspec(noalias)`co oznacza, że funkcja jest gwarantowana, aby nie modyfikować zmiennych globalnych. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md).

Ta funkcja nie sprawdza poprawności jego parametru, w przeciwieństwie do innych _aligned funkcji CRT. Jeśli *memblock* jest wskaźnikiem NULL, ta funkcja po prostu nie wykonuje żadnych akcji. Nie zmienia `errno` się i nie wywołuje nieprawidłowy program obsługi parametrów. Jeśli w funkcji wystąpi błąd spowodowany nieużywaniem wcześniej funkcji _aligned do przydzielenia bloku pamięci lub niewspółosiowość pamięci występuje z powodu nieprzewidzianych nieszczęść, funkcja generuje raport debugowania z [_RPT, _RPTF, _RPTW, _RPTFW makra](rpt-rptf-rptw-rptfw-macros.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_free**|\<> malloc.h|

## <a name="example"></a>Przykład

Aby uzyskać więcej informacji, zobacz [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Zobacz też

[Wyrównywanie danych](../../c-runtime-library/data-alignment.md)
