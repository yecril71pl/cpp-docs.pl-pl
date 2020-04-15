---
title: ___lc_collate_cp_func
ms.date: 4/2/2020
api_name:
- ___lc_collate_cp_func
- _o____lc_collate_cp_func
api_location:
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr90.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ___lc_collate_cp_func
helpviewer_keywords:
- ___lc_collate_cp_func
ms.assetid: 46ccc084-7ac9-4e5d-9138-e12cb5845615
ms.openlocfilehash: 241292f22beea0cbf4e14d1b4480f6621ef6ccca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351133"
---
# <a name="___lc_collate_cp_func"></a>___lc_collate_cp_func

Wewnętrzna funkcja CRT. Pobiera bieżącą stronę kodową sortowania wątku.

## <a name="syntax"></a>Składnia

```cpp
UINT ___lc_codepage_func(void);
```

## <a name="return-value"></a>Wartość zwracana

Bieżąca strona kodowa sortowania wątku.

## <a name="remarks"></a>Uwagi

`___lc_collate_cp_func`jest wewnętrzną funkcją CRT, która jest używana przez inne funkcje CRT, aby uzyskać bieżącą stronę kodową sortowania z lokalnego magazynu wątku dla danych CRT. Te informacje są również dostępne za pomocą funkcji [_get_current_locale.](../c-runtime-library/reference/get-current-locale.md)

Wewnętrzne funkcje CRT są specyficzne dla implementacji i mogą ulec zmianie z każdą wersją. Nie zaleca się ich używania w kodzie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`___lc_collate_cp_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Zobacz też

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)
