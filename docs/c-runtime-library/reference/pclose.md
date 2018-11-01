---
title: _pclose
ms.date: 11/04/2016
apiname:
- _pclose
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _pclose
- pclose
helpviewer_keywords:
- _pclose function
- pclose function
- pipes, closing
ms.assetid: e2e31a9e-ba3a-4124-bcbb-c4040110b3d3
ms.openlocfilehash: eb0f54ec27992cd0e62b11d8fec5bd54c3daea4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507721"
---
# <a name="pclose"></a>_pclose

Czeka na nowy procesor polecenia i zamyka strumienia na rurze skojarzonej.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _pclose(
FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Zwróć wartość z poprzedniego wywołania **_popen —**.

## <a name="return-value"></a>Wartość zwracana

Zwraca stan wyjścia kończącego procesora poleceń lub -1, jeśli wystąpi błąd. Format wartości zwracanej jest taki sam jak dla **_cwait**, z wyjątkiem bajty niskiego rzędu i wysokiego rzędu zostały zamienione. Jeśli wartość strumienia wynosi **NULL**, **_pclose —** ustawia **errno** do **EINVAL** i zwraca wartość -1.

Aby uzyskać informacje na temat tych i innych kodów błędu, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Pclose —** funkcja wyszukuje identyfikator procesu procesora poleceń (Cmd.exe), uruchamianego przez powiązane **_popen —** wywołanie, wykonuje [_cwait](cwait.md) wywołać dla nowego polecenia procesor i zamyka strumienia na rurze skojarzonej.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_pclose**|\<stdio.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_pipe](pipe.md)<br/>
[_popen, _wpopen](popen-wpopen.md)<br/>
