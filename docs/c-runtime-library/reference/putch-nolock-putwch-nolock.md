---
title: _putch_nolock —, _putwch_nolock — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _putwch_nolock
- _putch_nolock
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
- _putch_nolock
- _puttch_nolock
- putch_nolock
- putwch_nolock
- _putwch_nolock
dev_langs:
- C++
helpviewer_keywords:
- putwch_nolock function
- puttch_nolock function
- characters, writing
- putch_nolock function
- _putch_nolock function
- _puttch_nolock function
- console, writing characters to
- _putwch_nolock function
ms.assetid: edbc811d-bac6-47fa-a872-fe4f3a1590b0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e380f59e2f8015efdb6d3af07bfe509337da38a6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403335"
---
# <a name="putchnolock-putwchnolock"></a>_putch_nolock, _putwch_nolock

Zapisuje znak do konsoli bez blokowania wątku.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _putch_nolock(
int c
);
wint_t _putwch_nolock(
wchar_t c
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak jako dane wyjściowe.

## <a name="return-value"></a>Wartość zwracana

Zwraca *c* w przypadku powodzenia. Jeśli **_putch_nolock —** nie powiedzie się, zwraca **EOF**; Jeśli **_putwch_nolock —** nie powiedzie się, zwraca **weof —**.

## <a name="remarks"></a>Uwagi

**_putch_nolock —** i **_putwch_nolock —** są takie same jak **_putch —** i **_putwch —** odpowiednio z tą różnicą, że nie są chronione przed zakłóceniami przez inne wątki. Może być szybsze, ponieważ nie wiążą się z obciążenie zablokowania inne wątki. Ich używać tylko w kontekstach wątkowo, np. aplikacje jednowątkowe lub gdzie wywoływania zakres już obsługuje izolacji wątku.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_puttch_nolock**|**_putch_nolock**|**_putch_nolock**|**_putwch_nolock**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_putch_nolock**|\<conio.h>|
|**_putwch_nolock**|\<conio.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[We/Wy konsoli i portu](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
