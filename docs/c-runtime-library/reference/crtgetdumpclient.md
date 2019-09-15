---
title: _CrtGetDumpClient
ms.date: 11/04/2016
api_name:
- _CrtGetDumpClient
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CrtGetDumpClient
- _CrtGetDumpClient
helpviewer_keywords:
- _CrtGetDumpClient function
- CrtGetDumpClient function
ms.assetid: 9051867f-341b-493b-b53d-45d2b454a3ad
ms.openlocfilehash: 4b5c6c7d4d123d2d419f104ddaabd57c10ad320e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938744"
---
# <a name="_crtgetdumpclient"></a>_CrtGetDumpClient

Pobiera bieżącą funkcję zdefiniowaną przez aplikację w celu zatopienia bloków pamięci typu **_CLIENT_BLOCK** (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
_CRT_DUMP_CLIENT _CrtGetDumpClient( void );
```

## <a name="return-value"></a>Wartość zwracana

Zwraca bieżącą procedurę zrzutu.

## <a name="remarks"></a>Uwagi

Funkcja **_CrtGetDumpClient** pobiera bieżącą funkcję Hook dla obiektów dumpingowych przechowywanych w blokach pamięci **_CLIENT_BLOCK** dla procesu zrzutu pamięci debugowania w czasie wykonywania C.

Aby uzyskać więcej informacji na temat korzystania z innych funkcji w czasie wykonywania z możliwością podłączania i pisania własnych zdefiniowanych przez klienta funkcji Hook, zobacz [Zapisywanie funkcji punktu zaczepienia debugowania](/visualstudio/debugger/debug-hook-function-writing).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtGetDumpClient**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje wyłącznie [bibliotek uruchomieniowych C](../../c-runtime-library/crt-library-features.md) .

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
[_CrtSetDumpClient](crtsetdumpclient.md)<br/>
