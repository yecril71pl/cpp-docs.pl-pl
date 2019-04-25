---
title: _get_wpgmptr
ms.date: 11/04/2016
apiname:
- _get_wpgmptr
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
- get_wpgmptr
- _get_wpgmptr
helpviewer_keywords:
- _wpgmptr global variable
- get_wpgmptr function
- wpgmptr global variable
- _get_wpgmptr function
ms.assetid: a77cdd13-2303-4b7c-9a60-8debdbef2011
ms.openlocfilehash: 87738c8564b70df37a9f2fbdcc5e5ab80165af32
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331886"
---
# <a name="getwpgmptr"></a>_get_wpgmptr

Pobiera bieżącą wartość **_wpgmptr —** zmiennej globalnej.

## <a name="syntax"></a>Składnia

```C
errno_t _get_wpgmptr(
   wchar_t **pValue
);
```

### <a name="parameters"></a>Parametry

*pValue*<br/>
Wskaźnik do ciągu ma zostać wypełniony przy użyciu bieżącej wartości **_wpgmptr —** zmiennej.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero, jeśli to się powiedzie; Kod błędu. Jeśli *pValue* jest **NULL**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ta ustawia **errno** do **EINVAL** i zwraca **EINVAL**.

## <a name="remarks"></a>Uwagi

Wywoływać tylko **_get_wpgmptr —** program nie ma punktu wejścia szeroką, takich jak **wmain()** lub **wWinMain()**. **_Wpgmptr —** zmienna globalna zawiera pełną ścieżkę do pliku wykonywalnego skojarzonego z procesem jako ciąg znaków dwubajtowych. Aby uzyskać więcej informacji, zobacz [_pgmptr —, _wpgmptr —](../../c-runtime-library/pgmptr-wpgmptr.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_wpgmptr**|\<stdlib.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[_get_pgmptr](get-pgmptr.md)<br/>
