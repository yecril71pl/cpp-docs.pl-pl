---
title: _aligned_free — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 31c618eb54051582c7e398b174b943e5bf7d2d37
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="alignedfree"></a>_aligned_free

Zwalnia blok pamięci przydzielony przy [_aligned_malloc —](aligned-malloc.md) lub [_aligned_offset_malloc —](aligned-offset-malloc.md).

## <a name="syntax"></a>Składnia

```C
void _aligned_free (
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*memblock* wskaźnik do bloku pamięci, który został zwrócony do **_aligned_malloc —** lub **_aligned_offset_malloc —** funkcji.

## <a name="remarks"></a>Uwagi

**_aligned_free —** jest oznaczony jako `__declspec(noalias)`, co oznacza zagwarantowanie funkcji nie można modyfikować zmienne globalne. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md).

Ta funkcja nie można zweryfikować jej parametr, w przeciwieństwie do innych funkcji CRT _aligned. Jeśli *memblock* jest **NULL** wskaźnika, funkcja ta po prostu wykonuje żadnych akcji. Nie zmienia **errno** i nie jest wywoływany program obsługi nieprawidłowych parametrów. Jeśli wystąpi błąd w funkcji z powodu nie można przydzielić bloku pamięci używa wcześniej funkcje _aligned lub występuje niezgodność pamięci z powodu niektóre nieprzewidzianego calamity, funkcja generuje raport debugowania z [_RPT, _RPTF, _RPTW, _ Rptfw — makra](rpt-rptf-rptw-rptfw-macros.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_free**|\<malloc.h>|

## <a name="example"></a>Przykład

Aby uzyskać więcej informacji, zobacz [_aligned_malloc —](aligned-malloc.md).

## <a name="see-also"></a>Zobacz także

[Wyrównywanie danych](../../c-runtime-library/data-alignment.md)<br/>
