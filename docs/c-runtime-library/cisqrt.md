---
title: _CIsqrt
ms.date: 11/04/2016
apiname:
- _CIsqrt
apilocation:
- msvcr90.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcrt.dll
- msvcr110.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _CIsqrt
- CIsqrt
helpviewer_keywords:
- CIsqrt intrinsic
- _CIsqrt intrinsic
ms.assetid: 663548ea-398c-48ee-8397-a787c6ebb937
ms.openlocfilehash: 25df1641ff839a77792f5a465d72e578b5d0f405
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453771"
---
# <a name="cisqrt"></a>_CIsqrt

Oblicza pierwiastek kwadratowy z najwyższą wartość ze stosu.

## <a name="syntax"></a>Składnia

```
void __cdecl _CIsqrt();
```

## <a name="remarks"></a>Uwagi

Ta wersja `sqrt` funkcja ma specjalne Konwencja wywoływania obsługującą przez kompilator. Jego przyspiesza wykonywanie, ponieważ uniemożliwia kopie generowany i pomaga w alokacja rejestru.

Wartość wynikowa są wypychane na górze stosu.

## <a name="requirements"></a>Wymagania

**Platforma:** x86

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[sqrt, sqrtf, sqrtl](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)