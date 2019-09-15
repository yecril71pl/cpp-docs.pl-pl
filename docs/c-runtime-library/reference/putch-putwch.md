---
title: _putch, _putwch
ms.date: 11/04/2016
api_name:
- _putwch
- _putch
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
- api-ms-win-crt-conio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _putch
- putwch
- _putwch
helpviewer_keywords:
- _putch function
- characters, writing
- putwch function
- _putwch function
- putch function
- console, writing characters to
ms.assetid: 3babc7cf-e333-405d-8449-c788d61d51aa
ms.openlocfilehash: 8e7d7d57f5418e8c15aa02f015d3346298fa0422
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950048"
---
# <a name="_putch-_putwch"></a>_putch, _putwch

Zapisuje znak w konsoli.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _putch(
   int c
);

wint_t _putwch(
   wchar_t c
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak do wyprowadzenia.

## <a name="return-value"></a>Wartość zwracana

Zwraca *c* , jeśli powodzenie. Jeśli **_putch** nie powiedzie się, zwraca **EOF**; Jeśli **_putwch** nie powiedzie się, zwraca **WEOF**.

## <a name="remarks"></a>Uwagi

Te funkcje zapisują znak *c* bezpośrednio, bez buforowania, do konsoli programu. W systemie Windows NT **_putwch** zapisuje znaki Unicode przy użyciu bieżących ustawień regionalnych konsoli.

Wersje z sufiksem **_nolock** są identyczne, z tą różnicą, że nie są chronione przed ingerencją przez inne wątki. Aby uzyskać więcej informacji, zobacz **_putch_nolock**, **_putwch_nolock**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_puttch**|**_putch**|**_putch**|**_putwch**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_putch**|\<conio.h>|
|**_putwch**|\<conio.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

Zobacz przykład dla [_getch](getch-getwch.md).

## <a name="see-also"></a>Zobacz także

[We/wy konsoli i portu](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
