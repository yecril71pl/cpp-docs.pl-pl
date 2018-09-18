---
title: ___mb_cur_max_func, ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- ___mb_cur_max_l_func
- __p___mb_cur_max
- ___mb_cur_max_func
- __mb_cur_max
apilocation:
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- ___mb_cur_max_func
- ___mb_cur_max_l_func
- __p___mb_cur_max
- __mb_cur_max
dev_langs:
- C++
helpviewer_keywords:
- __mb_cur_max
- ___mb_cur_max_func
- ___mb_cur_max_l_func
- __p___mb_cur_max
ms.assetid: 60d36108-1ca7-45a6-8ce7-68a91f13e3a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7eb9682a648f8e302a620e3c2e0dc1631abf7945
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068276"
---
# <a name="mbcurmaxfunc-mbcurmaxlfunc-pmbcurmax-mbcurmax"></a>___mb_cur_max_func ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max

Wewnętrzny funkcji CRT. Pobiera maksymalną liczbę bajtów w znak wielobajtowy dla bieżących lub określonych ustawień regionalnych.

## <a name="syntax"></a>Składnia

```cpp
int ___mb_cur_max_func(void);
int ___mb_cur_max_l_func(_locale_t locale);
int * __p___mb_cur_max(void);
#define __mb_cur_max (___mb_cur_max_func())
```

#### <a name="parameters"></a>Parametry

Struktura ustawień regionalnych, można pobrać wyniku z ustawień regionalnych. Jeśli ta wartość jest równa null, ustawień regionalnych bieżącego wątku jest używana.

## <a name="return-value"></a>Wartość zwracana

Maksymalna liczba bajtów znaków wielobajtowych dla ustawień regionalnych bieżącego wątku lub określonych ustawień regionalnych.

## <a name="remarks"></a>Uwagi

Jest to funkcji wewnętrznej, który używa CRT, aby pobrać bieżącą wartość [MB_CUR_MAX](../c-runtime-library/mb-cur-max.md) — makro z magazynu lokalnego wątku. Firma Microsoft zaleca użycie `MB_CUR_MAX` makra w kodzie do celów przenośności.

`__mb_cur_max` Makro to wygodny sposób wywołania `___mb_cur_max_func()` funkcji. `__p___mb_cur_max` Funkcja jest zdefiniowana na potrzeby utrzymywania zgodności z Visual C++ 5.0 i starszych wersji.

Wewnętrzne funkcje CRT są specyficzne dla implementacji i może ulec zmianie z każdej wersji. Nie zalecamy ich użycie w kodzie.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`___mb_cur_max_func`, `___mb_cur_max_l_func`, `__p___mb_cur_max`|\<CType.h >, \<stdlib.h >|

## <a name="see-also"></a>Zobacz też

[MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)