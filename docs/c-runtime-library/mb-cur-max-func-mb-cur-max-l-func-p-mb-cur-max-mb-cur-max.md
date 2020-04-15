---
title: ___mb_cur_max_func, ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max
ms.date: 4/2/2020
api_name:
- ___mb_cur_max_l_func
- __p___mb_cur_max
- ___mb_cur_max_func
- __mb_cur_max
- _o____mb_cur_max_func
api_location:
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: f9b9e2d903bb05f5b1b653b4fb51c57b354d4126
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351077"
---
# <a name="___mb_cur_max_func-___mb_cur_max_l_func-__p___mb_cur_max-__mb_cur_max"></a>___mb_cur_max_func, ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max

Wewnętrzna funkcja CRT. Pobiera maksymalną liczbę bajtów w znaku wielobajtowym dla bieżącego lub określonego ustawienia regionalne.

## <a name="syntax"></a>Składnia

```cpp
int ___mb_cur_max_func(void);
int ___mb_cur_max_l_func(_locale_t locale);
int * __p___mb_cur_max(void);
#define __mb_cur_max (___mb_cur_max_func())
```

#### <a name="parameters"></a>Parametry

ustawienia regionalne Struktura ustawień regionalnych, aby pobrać wynik z. Jeśli ta wartość ma wartość null, używane są bieżące ustawienia regionalne wątku.

## <a name="return-value"></a>Wartość zwracana

Maksymalna liczba bajtów w znaku wielobajtowym dla bieżących ustawień regionalnych wątku lub określonych ustawień regionalnych.

## <a name="remarks"></a>Uwagi

Jest to funkcja wewnętrzna używana przez CRT do pobierania bieżącej wartości [makra MB_CUR_MAX](../c-runtime-library/mb-cur-max.md) z magazynu lokalnego wątku. Zaleca się użycie `MB_CUR_MAX` makra w kodzie do przenoszenia.

Makro `__mb_cur_max` jest wygodnym sposobem `___mb_cur_max_func()` wywołania funkcji. Funkcja `__p___mb_cur_max` jest zdefiniowana dla zgodności z visual C++ 5.0 i wcześniejszych wersji.

Wewnętrzne funkcje CRT są specyficzne dla implementacji i mogą ulec zmianie z każdą wersją. Nie zaleca się ich używania w kodzie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`___mb_cur_max_func`, `___mb_cur_max_l_func`, `__p___mb_cur_max`|\<ctype.h>, \<stdlib.h>|

## <a name="see-also"></a>Zobacz też

[MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)
