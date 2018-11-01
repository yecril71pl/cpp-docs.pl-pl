---
title: _CIlog
ms.date: 11/04/2016
apiname:
- _CIlog
apilocation:
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _CIlog
- CIlog
helpviewer_keywords:
- _CIlog intrinsic
- CIlog intrinsic
ms.assetid: 23503854-ddaa-4fe0-a4a3-7fbb3a43bdec
ms.openlocfilehash: 731c30e08c40f839c99d028aa46d5b61e5fd7c92
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566403"
---
# <a name="cilog"></a>_CIlog

Oblicza logarytm naturalny najwyższą wartość ze stosu.

## <a name="syntax"></a>Składnia

```
void __cdecl _CIlog();
```

## <a name="remarks"></a>Uwagi

Ta wersja `log` funkcja ma specjalne Konwencja wywoływania obsługującą przez kompilator. Jego przyspiesza wykonywanie, ponieważ uniemożliwia kopie generowany i pomaga w alokacja rejestru.

Wartość wynikowa są wypychane na górze stosu.

## <a name="requirements"></a>Wymagania

**Platforma:** x86

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[log, logf, log10, log10f](../c-runtime-library/reference/log-logf-log10-log10f.md)