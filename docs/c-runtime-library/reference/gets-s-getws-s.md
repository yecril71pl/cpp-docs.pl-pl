---
title: gets_s, _getws_s
ms.date: 11/04/2016
apiname:
- _getws_s
- gets_s
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
- _getws_s
- gets_s
helpviewer_keywords:
- getws_s function
- _getws_s function
- lines, getting
- streams, getting lines
- buffers, avoiding overruns
- buffer overruns
- buffers, buffer overruns
- gets_s function
- standard input, reading from
ms.assetid: 5880c36f-122c-4061-a1a5-aeeced6fe58c
ms.openlocfilehash: f71fafceaf1974bc5ff736ff175a67cf6c924ee6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482904"
---
# <a name="getss-getwss"></a>gets_s, _getws_s

Pobiera wiersz ze **stdin** strumienia. Te wersje [pobiera _getws —](../../c-runtime-library/gets-getws.md) mają wzmocnienia zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
char *gets_s(
   char *buffer,
   size_t sizeInCharacters
);
wchar_t *_getws_s(
   wchar_t *buffer,
   size_t sizeInCharacters
);
```

```cpp
template <size_t size>
char *gets_s( char (&buffer)[size] ); // C++ only

template <size_t size>
wchar_t *_getws_s( wchar_t (&buffer)[size] ); // C++ only
```

### <a name="parameters"></a>Parametry

*buffer*<br/>
Lokalizacja magazynowa ciągu wejściowego.

*sizeInCharacters*<br/>
Rozmiar buforu.

## <a name="return-value"></a>Wartość zwracana

Zwraca *buforu* w przypadku powodzenia. A **NULL** wskaźnik wskazuje warunek błędu lub końca pliku. Użyj [ferror](ferror.md) lub [feof](feof.md) do określenia, które z nich ma wystąpić.

## <a name="remarks"></a>Uwagi

**Gets_s —** funkcja odczytuje wiersz ze standardowego strumienia wejściowego **stdin** i zapisuje go w *buforu*. Linia składa się z wszystkich znaków, w tym pierwszego znaku nowego wiersza (\n). **gets_s —** następnie zastępuje znak nowego wiersza znakiem null (\0) przed zwróceniem linii. Z kolei **fgets_s** funkcji zachowuje znak nowego wiersza.

Jeśli pierwszym znakiem odczytu jest znak końca pliku, znak null znajduje się na początku *buforu* i **NULL** jest zwracana.

**_getws_s —** to wersja znaku dwubajtowego **gets_s —**; jej argument i wartość zwracana to ciągi znaków dwubajtowych.

Jeśli *buforu* jest **NULL** lub *sizeInCharacters* jest mniejsza niż zero, lub jeśli bufor jest za mały, aby zawierać wiersz danych wejściowych i terminator o wartości null, funkcje te wywołują Nieprawidłowy parametr uchwytu, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **NULL** i ustawiają mechanizm errno jako **ERANGE**.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążania szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu (eliminując potrzebę określenia argumentu rozmiaru) oraz ich mogą automatycznie zastąpić starsze, niezabezpieczone funkcje ich nowsze, bezpieczne odpowiedniki. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_getts_s**|**gets_s**|**gets_s**|**_getws_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**gets_s**|\<stdio.h>|
|**_getws_s**|\<stdio.h > lub \<wchar.h >|

Konsola nie jest obsługiwana w aplikacjach platformy uniwersalnej Windows (UWP). Standardowe uchwyty strumienia, które są powiązane z konsolą, **stdin**, **stdout**, i **stderr**, muszą zostać przekierowane zanim funkcje środowiska wykonawczego języka C można ich używać w aplikacjach platformy UWP . Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_gets_s.c
// This program retrieves a string from the stdin and
// prints the same string to the console.

#include <stdio.h>

int main( void )
{
   char line[21]; // room for 20 chars + '\0'
   gets_s( line, 20 );
   printf( "The line entered was: %s\n", line );
}
```

```Input
Hello there!
```

```Output
The line entered was: Hello there!
```

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[gets, _getws](../../c-runtime-library/gets-getws.md)<br/>
[fgets, fgetws](fgets-fgetws.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[puts, _putws](puts-putws.md)<br/>
