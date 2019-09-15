---
title: _aligned_free
ms.date: 11/04/2016
api_name:
- _aligned_free
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
ms.openlocfilehash: 44556d3f044a567f4903ef14a4b2a9b353af02ff
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943967"
---
# <a name="_aligned_free"></a>_aligned_free

Zwalnia blok pamięci, który został przydzielony do [_aligned_malloc](aligned-malloc.md) lub [_aligned_offset_malloc](aligned-offset-malloc.md).

## <a name="syntax"></a>Składnia

```C
void _aligned_free (
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Wskaźnik do bloku pamięci, który został zwrócony do `_aligned_malloc` funkcji or. `_aligned_offset_malloc`

## <a name="remarks"></a>Uwagi

**_aligned_free** jest oznaczona `__declspec(noalias)`, co oznacza, że funkcja nie modyfikuje zmiennych globalnych. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md).

Ta funkcja nie sprawdza poprawności jego parametru, w przeciwieństwie do innych funkcji _aligned CRT. Jeśli *memblock* jest wskaźnikiem typu null, ta funkcja po prostu nie wykonuje żadnych działań. Nie zmienia `errno` i nie wywołuje procedury obsługi nieprawidłowego parametru. Jeśli wystąpi błąd w funkcji z powodu nieużycia funkcji _aligned wcześniej do przydzielenia bloku pamięci lub nieprawidłowego wyrównania pamięci z powodu niektórych nieprzewidzianych Calamity, funkcja generuje raport debugowania z [_RPT, _RPTF, _RPTW, _RPTFW makr ](rpt-rptf-rptw-rptfw-macros.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_free**|\<malloc.h>|

## <a name="example"></a>Przykład

Aby uzyskać więcej informacji, zobacz [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Zobacz także

[Wyrównywanie danych](../../c-runtime-library/data-alignment.md)