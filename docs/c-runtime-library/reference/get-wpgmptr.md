---
title: _get_wpgmptr — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _wpgmptr global variable
- get_wpgmptr function
- wpgmptr global variable
- _get_wpgmptr function
ms.assetid: a77cdd13-2303-4b7c-9a60-8debdbef2011
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9393351174477a4da43d0b3bd49e107430e68ece
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398773"
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
Wskaźnik do ciągu należy podać bieżącą wartość **_wpgmptr —** zmiennej.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero w przypadku powodzenia; błąd o kodzie błędu. Jeśli *pValue* jest **NULL**, zgodnie z opisem w wywołaniu program obsługi nieprawidłowych parametrów [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, ta funkcja ustawia **errno** do **einval —** i zwraca **einval —**.

## <a name="remarks"></a>Uwagi

Wywoływać tylko **_get_wpgmptr —** program ma punktu wejścia szerokości, takich jak **wmain()** lub **wWinMain()**. **_Wpgmptr —** — zmienna globalna zawiera pełną ścieżkę do pliku wykonywalnego skojarzonych z procesem jako ciąg znaków dwubajtowych. Aby uzyskać więcej informacji, zobacz [_pgmptr —, _wpgmptr —](../../c-runtime-library/pgmptr-wpgmptr.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_wpgmptr**|\<stdlib.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[_get_pgmptr](get-pgmptr.md)<br/>
