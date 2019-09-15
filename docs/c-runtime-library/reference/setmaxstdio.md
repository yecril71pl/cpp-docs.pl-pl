---
title: _setmaxstdio
ms.date: 05/21/2019
api_name:
- _setmaxstdio
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
- setmaxstdio
- _setmaxstdio
helpviewer_keywords:
- maximum open files
- _setmaxstdio function
- setmaxstdio function
- open files, maximum
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
ms.openlocfilehash: 620213b4df9ea555189a1403b3c9e83b55cad6c6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948220"
---
# <a name="_setmaxstdio"></a>_setmaxstdio

Ustawia maksymalną liczbę jednocześnie otwartych plików na poziomie strumienia we/wy.

## <a name="syntax"></a>Składnia

```C
int _setmaxstdio(
   int new_max
);
```

### <a name="parameters"></a>Parametry

*new_max*<br/>
Nowa Maksymalna liczba otwartych plików jednocześnie na poziomie strumienia we/wy.

## <a name="return-value"></a>Wartość zwracana

Zwraca *new_max* , jeśli pomyślne; -1 w przeciwnym razie.

Jeśli wartość *new_max* jest mniejsza niż **_IOB_ENTRIES**lub większa niż maksymalna liczba dojść dostępnych w systemie operacyjnym, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca wartość-1 i ustawia **errno** na **EINVAL**.

Aby uzyskać informacje o tych i innych kodach błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_setmaxstdio** zmienia maksymalną wartość liczby plików, które mogą być otwarte jednocześnie na poziomie strumienia we/wy.

We/wy w czasie wykonywania C/O jest teraz obsługiwane nawet do 8 192 plików jednocześnie na [niskim poziomie we/wy](../../c-runtime-library/low-level-i-o.md). Ten poziom obejmuje pliki otwarte i dostępne przy użyciu rodziny **_open**, **_read**i **_write** funkcji we/wy. Domyślnie do 512 plików można otwierać jednocześnie na [poziomie strumienia we/wy](../../c-runtime-library/stream-i-o.md). Ten poziom obejmuje pliki otwarte i dostępne przy użyciu rodziny **fopen**, **fgetc**i **fputc** funkcji. Limit 512 otwartych plików na poziomie strumienia we/wy można zwiększyć do maksymalnie 8 192 przy użyciu funkcji **_setmaxstdio** .

Ponieważ funkcje na poziomie strumienia operacji we/wy, takie jak **fopen**, są tworzone na podstawie niskich funkcji we/wy, wartość maksymalna 8 192 to stały górny limit liczby jednocześnie otwartych plików, do których dostęp odbywa się za pomocą biblioteki wykonawczej C.

> [!NOTE]
> Ten górny limit może być poza zakresem obsługiwanym przez określoną platformę i konfigurację Win32.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_setmaxstdio**|\<stdio.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz [_getmaxstdio](getmaxstdio.md) , aby zapoznać się z przykładem korzystania z **_setmaxstdio**.

## <a name="see-also"></a>Zobacz także

[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
