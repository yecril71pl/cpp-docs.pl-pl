---
title: _get_pgmptr
ms.date: 11/04/2016
apiname:
- _get_pgmptr
apilocation:
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
apitype: DLLExport
f1_keywords:
- get_pgmptr
- _get_pgmptr
helpviewer_keywords:
- get_pgmptr function
- _get_pgmptr function
- pgmptr global variable
- _pgmptr global variable
ms.assetid: 29f16a9f-a685-4721-add3-7fad4f67eece
ms.openlocfilehash: 2d3959a69d85fca38e4d099d3365553f88fd015f
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51332091"
---
# <a name="getpgmptr"></a>_get_pgmptr

Pobiera bieżącą wartość **_pgmptr —** zmiennej globalnej.

## <a name="syntax"></a>Składnia

```C
errno_t _get_pgmptr(
   char **pValue
);
```

### <a name="parameters"></a>Parametry

*pValue*<br/>
Wskaźnik do ciągu ma zostać wypełniony przy użyciu bieżącej wartości **_pgmptr —** zmiennej.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero, jeśli to się powiedzie; Kod błędu. Jeśli *pValue* jest **NULL**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ta ustawia **errno** do **EINVAL** i zwraca **EINVAL**.

## <a name="remarks"></a>Uwagi

Wywoływać tylko **_get_pgmptr —** program nie ma punktu wejścia wąskie, takich jak **main()** lub **WinMain()**. **_Pgmptr —** zmienna globalna zawiera pełną ścieżkę do pliku wykonywalnego skojarzonego z procesem. Aby uzyskać więcej informacji, zobacz [_pgmptr —, _wpgmptr —](../../c-runtime-library/pgmptr-wpgmptr.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_pgmptr**|\<stdlib.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[_get_wpgmptr](get-wpgmptr.md)<br/>
