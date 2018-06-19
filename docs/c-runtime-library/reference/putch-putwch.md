---
title: _putch —, _putwch — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _putwch
- _putch
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
- api-ms-win-crt-conio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _putch
- putwch
- _putwch
dev_langs:
- C++
helpviewer_keywords:
- _putch function
- characters, writing
- putwch function
- _putwch function
- putch function
- console, writing characters to
ms.assetid: 3babc7cf-e333-405d-8449-c788d61d51aa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a0a6e50a4cd6794e28cc59bb2b080c57c0993986
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401808"
---
# <a name="putch-putwch"></a>_putch, _putwch

Zapisuje znak do konsoli.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Znak jako dane wyjściowe.

## <a name="return-value"></a>Wartość zwracana

Zwraca *c* w przypadku powodzenia. Jeśli **_putch —** nie powiedzie się, zwraca **EOF**; Jeśli **_putwch —** nie powiedzie się, zwraca **weof —**.

## <a name="remarks"></a>Uwagi

Te funkcje wpisz znak *c* bezpośrednio, bez buforowania do konsoli. W systemie Windows NT **_putwch —** zapisuje znaków Unicode przy użyciu bieżących ustawień regionalnych konsoli.

Wersje z **_nolock —** sufiks są identyczne z tą różnicą, że nie są chronione przez inne wątki od zakłóceń. Aby uzyskać więcej informacji, zobacz **_putch_nolock —**, **_putwch_nolock —**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_puttch**|**_putch**|**_putch**|**_putwch**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_putch**|\<conio.h>|
|**_putwch**|\<conio.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

Zobacz przykład [_getch —](getch-getwch.md).

## <a name="see-also"></a>Zobacz także

[We/Wy konsoli i portu](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
