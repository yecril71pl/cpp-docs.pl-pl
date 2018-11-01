---
title: ___setlc_active_func, ___unguarded_readlc_active_add_func
ms.date: 11/04/2016
apiname:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
apilocation:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- ___unguarded_readlc_active_add_func
- ___setlc_active_func
helpviewer_keywords:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
ms.assetid: 605ec4e3-81e5-4ece-935a-f434768cc702
ms.openlocfilehash: 23095bb13108ec9fde2b168035009f440e9d96f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525787"
---
# <a name="setlcactivefunc-unguardedreadlcactiveaddfunc"></a>___setlc_active_func, ___unguarded_readlc_active_add_func

OBSOLETE. CRT eksportuje tych wewnętrznych funkcji tylko w celu zachowania zgodność binarną.

## <a name="syntax"></a>Składnia

```cpp
int ___setlc_active_func(void);
int * ___unguarded_readlc_active_add_func(void);
```

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana nie ma znaczenia.

## <a name="remarks"></a>Uwagi

Mimo że wewnętrzne funkcje CRT `___setlc_active_func` i `___unguarded_readlc_active_add_func` są przestarzałe i nie są już używane, są eksportowane przez bibliotekę CRT, aby zachować zgodność binarną. Oryginalny celem `___setlc_active_func` było zwrócenie liczby aktywnych wywołań `setlocale` funkcji. Oryginalny celem `___unguarded_readlc_active_add_func` było zwrócenie liczby funkcji, które określone ustawienia regionalne bez blokowania go.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`___setlc_active_func`, `___unguarded_readlc_active_add_func`|brak|

## <a name="see-also"></a>Zobacz też

[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)