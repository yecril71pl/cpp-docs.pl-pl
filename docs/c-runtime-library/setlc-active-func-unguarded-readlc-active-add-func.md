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
ms.openlocfilehash: 244bb5b0bd6a15dab2de1ad2d6b71c2ae2f850bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62268827"
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

## <a name="see-also"></a>Zobacz także

[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)
