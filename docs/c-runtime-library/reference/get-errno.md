---
title: _get_errno
ms.date: 11/04/2016
apiname:
- _get_errno
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
- _get_errno
helpviewer_keywords:
- get_errno function
- errno global variable
- _get_errno function
ms.assetid: b3fd5ebc-f41b-4314-a2f4-2f2d79d6e740
ms.openlocfilehash: fb0897451c72020cd72a821ec9928ed655d84b7e
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51331818"
---
# <a name="geterrno"></a>_get_errno

Pobiera bieżącą wartość errno — zmienna globalna.

## <a name="syntax"></a>Składnia

```C
errno_t _get_errno(
   int * pValue
);
```

### <a name="parameters"></a>Parametry

*pValue*<br/>
Wskaźnik do liczby całkowitej trzeba napełniać bieżącą wartość **errno** zmiennej.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero, jeśli to się powiedzie; Kod błędu. Jeśli *pValue* jest **NULL**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ta ustawia **errno** do **EINVAL** i zwraca **EINVAL**.

## <a name="remarks"></a>Uwagi

Możliwe wartości **errno** są zdefiniowane w Errno.h. Zobacz też [errno — stałe](../../c-runtime-library/errno-constants.md).

## <a name="example"></a>Przykład

```C
// crt_get_errno.c
#include <stdio.h>
#include <fcntl.h>
#include <sys/stat.h>
#include <share.h>
#include <errno.h>

int main()
{
   errno_t err;
   int pfh;
   _sopen_s( &pfh, "nonexistent.file", _O_WRONLY, _SH_DENYNO, _S_IWRITE );
   _get_errno( &err );
   printf( "errno = %d\n", err );
   printf( "fyi, ENOENT = %d\n", ENOENT );
}
```

```Output
errno = 2
fyi, ENOENT = 2
```

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_get_errno**|\<stdlib.h>|\<errno.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[_set_errno](set-errno.md)<br/>
[errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
