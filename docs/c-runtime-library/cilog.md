---
title: _CIlog
ms.date: 4/2/2020
api_name:
- _CIlog
- _o__CIlog
api_location:
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CIlog
- CIlog
helpviewer_keywords:
- _CIlog intrinsic
- CIlog intrinsic
ms.assetid: 23503854-ddaa-4fe0-a4a3-7fbb3a43bdec
ms.openlocfilehash: 405af59eab918498578c2d62c66be1017ecf156f
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918060"
---
# <a name="_cilog"></a>_CIlog

Oblicza logarytm naturalny górnej wartości w stosie.

## <a name="syntax"></a>Składnia

```cpp
void __cdecl _CIlog();
```

## <a name="remarks"></a>Uwagi

Ta wersja `log` funkcji ma wyspecjalizowaną konwencję wywoływania, którą rozpoznaje kompilator. Przyspiesza to wykonywanie, ponieważ uniemożliwia generowanie kopii i pomaga w zarejestrowaniu alokacji.

Wartość wyników jest wypychana na górze stosu.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](global-state.md).

## <a name="requirements"></a>Wymagania

**Platforma:** x86

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[log, logf, log10, log10f](../c-runtime-library/reference/log-logf-log10-log10f.md)
