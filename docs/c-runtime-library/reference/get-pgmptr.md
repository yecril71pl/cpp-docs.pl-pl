---
title: _get_pgmptr
ms.date: 4/2/2020
api_name:
- _get_pgmptr
- _o__get_pgmptr
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
- get_pgmptr
- _get_pgmptr
helpviewer_keywords:
- get_pgmptr function
- _get_pgmptr function
- pgmptr global variable
- _pgmptr global variable
ms.assetid: 29f16a9f-a685-4721-add3-7fad4f67eece
ms.openlocfilehash: efcac6a64c01bee38a3753bdec378dae625db35e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345022"
---
# <a name="_get_pgmptr"></a>_get_pgmptr

Pobiera bieżącą wartość **zmiennej globalnej _pgmptr.**

## <a name="syntax"></a>Składnia

```C
errno_t _get_pgmptr(
   char **pValue
);
```

### <a name="parameters"></a>Parametry

*wartość pValue*<br/>
Wskaźnik do ciągu, który ma być wypełniony bieżącą wartością **zmiennej _pgmptr.**

## <a name="return-value"></a>Wartość zwracana

Zwraca zero, jeśli zakończy się pomyślnie; kod błędu w przypadku awarii. Jeśli *wartość pValue* ma **wartość NULL,** nieprawidłowy program obsługi parametrów jest wywoływany zgodnie z opisem w [yd.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, ta funkcja ustawia **errno** na **EINVAL** i zwraca **wartość EINVAL**.

## <a name="remarks"></a>Uwagi

Wywołaj **_get_pgmptr** tylko wtedy, gdy program ma wąski punkt wejścia, taki jak **main()** lub **WinMain()**. **_pgmptr** zmienna globalna zawiera pełną ścieżkę do pliku wykonywalnego skojarzonego z procesem. Aby uzyskać więcej informacji, zobacz [_pgmptr, _wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_pgmptr**|\<>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[_get_wpgmptr](get-wpgmptr.md)<br/>
