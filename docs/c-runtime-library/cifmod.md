---
title: _CIfmod
ms.date: 11/04/2016
apiname:
- _CIfmod
apilocation:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _CIfmod
- CIfmod
helpviewer_keywords:
- CIfmod intrinsic
- _CIfmod intrinsic
ms.assetid: 7c050653-7ec6-4810-b3a7-7a0057ea65ed
ms.openlocfilehash: e0e6b2f846de77d27b1826e1f24cd364c0d76a64
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703080"
---
# <a name="cifmod"></a>_CIfmod

Oblicza zmiennoprzecinkową resztę działania najważniejsze dwie wartości na stosie.

## <a name="syntax"></a>Składnia

```
void __cdecl _CIfmod();
```

## <a name="remarks"></a>Uwagi

Ta wersja `fmod` funkcja ma specjalne Konwencja wywoływania obsługującą przez kompilator. Jego przyspiesza wykonywanie, ponieważ uniemożliwia kopie generowany i pomaga w alokacja rejestru.

Wartość wynikowa są wypychane na górze stosu.

## <a name="requirements"></a>Wymagania

**Platforma:** x86

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[fmod, fmodf](../c-runtime-library/reference/fmod-fmodf.md)