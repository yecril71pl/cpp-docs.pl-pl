---
title: _putch, _putwch
ms.date: 4/2/2020
api_name:
- _putwch
- _putch
- _o__putch
- _o__putwch
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 123d4a9b1ee5024ed85b7034462b469740012b85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338419"
---
# <a name="_putch-_putwch"></a>_putch, _putwch

Zapisuje znak do konsoli.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*C*<br/>
Znak ma być dane wyjściowe.

## <a name="return-value"></a>Wartość zwracana

Zwraca *c,* jeśli zakończy się pomyślnie. Jeśli **_putch** nie powiedzie się, zwraca **EOF**; jeśli **_putwch** nie powiedzie się, zwraca **WEOF**.

## <a name="remarks"></a>Uwagi

Te funkcje zapisują znak *c* bezpośrednio, bez buforowania, do konsoli. W systemie Windows NT **_putwch** zapisuje znaki Unicode przy użyciu bieżącego ustawienia ustawień regionalnych konsoli.

Wersje z sufiksem **_nolock** są identyczne, z tą różnicą, że nie są chronione przed zakłóceniami przez inne wątki. Aby uzyskać więcej informacji, zobacz **_putch_nolock** **, _putwch_nolock**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_puttch**|**_putch**|**_putch**|**_putwch**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_putch**|\<> conio.h|
|**_putwch**|\<> conio.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

Zobacz przykład [_getch](getch-getwch.md).

## <a name="see-also"></a>Zobacz też

[Operacje We/Wy konsoli i portu](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
