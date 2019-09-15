---
title: _CIcos
ms.date: 04/11/2018
api_name:
- _CIcos
api_location:
- msvcr90.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CIcos
- _CIcos
helpviewer_keywords:
- _CIcos intrinsic
- CIcos intrinsic
ms.assetid: 6fc203fb-66f3-4ead-9784-f85833c26f1b
ms.openlocfilehash: 5a57e948a73b8c4243ebe5a8a12f62cc55a40f3b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940537"
---
# <a name="_cicos"></a>_CIcos

Oblicza cosinus górnej wartości w stosie zmiennoprzecinkowym.

## <a name="syntax"></a>Składnia

```C
void __cdecl _CIcos();
```

## <a name="remarks"></a>Uwagi

Ta wersja funkcji [cos](../c-runtime-library/reference/cos-cosf-cosl.md) ma wyspecjalizowaną konwencję wywoływania, którą rozpoznaje kompilator. Przyspiesza to wykonywanie, ponieważ uniemożliwia generowanie kopii i pomaga w zarejestrowaniu alokacji.

Wartość wyników jest wypychana na górze stosu zmiennoprzecinkowego.

## <a name="requirements"></a>Wymagania

**Platforma:** x86

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[cos, cosf, cosl](../c-runtime-library/reference/cos-cosf-cosl.md)<br/>
