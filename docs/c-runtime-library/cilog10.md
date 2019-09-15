---
title: _CIlog10
ms.date: 11/04/2016
api_name:
- _CIlog10
api_location:
- msvcr100.dll
- msvcr120.dll
- msvcr80.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr110.dll
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CIlog10
- _CIlog10
helpviewer_keywords:
- _CIlog10 intrinsic
- CIlog10 intrinsic
ms.assetid: 05d7fcaa-3cff-4cc5-8d44-015e7cacba24
ms.openlocfilehash: c99fdab859acf280afc8a595696a17b2d03a47e4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944610"
---
# <a name="_cilog10"></a>_CIlog10

`log10` Wykonuje operację na najwyższej wartości na stosie.

## <a name="syntax"></a>Składnia

```
void __cdecl _CIlog10();
```

## <a name="remarks"></a>Uwagi

Ta wersja `log10` funkcji ma wyspecjalizowaną konwencję wywoływania, którą rozpoznaje kompilator. Funkcja przyspiesza wykonywanie, ponieważ uniemożliwia generowanie kopii i pomaga w zarejestrowaniu alokacji.

Wartość wyników jest wypychana na górze stosu.

## <a name="requirements"></a>Wymagania

**Platforma:** x86

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[log, logf, log10, log10f](../c-runtime-library/reference/log-logf-log10-log10f.md)
