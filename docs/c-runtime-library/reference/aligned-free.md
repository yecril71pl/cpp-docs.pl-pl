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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: d296600da4db2b97479de95cfc1f8c41d0e50708
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915952"
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
Wskaźnik do bloku pamięci, który został zwrócony do funkcji `_aligned_malloc` or. `_aligned_offset_malloc`

## <a name="remarks"></a>Uwagi

**_aligned_free** jest oznaczona `__declspec(noalias)`, co oznacza, że funkcja nie modyfikuje zmiennych globalnych. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md).

Ta funkcja nie sprawdza poprawności jego parametru, w przeciwieństwie do innych _aligned funkcje CRT. Jeśli *memblock* jest wskaźnikiem typu null, ta funkcja po prostu nie wykonuje żadnych działań. Nie zmienia `errno` i nie wywołuje procedury obsługi nieprawidłowego parametru. Jeśli wystąpi błąd w funkcji, z powodu braku funkcji _aligned wcześniej do przydzielenia bloku pamięci lub nieprawidłowego wyrównania pamięci z powodu niektórych nieprzewidzianych Calamity, funkcja generuje raport debugowania z [_RPT, _RPTF, _RPTW, _RPTFW makra](rpt-rptf-rptw-rptfw-macros.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_free**|\<malloc. h>|

## <a name="example"></a>Przykład

Aby uzyskać więcej informacji, zobacz [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Zobacz też

[Wyrównywanie danych](../../c-runtime-library/data-alignment.md)
