---
title: _CIexp
ms.date: 11/04/2016
api_name:
- _CIexp
api_location:
- msvcr120.dll
- msvcr80.dll
- msvcr110.dll
- msvcr100.dll
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CIexp
- _CIexp
helpviewer_keywords:
- CIexp intrinsic
- _CIexp intrinsic
ms.assetid: f8a3e3b7-fa57-41a3-9983-6c81914cbb55
ms.openlocfilehash: c901442bc7874e75dc0be03c72953dbacb67add3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944700"
---
# <a name="_ciexp"></a>_CIexp

Oblicza wartość wykładniczą górnej wartości na stosie.

## <a name="syntax"></a>Składnia

```
void __cdecl _CIexp();
```

## <a name="remarks"></a>Uwagi

Ta wersja `exp` funkcji ma wyspecjalizowaną konwencję wywoływania, którą rozpoznaje kompilator. Przyspiesza to wykonywanie, ponieważ uniemożliwia generowanie kopii i pomaga w zarejestrowaniu alokacji.

Wartość wyników jest wypychana na górze stosu.

## <a name="requirements"></a>Wymagania

**Platforma:** x86

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[exp, expf, expl](../c-runtime-library/reference/exp-expf.md)
