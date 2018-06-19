---
title: _get_pgmptr — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- get_pgmptr function
- _get_pgmptr function
- pgmptr global variable
- _pgmptr global variable
ms.assetid: 29f16a9f-a685-4721-add3-7fad4f67eece
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0488e2a7b8cd907872e835abb63e62f29f259455
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397782"
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
Wskaźnik do ciągu należy podać bieżącą wartość **_pgmptr —** zmiennej.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero w przypadku powodzenia; błąd o kodzie błędu. Jeśli *pValue* jest **NULL**, zgodnie z opisem w wywołaniu program obsługi nieprawidłowych parametrów [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, ta funkcja ustawia **errno** do **einval —** i zwraca **einval —**.

## <a name="remarks"></a>Uwagi

Wywoływać tylko **_get_pgmptr —** program ma punktu wejścia wąskie, takich jak **main()** lub **WinMain()**. **_Pgmptr —** — zmienna globalna zawiera pełną ścieżkę do pliku wykonywalnego skojarzonych z procesem. Aby uzyskać więcej informacji, zobacz [_pgmptr —, _wpgmptr —](../../c-runtime-library/pgmptr-wpgmptr.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_pgmptr**|\<stdlib.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[_get_wpgmptr](get-wpgmptr.md)<br/>
