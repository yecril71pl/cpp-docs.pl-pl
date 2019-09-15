---
title: _pclose
ms.date: 11/04/2016
api_name:
- _pclose
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _pclose
- pclose
helpviewer_keywords:
- _pclose function
- pclose function
- pipes, closing
ms.assetid: e2e31a9e-ba3a-4124-bcbb-c4040110b3d3
ms.openlocfilehash: 383dd96553463a2619537cf06fc6534770ed88d5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951086"
---
# <a name="_pclose"></a>_pclose

Czeka na nowy procesor poleceń i zamyka strumień na skojarzonym potoku.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _pclose(
FILE *stream
);
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Zwraca wartość z poprzedniego wywołania do **_popen**.

## <a name="return-value"></a>Wartość zwracana

Zwraca stan zakończenia procesora poleceń kończących lub-1, jeśli wystąpi błąd. Format wartości zwracanej jest taki sam jak dla **_cwait**, z wyjątkiem bajtów o niskiej kolejności i dużej kolejności. Jeśli strumień ma **wartość null**, **_pclose** ustawia **errno** na **EINVAL** i zwraca wartość-1.

Aby uzyskać informacje o tych i innych kodach błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_pclose** wyszukuje identyfikator procesu procesora poleceń (cmd. exe) uruchamiany przez skojarzone wywołanie **_popen** , wykonuje wywołanie [_cwait](cwait.md) na nowym procesorze poleceń i zamyka strumień na skojarzonym potoku.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_pclose**|\<stdio.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_pipe](pipe.md)<br/>
[_popen, _wpopen](popen-wpopen.md)<br/>
