---
title: ___mb_cur_max_func, ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max
ms.date: 11/04/2016
api_name:
- ___mb_cur_max_l_func
- __p___mb_cur_max
- ___mb_cur_max_func
- __mb_cur_max
api_location:
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- api-ms-win-crt-locale-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ___mb_cur_max_func
- ___mb_cur_max_l_func
- __p___mb_cur_max
- __mb_cur_max
helpviewer_keywords:
- __mb_cur_max
- ___mb_cur_max_func
- ___mb_cur_max_l_func
- __p___mb_cur_max
ms.assetid: 60d36108-1ca7-45a6-8ce7-68a91f13e3a1
ms.openlocfilehash: a37ae2134d92310d6a530c759559b5e4b4af00f6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944196"
---
# <a name="___mb_cur_max_func-___mb_cur_max_l_func-__p___mb_cur_max-__mb_cur_max"></a>___mb_cur_max_func, ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max

Wewnętrzna funkcja CRT. Pobiera maksymalną liczbę bajtów w znaku wielobajtowym dla bieżących lub określonych ustawień regionalnych.

## <a name="syntax"></a>Składnia

```cpp
int ___mb_cur_max_func(void);
int ___mb_cur_max_l_func(_locale_t locale);
int * __p___mb_cur_max(void);
#define __mb_cur_max (___mb_cur_max_func())
```

#### <a name="parameters"></a>Parametry

Ustawienia regionalne struktury ustawień regionalnych, z których ma zostać pobrany wynik. Jeśli ta wartość jest równa null, używane są bieżące ustawienia regionalne wątku.

## <a name="return-value"></a>Wartość zwracana

Maksymalna liczba bajtów w znaku wielobajtowym dla bieżących ustawień regionalnych wątku lub określonych ustawień regionalnych.

## <a name="remarks"></a>Uwagi

Jest to wewnętrzna funkcja wykorzystywana przez CRT do pobierania bieżącej wartości makra [MB_CUR_MAX](../c-runtime-library/mb-cur-max.md) z lokalnego magazynu wątków. Zalecamy użycie `MB_CUR_MAX` makra w kodzie do przenośności.

Makro jest wygodnym sposobem `___mb_cur_max_func()` wywołania funkcji. `__mb_cur_max` Funkcja jest zdefiniowana pod kątem zgodności z programem C++ Visual 5,0 i wcześniejszymi wersjami. `__p___mb_cur_max`

Wewnętrzne funkcje CRT są specyficzne dla implementacji i mogą ulec zmianie w każdej wersji. Nie zalecamy ich używania w kodzie.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`___mb_cur_max_func`, `___mb_cur_max_l_func`, `__p___mb_cur_max`|\<ctype.h>, \<stdlib.h>|

## <a name="see-also"></a>Zobacz także

[MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)
