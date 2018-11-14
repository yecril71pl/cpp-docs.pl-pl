---
title: _get_fmode
ms.date: 11/04/2016
apiname:
- _get_fmode
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
- get_fmode
- _get_fmode
helpviewer_keywords:
- _get_fmode function
- file translation [C++], default mode
- get_fmode function
ms.assetid: 22ea70e2-b9b5-422d-b514-64f4beaea45c
ms.openlocfilehash: dc4740b20ab7283dd8b9f73f458eaba34e582832
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328048"
---
# <a name="getfmode"></a>_get_fmode

Pobiera domyślny tryb translacji plików dla operacji We/Wy na plikach.

## <a name="syntax"></a>Składnia

```C
errno_t _get_fmode(
   int * pmode
);
```

### <a name="parameters"></a>Parametry

*pmode*<br/>
Wskaźnik do liczby całkowitej trzeba napełniać bieżący tryb domyślny: **_O_TEXT** lub **_O_BINARY**.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero, jeśli to się powiedzie; Kod błędu. Jeśli *pmode* jest **NULL**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** a funkcja zwraca **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja pobiera wartość [_fmode](../../c-runtime-library/fmode.md) zmiennej globalnej. Ta zmienna Określa domyślny tryb translacji plików dla obu niskiego poziomu i przesyłanie strumieniowe operacji We/Wy pliku, taką jak **_otwórz**, **_pipe —**, **fopen —**, i [ freopen —](freopen-wfreopen.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_get_fmode**|\<stdlib.h>|\<fcntl.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład w [_set_fmode —](set-fmode.md).

## <a name="see-also"></a>Zobacz także

[_fmode](../../c-runtime-library/fmode.md)<br/>
[_set_fmode](set-fmode.md)<br/>
[_setmode](setmode.md)<br/>
[We/Wy pliku w trybie binarnym i tekstowym](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
