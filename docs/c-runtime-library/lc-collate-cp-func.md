---
title: ___lc_collate_cp_func
ms.date: 11/04/2016
apiname:
- ___lc_collate_cp_func
apilocation:
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- ___lc_collate_cp_func
helpviewer_keywords:
- ___lc_collate_cp_func
ms.assetid: 46ccc084-7ac9-4e5d-9138-e12cb5845615
ms.openlocfilehash: fac8b7ba2e9568dd53509e5cccbb96a6b2f1df8d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62342768"
---
# <a name="lccollatecpfunc"></a>___lc_collate_cp_func

Wewnętrzny funkcji CRT. Pobiera bieżący strona kodowa sortowania wątku.

## <a name="syntax"></a>Składnia

```cpp
UINT ___lc_codepage_func(void);
```

## <a name="return-value"></a>Wartość zwracana

Bieżąca strona kodowa sortowania wątku.

## <a name="remarks"></a>Uwagi

`___lc_collate_cp_func` jest wewnętrzny funkcji CRT, który jest używany przez inne funkcje CRT, można uzyskać z magazynu lokalnego wątku CRT danych bieżącej stronie kodowej sortowania. Te informacje są dostępne również za pomocą [_get_current_locale —](../c-runtime-library/reference/get-current-locale.md) funkcji.

Wewnętrzne funkcje CRT są specyficzne dla implementacji i może ulec zmianie z każdej wersji. Nie zalecamy ich użycie w kodzie.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`___lc_collate_cp_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Zobacz także

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)
