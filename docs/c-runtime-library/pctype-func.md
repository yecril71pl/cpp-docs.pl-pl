---
title: __pctype_func | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
dev_langs:
- C++
helpviewer_keywords:
- __pctype_func
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36c8dd0467dc50c9eba9db954f28711aa8525cd2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034296"
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

## <a name="see-also"></a>Zobacz też

[_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)