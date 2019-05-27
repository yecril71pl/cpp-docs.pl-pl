---
title: _setmaxstdio
ms.date: 05/21/2019
apiname:
- _setmaxstdio
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
- setmaxstdio
- _setmaxstdio
helpviewer_keywords:
- maximum open files
- _setmaxstdio function
- setmaxstdio function
- open files, maximum
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
ms.openlocfilehash: 94b768d920ffd86a5bd762f8994244dda67fb15f
ms.sourcegitcommit: bde3279f70432f819018df74923a8bb895636f81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2019
ms.locfileid: "66174822"
---
# <a name="setmaxstdio"></a>_setmaxstdio

Ustawia poziom maksymalną liczbę plików jednocześnie otwarty na we/wy strumienia.

## <a name="syntax"></a>Składnia

```C
int _setmaxstdio(
   int new_max
);
```

### <a name="parameters"></a>Parametry

*new_max*<br/>
Nowe maksymalna liczba równocześnie Otwórz pliki na poziomie operacji We/Wy strumienia.

## <a name="return-value"></a>Wartość zwracana

Zwraca *new_max* w przypadku powodzenia; w przeciwnym razie -1.

Jeśli *new_max* jest mniejsza niż **_IOB_ENTRIES**, lub większa niż maksymalna liczba obsługuje dostępne w systemie operacyjnym, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [ Walidacja parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja zwraca wartość -1 i ustawia **errno** do **EINVAL**.

Aby uzyskać informacje na temat tych i innych kodów błędu, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Setmaxstdio —** funkcji zmienia wartość maksymalną liczbę plików, które mogą być otwarte jednocześnie w strumieniu poziom operacji We/Wy.

C czasu wykonywania operacji We/Wy teraz obsługuje maksymalnie 8192 pliki otwarte jednocześnie na [niski poziom operacji We/Wy](../../c-runtime-library/low-level-i-o.md). Ten poziom obejmuje pliki otwarte i uzyskiwać dostęp za pomocą **_otwórz**, **_przeczytaj**, i **_write** rodziny funkcji we/wy. Domyślnie, maksymalnie 512 plików może być otwarty jednocześnie na [strumienia we/wy poziom](../../c-runtime-library/stream-i-o.md). Ten poziom obejmuje pliki otwarte i uzyskiwać dostęp za pomocą **fopen —**, **fgetc —**, i **fputc** rodziny funkcji. Można zwiększyć limit równy 512 otwarte pliki na poziomie we/wy strumienia do maksymalnie 8192 przy użyciu **_setmaxstdio —** funkcji.

Ponieważ strumienia I/O-level funkcje, takie jak **fopen —**, są tworzone na podstawie funkcji I/O — poziom niski maksymalnie 8192 jest sztywnego, górnego limitu liczby jednocześnie otwartych plików, dostępne za pośrednictwem biblioteki wykonawczej C.

> [!NOTE]
> Ta górny limit może być poza co jest obsługiwane w określonej platformy Win32 i o określonej konfiguracji.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_setmaxstdio**|\<stdio.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz [_getmaxstdio —](getmaxstdio.md) na przykład za pomocą **_setmaxstdio —**.

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
