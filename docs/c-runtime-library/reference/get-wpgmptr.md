---
title: _get_wpgmptr
ms.date: 11/04/2016
api_name:
- _get_wpgmptr
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_wpgmptr
- _get_wpgmptr
helpviewer_keywords:
- _wpgmptr global variable
- get_wpgmptr function
- wpgmptr global variable
- _get_wpgmptr function
ms.assetid: a77cdd13-2303-4b7c-9a60-8debdbef2011
ms.openlocfilehash: 0cd2dc9c2f82d3dc49a17dc438157233c50b3261
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955568"
---
# <a name="_get_wpgmptr"></a>_get_wpgmptr

Pobiera bieżącą wartość zmiennej globalnej **_wpgmptr** .

## <a name="syntax"></a>Składnia

```C
errno_t _get_wpgmptr(
   wchar_t **pValue
);
```

### <a name="parameters"></a>Parametry

*pValue*<br/>
Wskaźnik do ciągu, który ma zostać wypełniony bieżącą wartością zmiennej **_wpgmptr** .

## <a name="return-value"></a>Wartość zwracana

Zwraca zero, jeśli pomyślne; kod błędu w przypadku niepowodzenia. Jeśli *pValue* ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja ustawia **errno** na **EINVAL** i zwraca **EINVAL**.

## <a name="remarks"></a>Uwagi

Wywołaj **_get_wpgmptr** tylko wtedy, gdy program ma szeroki punkt wejścia, taki jak **wmain ()** lub **wWinMain ()** . Zmienna globalna **_wpgmptr** zawiera pełną ścieżkę do pliku wykonywalnego skojarzonego z procesem jako ciąg znaków dwubajtowych. Aby uzyskać więcej informacji, zobacz [_pgmptr, _wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_wpgmptr**|\<stdlib.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[_get_pgmptr](get-pgmptr.md)<br/>
