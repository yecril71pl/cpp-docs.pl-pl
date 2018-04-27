---
title: putchar —, putwchar — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- putchar
- putwchar
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
- putchar
- putwchar
- _puttchar
dev_langs:
- C++
helpviewer_keywords:
- putchar function
- _puttchar function
- characters, writing
- standard output, writing to
- putwchar function
ms.assetid: 93657c7f-cca1-4032-8e3a-cd6ab6193748
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 722ef228203afa85728b57549c9eeb69c3745723
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="putchar-putwchar"></a>putchar, putwchar

Zapisuje znaku **stdout**.

## <a name="syntax"></a>Składnia

```C
int putchar(
   int c
);
wint_t putwchar(
   wchar_t c
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak do zapisania.

## <a name="return-value"></a>Wartość zwracana

Zwraca znak zapisywane. Wskazująca błąd lub warunek plik końcowy **putc —** i **putchar —** zwracać ** EOF`; **putwc` i **putwchar —** zwracać **weof —**. Wszystkie cztery procedury, można użyć [ferror —](ferror.md) lub [feof —](feof.md) do sprawdzenia błąd lub koniec pliku. Jeśli przekazany wskaźnika o wartości null *strumienia*, te funkcje wygeneruje wyjątek nieprawidłowy parametr, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, zwracają **EOF** lub **weof —** i ustaw **errno** do **einval —**.

Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych i innych kodów błędów.

## <a name="remarks"></a>Uwagi

**Putc —** procedury zapisuje pojedynczy znak *c* z danymi wyjściowymi *strumienia* w bieżącym położeniu. Dowolna liczba całkowita mogą zostać przekazane do **putc —**, ale są zapisywane tylko pierwszych 8 bitów. **Putchar —** procedura jest identyczna jak **putc — (** * c ***, stdout)**. Dla każdej procedury Jeśli wystąpi błąd, ustaw wskaźnik błędów dla tego strumienia. **putc —** i **putchar —** są podobne do **fputc —** i **_fputchar —**, ale są implementowane zarówno jako funkcje, jak i jako makra (zobacz [ Wybieranie pomiędzy funkcjami i makrami](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)). **putwc —** i **putwchar —** wersji znaków dwubajtowych **putc —** i **putchar —**odpowiednio.

Wersje z **_nolock —** sufiks są identyczne z tą różnicą, że nie są chronione przez inne wątki od zakłóceń. Może być szybsze, ponieważ nie wiążą się z obciążenie zablokowania inne wątki. Ich używać tylko w kontekstach wątkowo, np. aplikacje jednowątkowe lub gdzie wywoływania zakres już obsługuje izolacji wątku.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_puttchar —**|**putchar —**|**putchar —**|**putwchar —**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**putchar —**|\<stdio.h>|
|**putwchar —**|\<stdio.h > lub \<wchar.h >|

Konsoli nie jest obsługiwane w aplikacjach systemu Windows platformy Uniwersalnej. Uchwyty Standardowy strumień, które są skojarzone z konsoli programu **stdin**, **stdout**, i **stderr**, muszą być przekierowywane przed funkcje wykonawcze języka C można używać ich w aplikacji platformy uniwersalnej systemu Windows . Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_putchar.c
/* This program uses putc to write buffer
* to a stream. If an error occurs, the program
* stops before writing the entire buffer.
*/

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char *p, buffer[] = "This is the line of output\n";
   int  ch;

   ch = 0;

   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )
      ch = putchar( *p );
}
```

### <a name="output"></a>Dane wyjściowe

```Output
This is the line of output
```

## <a name="see-also"></a>Zobacz także

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
