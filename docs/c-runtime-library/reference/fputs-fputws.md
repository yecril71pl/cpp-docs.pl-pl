---
title: fputs, fputws
ms.date: 4/2/2020
api_name:
- fputs
- fputws
- _o_fputs
- _o_fputws
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
- fputs
- fputws
- _fputts
helpviewer_keywords:
- streams, writing strings to
- fputws function
- _fputts function
- fputs function
- fputts function
ms.assetid: d48c82b8-aa17-4830-8c7d-30442ddbb326
ms.openlocfilehash: 0a6ac7770e88975a60e1e4aef522dddf901206fb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346219"
---
# <a name="fputs-fputws"></a>fputs, fputws

Zapisuje ciąg do strumienia.

## <a name="syntax"></a>Składnia

```C
int fputs(
   const char *str,
   FILE *stream
);
int fputws(
   const wchar_t *str,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Ciąg wyjściowy.

*Strumienia*<br/>
Wskaźnik do struktury **PLIK.**

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wartość nieujemną, jeśli zakończy się pomyślnie. W sprawie błędu **fputs** i **fputws** zwracają **EOF**. Jeśli *str* lub *strumień* jest wskaźnikiem null, te funkcje wywołać nieprawidłowy program obsługi parametrów, zgodnie z opisem w sprawdzanie [poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, te funkcje **ustawiają errno** na **EINVAL,** a następnie **fputs** zwraca **EOF**, a **fputws** zwraca **WEOF**.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr aby](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) uzyskać więcej informacji na temat tych i innych kodów błędów.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji kopiuje *str* do *strumienia* wyjściowego w bieżącej pozycji. **fputws** kopiuje argument *szerokoznakowy str* do *strumienia* jako ciąg wieloznakowy lub ciąg znaków szerokoznakowych zgodnie z tym, czy *strumień* jest otwierany odpowiednio w trybie tekstowym, czy binarnym. Żadna z tych funkcji nie kopiuje kończącego się znaku null.

Te dwie funkcje zachowują się identycznie, jeśli strumień jest otwarty w trybie ANSI. **fputs** obecnie nie obsługuje danych wyjściowych do strumienia UNICODE.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fputts**|**fputs ( fputs )**|**fputs ( fputs )**|**fputws ( fputws )**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fputs ( fputs )**|\<stdio.h>|
|**fputws ( fputws )**|\<stdio.h> lub \<wchar.h>|

Konsola nie jest obsługiwana w aplikacjach platformy uniwersalnej systemu Windows (UWP). Standardowe uchwyty strumienia, które są skojarzone z konsolą—**stdin,** **stdout**i **stderr**— muszą zostać przekierowane, zanim funkcje c w czasie wykonywania będą mogły z nich korzystać w aplikacjach platformy uniwersalnej systemu Windows. Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_fputs.c
// This program uses fputs to write
// a single line to the stdout stream.

#include <stdio.h>

int main( void )
{
   fputs( "Hello world from fputs.\n", stdout );
}
```

```Output
Hello world from fputs.
```

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fgets, fgetws](fgets-fgetws.md)<br/>
[gets, _getws](../../c-runtime-library/gets-getws.md)<br/>
[puts, _putws](puts-putws.md)<br/>
