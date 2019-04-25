---
title: __pctype_func
ms.date: 11/04/2016
apiname:
- __pctype_func
apilocation:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- __pctype_func
helpviewer_keywords:
- __pctype_func
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
ms.openlocfilehash: a152f3612373189c964aaca005fe3b989eec8694
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62289172"
---
# <a name="pctypefunc"></a>__pctype_func

Pobiera wskaźnik do tablicy informacji o klasyfikacji znaków.

## <a name="syntax"></a>Składnia

```cpp
const unsigned short *__pctype_func(
   )
```

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do tablicy informacji o klasyfikacji znaków.

## <a name="remarks"></a>Uwagi

Informacje przedstawione w tabeli klasyfikacji znaków jest tylko do użytku wewnętrznego i jest używany przez różne funkcje, które klasyfikowania znaków typu `char`. Aby uzyskać więcej informacji, zobacz `Remarks` części [_pctype —, _pwctype —, _wctype —, _mbctype —, _mbcasemap —](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|__pctype_func|CType.h|

## <a name="see-also"></a>Zobacz także

[_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)
