---
title: ferror
ms.date: 4/2/2020
api_name:
- ferror
- _o_ferror
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ferror
helpviewer_keywords:
- ferror function
- streams, testing for errors
- errors [C++], testing for stream
ms.assetid: 528a34bc-f2aa-4c3f-b89a-5b148e6864f7
ms.openlocfilehash: e424ffe3f113e50e318d9198bd5f06aaec96852a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347291"
---
# <a name="ferror"></a>ferror

Testy błędu w strumieniu.

## <a name="syntax"></a>Składnia

```C
int ferror(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Strumienia*<br/>
Wskaźnik do struktury **PLIK.**

## <a name="return-value"></a>Wartość zwracana

Jeśli w *strumieniu*nie wystąpił żaden błąd, **ferror** zwraca wartość 0. W przeciwnym razie zwraca wartość niezerową. Jeśli strumień ma **wartość NULL**, **ferror** wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [zatwierdzeniu parametru.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, ta funkcja ustawia **errno** na **EINVAL** i zwraca 0.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr aby](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) uzyskać więcej informacji na temat tych i innych kodów błędów.

## <a name="remarks"></a>Uwagi

**Ferror** rutynowych (realizowane zarówno jako funkcja, jak i jako makro) testy dla odczytu lub zapisu błędu w pliku skojarzonym ze *strumieniem*. Jeśli wystąpił błąd, wskaźnik błędu dla strumienia pozostaje ustawiony, dopóki strumień nie zostanie zamknięty lub przewinie ponownie lub dopóki nie zostanie **wywołany przez jaśniejsze** go.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**ferror**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [feof](feof.md).

## <a name="see-also"></a>Zobacz też

[Obsługa błędów](../../c-runtime-library/error-handling-crt.md)<br/>
[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
