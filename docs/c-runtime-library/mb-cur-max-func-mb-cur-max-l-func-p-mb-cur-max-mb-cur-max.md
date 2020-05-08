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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 8287e2e7cab8880d35fef170287713adcc103c7e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912958"
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

Jest to wewnętrzna funkcja wykorzystywana przez CRT do pobrania bieżącej wartości makra [MB_CUR_MAX](../c-runtime-library/mb-cur-max.md) z lokalnego magazynu wątków. Zalecamy użycie `MB_CUR_MAX` makra w kodzie do przenośności.

`__mb_cur_max` Makro jest wygodnym sposobem wywołania `___mb_cur_max_func()` funkcji. `__p___mb_cur_max` Funkcja jest zdefiniowana pod kątem zgodności z Visual C++ 5,0 i wcześniejszymi wersjami.

Wewnętrzne funkcje CRT są specyficzne dla implementacji i mogą ulec zmianie w każdej wersji. Nie zalecamy ich używania w kodzie.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`___mb_cur_max_func`, `___mb_cur_max_l_func`, `__p___mb_cur_max`|\<CType. h>, \<STDLIB. h>|

## <a name="see-also"></a>Zobacz też

[MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)
