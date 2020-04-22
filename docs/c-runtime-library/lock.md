---
title: _lock
ms.date: 11/04/2016
api_name:
- _lock
api_location:
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- lock
- _lock
helpviewer_keywords:
- lock function
- _lock function
ms.assetid: 29f77c37-30de-4b3d-91b6-030216e645a6
ms.openlocfilehash: 9ab7cab2209dc2e02cacca6d540927aa39dc3965
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745389"
---
# <a name="_lock"></a>_lock

Uzyskuje blokadę wielowątkową.

> [!IMPORTANT]
> Ta funkcja jest przestarzała. Począwszy od programu Visual Studio 2015, nie jest dostępna w CRT.

## <a name="syntax"></a>Składnia

```cpp
void __cdecl _lock
   int locknum
);
```

#### <a name="parameters"></a>Parametry

*locknum ( locknum )*<br/>
[w] Identyfikator blokady do nabycia.

## <a name="remarks"></a>Uwagi

Jeśli blokada została już nabyta, ta metoda mimo to uzyskuje blokadę i powoduje wewnętrzny błąd w czasie wykonywania C (CRT). Jeśli metoda nie może uzyskać blokady, kończy pracę z błędem ośowym i ustawia kod błędu na `_RT_LOCK`.

## <a name="requirements"></a>Wymagania

**Źródło:** mlock.c

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[_unlock](../c-runtime-library/unlock.md)
