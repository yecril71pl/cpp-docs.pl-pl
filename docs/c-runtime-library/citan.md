---
title: _CItan
ms.date: 04/11/2018
apiname:
- _CItan
apilocation:
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcrt.dll
- msvcr110.dll
- msvcr90.dll
- msvcr120.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _CItan
- CItan
helpviewer_keywords:
- CItan intrinsic
- _CItan intrinsic
ms.assetid: d1ea3113-50a2-45a6-b6bc-680fcdcc0928
ms.openlocfilehash: d64ce3e187a055185a82868988825c418b3f54bd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344788"
---
# <a name="citan"></a>_CItan

Oblicza tangens najwyższą wartość na stosu zmiennoprzecinkowego.

## <a name="syntax"></a>Składnia

```C
void __cdecl _CItan();
```

## <a name="remarks"></a>Uwagi

Ta wersja [tan](../c-runtime-library/reference/tan-tanf-tanl.md) funkcja ma specjalne Konwencja wywoływania obsługującą przez kompilator. Funkcja przyspiesza wykonywanie, ponieważ uniemożliwia kopie generowany i pomaga w alokacja rejestru.

Wartość wynikowa są wypychane na górze stosu zmiennoprzecinkowego.

## <a name="requirements"></a>Wymagania

**Platforma:** x86

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[tan, tanf, tanl](../c-runtime-library/reference/tan-tanf-tanl.md)<br/>
