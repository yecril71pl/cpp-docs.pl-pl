---
title: ferror
ms.date: 11/04/2016
apiname:
- ferror
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
- ferror
helpviewer_keywords:
- ferror function
- streams, testing for errors
- errors [C++], testing for stream
ms.assetid: 528a34bc-f2aa-4c3f-b89a-5b148e6864f7
ms.openlocfilehash: 2be90ffe8a135b4108abd9504099bd2f6c28f249
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587892"
---
# <a name="ferror"></a>ferror

Testuje pod kątem wystąpienia błędu w strumieniu.

## <a name="syntax"></a>Składnia

```C
int ferror(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

Jeśli żaden błąd nie wystąpił na *strumienia*, **ferror** zwraca wartość 0. W przeciwnym razie zwraca wartość różną od zera. Jeśli wartość strumienia wynosi **NULL**, **ferror** wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ta ustawia **errno** do **EINVAL** i zwraca wartość 0.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych i innych kodów błędu,.

## <a name="remarks"></a>Uwagi

**Ferror** procedura (implementowana jako funkcja i jak makra) testy na potrzeby odczytywania lub zapisywania błąd w pliku skojarzone z *strumienia*. Jeśli wystąpi błąd, pozostaje Ustaw wskaźnik błędu dla strumienia, dopóki strumień zostanie zamknięty lub przewinięta lub do momentu **clearerr —** nazywa się przed nim.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**ferror**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [feof](feof.md).

## <a name="see-also"></a>Zobacz także

[Obsługa błędów](../../c-runtime-library/error-handling-crt.md)<br/>
[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
