---
title: __pctype_func
ms.date: 11/04/2016
api_name:
- __pctype_func
api_location:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __pctype_func
helpviewer_keywords:
- __pctype_func
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
ms.openlocfilehash: f5dae74dd601df1dc737293a181eca60f5cd23f8
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944039"
---
# <a name="__pctype_func"></a>__pctype_func

Pobiera wskaźnik do tablicy informacji o klasyfikacji znaków.

## <a name="syntax"></a>Składnia

```cpp
const unsigned short *__pctype_func(
   )
```

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do tablicy informacji o klasyfikacji znaków.

## <a name="remarks"></a>Uwagi

Informacje w tabeli klasyfikacji znaków są przeznaczone tylko do użytku wewnętrznego i są używane przez różne funkcje, które klasyfikują znaki typu `char`. Aby uzyskać więcej informacji, zobacz `Remarks` sekcję [_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|__pctype_func|CType. h|

## <a name="see-also"></a>Zobacz także

[_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)
