---
title: _lock
ms.date: 11/04/2016
apiname:
- _lock
apilocation:
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120_clr0400.dll
apitype: DLLExport
f1_keywords:
- lock
- _lock
helpviewer_keywords:
- lock function
- _lock function
ms.assetid: 29f77c37-30de-4b3d-91b6-030216e645a6
ms.openlocfilehash: d29488c6dec15fb58eef24f50c1bfafefb8e85c6
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741148"
---
# <a name="lock"></a>_lock

Uzyskuje blokadę wielu wątków.

> [!IMPORTANT]
>  Ta funkcja jest przestarzała. Począwszy od programu Visual Studio 2015, nie jest dostępna w CRT.

## <a name="syntax"></a>Składnia

```
void __cdecl _lock
   int locknum
);
```

#### <a name="parameters"></a>Parametry

*locknum*<br/>
[in] Identyfikator blokady w celu uzyskania.

## <a name="remarks"></a>Uwagi

Jeśli już pozyskany blokady, ta metoda uzyskuje blokadę mimo to i powoduje błąd wewnętrzny (CRT) środowiska wykonawczego języka C. Jeśli metoda nie może uzyskać blokady, kończy działanie z powodu błędu krytycznego i ustawia kod błędu: `_RT_LOCK`.

## <a name="requirements"></a>Wymagania

**Źródło:** mlock.c

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[_unlock](../c-runtime-library/unlock.md)
