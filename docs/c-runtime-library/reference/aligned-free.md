---
title: _aligned_free — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _aligned_free
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
- aligned_free
- _aligned_free
dev_langs:
- C++
helpviewer_keywords:
- _aligned_free function
- aligned_free function
ms.assetid: ed1ce952-cdfc-4682-85cc-f75d4101603d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 54700ad2a1eed391647a66a4c54a726b75e812f4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069719"
---
# <a name="alignedfree"></a>_aligned_free

Zwalnia blok pamięci, która została przydzielona za pomocą [_aligned_malloc](aligned-malloc.md) lub [_aligned_offset_malloc —](aligned-offset-malloc.md).

## <a name="syntax"></a>Składnia

```C
void _aligned_free (
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Wskaźnik do bloku pamięci, który został zwrócony do `_aligned_malloc` lub `_aligned_offset_malloc` funkcji.

## <a name="remarks"></a>Uwagi

**_aligned_free —** jest oznaczony jako `__declspec(noalias)`, co oznacza, że funkcja daje gwarancję niemodyfikowania zmiennych globalnych. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md).

Ta funkcja nie można zweryfikować parametr, w przeciwieństwie do innych funkcji CRT _aligned. Jeśli *memblock* jest wskaźnikiem typu NULL, funkcja ta po prostu wykonuje żadnych akcji. Nie zmienia `errno` i nie wywołuje program obsługi nieprawidłowych parametrów. Jeśli wystąpi błąd w funkcji ze względu na nie przy użyciu funkcji _aligned wcześniej przydzielić blok pamięci lub występuje niezgodność pamięci z powodu niektóre nieprzewidziane calamity, funkcja generuje raport debugowania z [_RPT, _RPTF, _RPTW, _ Rptfw — makra](rpt-rptf-rptw-rptfw-macros.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_free**|\<malloc.h>|

## <a name="example"></a>Przykład

Aby uzyskać więcej informacji, zobacz [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Zobacz także

[Wyrównywanie danych](../../c-runtime-library/data-alignment.md)