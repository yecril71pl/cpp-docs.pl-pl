---
title: ___lc_codepage_func
ms.date: 11/04/2016
apiname:
- ___lc_codepage_func
apilocation:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
- msvcr110.dll
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- lc_codepage_func
- ___lc_codepage_func
helpviewer_keywords:
- ___lc_codepage_func
ms.assetid: 6a663bd0-5a63-4a2f-9507-872ec1582aae
ms.openlocfilehash: 3a6bcb9688116fc72b4c33b13fff73db3dff6c15
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573270"
---
# <a name="lccodepagefunc"></a>___lc_codepage_func

Wewnętrzny funkcji CRT. Pobiera bieżący strona kodowa wątku.

## <a name="syntax"></a>Składnia

```cpp
UINT ___lc_codepage_func(void);
```

## <a name="return-value"></a>Wartość zwracana

Bieżąca strona kodowa wątku.

## <a name="remarks"></a>Uwagi

`___lc_codepage_func` jest wewnętrzny funkcji CRT, który jest używany przez inne funkcje CRT, można uzyskać z magazynu lokalnego wątku CRT danych bieżącej stronie kodowej. Te informacje są dostępne również za pomocą [_get_current_locale —](../c-runtime-library/reference/get-current-locale.md) funkcji.

A *strony kodowej* mapowania kodów pojedynczych znaków jednobajtowych lub znaków dwubajtowych. Różne strony kodowe obejmują różne znaki specjalne, zwykle dostosowane do języka lub grupy z języków. Aby uzyskać więcej informacji dotyczących stron kodowych, zobacz [stron kodowych](../c-runtime-library/code-pages.md).

Wewnętrzne funkcje CRT są specyficzne dla implementacji i może ulec zmianie z każdej wersji. Nie zalecamy ich użycie w kodzie.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`___lc_codepage_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Zobacz też

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)