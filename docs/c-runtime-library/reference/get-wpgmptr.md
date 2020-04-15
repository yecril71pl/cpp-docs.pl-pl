---
title: _get_wpgmptr
ms.date: 4/2/2020
api_name:
- _get_wpgmptr
- _o__get_wpgmptr
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 1e54d3dbdc837c491f5b39d33a9b8197094ac60b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344864"
---
# <a name="_get_wpgmptr"></a>_get_wpgmptr

Pobiera bieżącą wartość **zmiennej globalnej _wpgmptr.**

## <a name="syntax"></a>Składnia

```C
errno_t _get_wpgmptr(
   wchar_t **pValue
);
```

### <a name="parameters"></a>Parametry

*wartość pValue*<br/>
Wskaźnik do ciągu, który ma być wypełniony bieżącą wartością **zmiennej _wpgmptr.**

## <a name="return-value"></a>Wartość zwracana

Zwraca zero, jeśli zakończy się pomyślnie; kod błędu w przypadku awarii. Jeśli *wartość pValue* ma **wartość NULL,** nieprawidłowy program obsługi parametrów jest wywoływany zgodnie z opisem w [yd.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, ta funkcja ustawia **errno** na **EINVAL** i zwraca **wartość EINVAL**.

## <a name="remarks"></a>Uwagi

Wywołaj **_get_wpgmptr** tylko wtedy, gdy program ma szeroki punkt wejścia, taki jak **wmain()** lub **wWinMain()**. **_wpgmptr** zmienna globalna zawiera pełną ścieżkę do pliku wykonywalnego skojarzonego z procesem jako ciąg znaków szerokich. Aby uzyskać więcej informacji, zobacz [_pgmptr, _wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_wpgmptr**|\<>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[_get_pgmptr](get-pgmptr.md)<br/>
