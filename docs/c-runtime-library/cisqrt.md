---
title: _CIsqrt
ms.date: 4/2/2020
api_name:
- _CIsqrt
- _o__CIsqrt
api_location:
- msvcr90.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcrt.dll
- msvcr110.dll
- msvcr100.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CIsqrt
- CIsqrt
helpviewer_keywords:
- CIsqrt intrinsic
- _CIsqrt intrinsic
ms.assetid: 663548ea-398c-48ee-8397-a787c6ebb937
ms.openlocfilehash: baedb0541e16c28d18d0062fa5498fb8e2c8dea8
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918351"
---
# <a name="_cisqrt"></a>_CIsqrt

Oblicza pierwiastek kwadratowy górnej wartości na stosie.

## <a name="syntax"></a>Składnia

```cpp
void __cdecl _CIsqrt();
```

## <a name="remarks"></a>Uwagi

Ta wersja `sqrt` funkcji ma wyspecjalizowaną konwencję wywoływania, którą rozpoznaje kompilator. Przyspiesza to wykonywanie, ponieważ uniemożliwia generowanie kopii i pomaga w zarejestrowaniu alokacji.

Wartość wyników jest wypychana na górze stosu.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](global-state.md).

## <a name="requirements"></a>Wymagania

**Platforma:** x86

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[sqrt, sqrtf, sqrtl](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)
