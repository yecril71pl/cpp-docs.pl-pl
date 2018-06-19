---
title: fputc —, fputwc — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- fputc
- fputwc
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
- fputc
- fputwc
- _fputtc
dev_langs:
- C++
helpviewer_keywords:
- streams, writing characters to
- fputtc function
- _fputtc function
- fputwc function
- fputc function
ms.assetid: 5a0a593d-43f4-4fa2-a401-ec4e23de4d2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af93e0c42002dc557f691daadd2fc003dced0247
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401424"
---
# <a name="fputc-fputwc"></a>fputc, fputwc

Zapisuje znak w strumieniu.

## <a name="syntax"></a>Składnia

```C
int fputc(
   int c,
   FILE *stream
);
wint_t fputwc(
   wchar_t c,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak do zapisania.

*Strumień*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca znak zapisywane. Aby uzyskać **fputc —**, zwracana wartość **EOF** wskazuje błąd. Aby uzyskać **fputwc —**, zwracana wartość **weof —** wskazuje błąd. Jeśli *strumienia* jest **NULL**, te funkcje Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, zwracają **EOF** i ustaw **errno** do **einval —**.

Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych i innych kodów błędów.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji zapisuje pojedynczy znak *c* do pliku w pozycji wskazywana przez wskaźnik położenia skojarzony plik (jeśli jest zdefiniowana) i przesuwa wskaźnik zależnie od potrzeb. W przypadku liczby **fputc —** i **fputwc —**, plik jest skojarzony z *strumienia*. Jeśli plik nie może obsłużyć żądań pozycjonowania lub został otwarty w trybie append, znak jest dołączany do końca strumienia.

Dwie funkcje zachowują się tak samo, jakby strumień jest otwarty w trybie ANSI. **fputc —** nie obsługuje obecnie dane wyjściowe do strumienia UNICODE.

Wersje z **_nolock —** sufiks są identyczne z tą różnicą, że nie są chronione przez inne wątki od zakłóceń. Aby uzyskać więcej informacji, zobacz[_fputc_nolock —, _fputwc_nolock —](fputc-nolock-fputwc-nolock.md).

Uwagi dotyczące procedury należy wykonać.

|Procedura|Uwagi|
|-------------|-------------|
|**fputc —**|Odpowiednikiem **putc —**, ale zaimplementowany tylko jako funkcję, a nie jako funkcję i makra.|
|**fputwc —**|Wersja znaków dwubajtowych **fputc —**. Zapisuje *c* jako znaków wielobajtowych lub znaków dwubajtowych zgodnie z czy *strumienia* jest otwarty w trybie tekst lub binarny.|

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fputtc —**|**fputc —**|**fputc —**|**fputwc —**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fputc —**|\<stdio.h>|
|**fputwc —**|\<stdio.h > lub \<wchar.h >|

Konsoli nie jest obsługiwane w aplikacjach systemu Windows platformy Uniwersalnej. Uchwyty Standardowy strumień, które są skojarzone z konsoli programu —**stdin**, **stdout**, i **stderr**— muszą być przekierowywane przed funkcje wykonawcze języka C można używać ich w aplikacji platformy uniwersalnej systemu Windows . Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_fputc.c
// This program uses fputc
// to send a character array to stdout.

#include <stdio.h>

int main( void )
{
   char strptr1[] = "This is a test of fputc!!\n";
   char *p;

   // Print line to stream using fputc.
   p = strptr1;
   while( (*p != '\0') && fputc( *(p++), stdout ) != EOF ) ;

}
```

```Output
This is a test of fputc!!
```

## <a name="see-also"></a>Zobacz także

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
