---
title: _set_errno
ms.date: 11/04/2016
apiname:
- _set_errno
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
- set_errno
- _set_errno
helpviewer_keywords:
- errno global variable
- set_errno function
- _set_errno function
ms.assetid: d338914a-1894-4cf3-ae45-f2c4eb26590b
ms.openlocfilehash: 42a60875d4ab701c05b8bc12f8d4afb77852e3a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452155"
---
# <a name="seterrno"></a>_set_errno

Ustaw wartość **errno** zmiennej globalnej.

## <a name="syntax"></a>Składnia

```C
errno_t _set_errno( int error_value );
```

### <a name="parameters"></a>Parametry

*error_value*<br/>
Nowa wartość **errno**.

## <a name="return-value"></a>Wartość zwracana

Zwraca zero, jeśli to się powiedzie.

## <a name="remarks"></a>Uwagi

Możliwe wartości są definiowane w Errno.h. Zobacz też [errno — stałe](../../c-runtime-library/errno-constants.md).

## <a name="example"></a>Przykład

```C
// crt_set_errno.c
#include <stdio.h>
#include <errno.h>

int main()
{
   _set_errno( EILSEQ );
   perror( "Oops" );
}
```

```Output
Oops: Illegal byte sequence
```

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_set_errno**|\<stdlib.h>|\<errno.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[_get_errno](get-errno.md)<br/>
[errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
