---
title: ___setlc_active_func, ___unguarded_readlc_active_add_func | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
dev_langs:
- C++
helpviewer_keywords:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
ms.assetid: 605ec4e3-81e5-4ece-935a-f434768cc702
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 59ec444ae81d680bf57aa4542f231c021f1abddc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102785"
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