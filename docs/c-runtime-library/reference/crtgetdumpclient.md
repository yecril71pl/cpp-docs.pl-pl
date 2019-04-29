---
title: _CrtGetDumpClient
ms.date: 11/04/2016
apiname:
- _CrtGetDumpClient
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
apitype: DLLExport
f1_keywords:
- CrtGetDumpClient
- _CrtGetDumpClient
helpviewer_keywords:
- _CrtGetDumpClient function
- CrtGetDumpClient function
ms.assetid: 9051867f-341b-493b-b53d-45d2b454a3ad
ms.openlocfilehash: e4700bd936bec97014508c4a971f6e6c278c6a11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339926"
---
# <a name="crtgetdumpclient"></a>_CrtGetDumpClient

Pobiera bieżącą funkcję zdefiniowanych przez aplikację do zrzucania **_CLIENT_BLOCK** wpisz bloki pamięci (tylko wersja debugowania).

## <a name="syntax"></a>Składnia

```C
_CRT_DUMP_CLIENT _CrtGetDumpClient( void );
```

## <a name="return-value"></a>Wartość zwracana

Zwraca bieżący procedury zrzutu.

## <a name="remarks"></a>Uwagi

**_Crtgetdumpclient —** funkcja pobiera bieżącą funkcję hak służąca do zrzucania obiektów przechowywanych w **_CLIENT_BLOCK** bloki pamięci dla środowiska wykonawczego języka C debugować proces zrzutu pamięci.

Aby uzyskać więcej informacji na temat korzystania innych funkcją podłączania funkcji wykonawczej i pisanie własnych zdefiniowaną przez klienta funkcje punktów zaczepienia, zobacz [debugowania pisania funkcji punktów zaczepienia](/visualstudio/debugger/debug-hook-function-writing).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtGetDumpClient**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
[_CrtSetDumpClient](crtsetdumpclient.md)<br/>
